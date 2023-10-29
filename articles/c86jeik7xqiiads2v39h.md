---
title: "Qemuを使用したDockerの高速化"
emoji: ""
type: "25-砂場"
topics: ['25-砂場']
published: False
---

# Qemuを使用したDockerの高速化

Qemuを使用したDockerの高速化

最近、macOS (x86_64) のQemuのHV（Hypervisor Framework）を使用できることを知りました。普段使いにも十分な高速性があり、ホストからゲストへの書き込み速度をDocker Desktopと比較してみました。すると、Qemuの方が2倍ほど高速でした。

まずはデビアンのインストールを行います。

```bash
$ qemu-system-x86_64 --smp 2 -m 2G -accel hvf -cdrom debian-12.1.0-amd64-netinst.iso -hda debian.qcow2
```

次に、Docker Desktop（デビアン）からホストへの書き込み速度を計測しました。

- ランダムデータ書き込み: 7秒
- ゼロデータ書き込み: 4.5秒

```bash
$ docker run --rm -it -v ~/Documents/Docker:/mnt debian
# root@d199a88b8c1e:/mnt# dd if=/dev/urandom of=dat bs=100M count=10 conv=fsync
10+0 records in
10+0 records out
1048576000 bytes (1.0 GB, 1000 MiB) copied, 7.0478 s, 149 MB/s
# root@d199a88b8c1e:/mnt# dd if=/dev/zero of=dat bs=100M count=10 conv=fsync
10+0 records in
10+0 records out
1048576000 bytes (1.0 GB, 1000 MiB) copied, 4.51917 s, 232 MB/s
```

Qemuでも同様の書き込み速度を計測しました。

- ランダムデータ書き込み: 3.9秒
- ゼロデータ書き込み: 1.8秒

```bash
$ qemu-system-x86_64 --smp 2 -m 2G -accel hvf -hda debian.qcow2 -display none -daemonize -nic user,hostfwd=tcp::5000-:22 -virtfs local,path=$HOME/Documents/Qemu,security_model=none,mount_tag=Shared
$ ssh admin@localhost -p5000
$ mount -t 9p -o noatime,trans=virtio,version=9p2000.L Shared /mnt
$ root@localhost:/mnt# dd if=/dev/urandom of=dat bs=100M count=10 conv=fsync
10+0 records in
10+0 records out
1048576000 bytes (1.0 GB, 1000 MiB) copied, 3.96111 s, 265 MB/s
$ root@localhost:/mnt# dd if=/dev/zero of=dat bs=100M count=10 conv=fsync
10+0 records in
10+0 records out
1048576000 bytes (1.0 GB, 1000 MiB) copied, 1.89221 s, 554 MB/s
```

Qemuを使用した場合、書き込み速度が高速であることが確認できました。この結果を受けて、私はDocker Desktopを使わずにQemu上にDockerを立てることを考えています。以前からVirtualbox 7以降でホスト側のネットワーク周りで問題が発生していたため、最近はほとんど使用していませんでした。

もし興味がある方は、ぜひ試してみてください！
