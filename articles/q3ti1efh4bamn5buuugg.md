---
title: "How to Improve Performance with Qemu on macOS"
emoji: ""
type: "25-砂場"
topics: ['25-砂場']
published: False
---

# How to Improve Performance with Qemu on macOS

How to Improve Performance with Qemu on macOS

こんにちは、みなさん！今回は、macOS (x86_64) 上での Qemu の利用についてお話ししたいと思います。実は、HVF (Hypervisor Framework) を使用することで、Qemu でも高速な仮想化が可能なんですよ。

最近、Qemu を使用して Docker Desktop の書き込み速度を比較してみたところ、驚くべき結果が出ました。Qemu は、ホストとゲスト間の書き込み速度が Docker Desktop の約2倍も高速だったんです。

さっそく、Debian をインストールしてみましょう。以下のコマンドを実行します。

```
$ qemu-system-x86_64 --smp 2 -m 2G -accel hvf -cdrom debian-12.1.0-amd64-netinst.*** -hda debian.qcow2
```

次に、Docker Desktop (Debian) からホストへの書き込み速度を測定してみます。`urandom` と `zero` の書き込みをそれぞれ行いました。結果は以下の通りです。

```
$ docker run --rm -it -v ~/Documents/Docker:/mnt debian
# root@d199a88b8c1e:/mnt# dd if=/dev/urandom of=dat bs=100M count=10 conv=fsync
10+0 records in
10+0 records out
*** bytes (1.0 GB, 1000 MiB) copied, 7.0478 s, 149 MB/s
# root@d199a88b8c1e:/mnt# dd if=/dev/zero of=dat bs=100M count=10 conv=fsync
10+0 records in
10+0 records out
*** bytes (1.0 GB, 1000 MiB) copied, 4.51917 s, 232 MB/s
```

同じように、Qemu 上でも書き込み速度を測定してみました。結果は以下の通りです。

```
$ qemu-system-x86_64 --smp 2 -m 2G -accel hvf -hda debian.qcow2 -display none -daemonize -*** user,hostfwd=tcp::5000-:22 -virtfs local,path=$HOME/Documents/Qemu,security_model=none,mount_***=Shared
$ ssh admin@localhost -p5000
$ mount -t 9p -o noatime,trans=virtio,version=9p2000.L Shared /mnt
$ root@localhost:/mnt# dd if=/dev/urandom of=dat bs=100M count=10 conv=fsync
10+0 records in
10+0 records out
*** bytes (1.0 GB, 1000 MiB) copied, 3.96111 s, 265 MB/s
$ root@localhost:/mnt# dd if=/dev/zero of=dat bs=100M count=10 conv=fsync
10+0 records in
10+0 records out
*** bytes (1.0 GB, 1000 MiB) copied, 1.89221 s, 554 MB/s
```

Qemu 上でも Docker Desktop と同等の結果が得られましたが、書き込み速度は更に高速でした。

このような結果を受けて、私は Docker Desktop を使わずに Qemu で Docker コンテナを動かすことを検討しています。特に、Virtualbox 7 以降のバージョンではネットワーク周りでの問題が発生しやすいため、Qemu の利用をおすすめします。

また、UTM についても触れてみましたが、Gentoo の起動にはまだ問題があるようです。興味のある方は、ぜひ試してみてください。

それでは、今回のお話は以上です。Qemu の利用によって高速な仮想環境が手に入ることをご紹介しました。お役に立てれば幸いです！
