---
title: "macOSでのQemuの使用とDocker Desktopとの比較"
emoji: ""
type: "25-砂場"
topics: ['25-砂場']
published: False
---

# macOSでのQemuの使用とDocker Desktopとの比較

# macOSでのQemuの使用とDocker Desktopとの比較

最近、macOS (x86_64) 上でのQemuの使用について知ったのですが、HVF（Hypervisor Framework）を使用することができるそうです。普通に使用する分には高速であり、Docker Desktopと比較してみると、Qemuの方が2倍ほど高速でした。

とりあえず、debianをインストールしてみることにしました。

```shell
$ qemu-system-x86_64 --smp 2 -m 2G -accel hvf -cdrom debian-12.1.0-amd64-netinst.iso -hda debian.qcow2
```

その後、Docker Desktop（debian）からホストへの書き込み速度を比較してみました。

```shell
$ docker run --rm -it -v ~/Documents/Docker:/mnt debian
# root@d199a88b8c1e:/mnt# dd if=/dev/urandom of=dat bs=100M count=10 conv=fsync
# root@d199a88b8c1e:/mnt# dd if=/dev/zero of=dat bs...
```

意外にも、Qemuの方が使えそうな結果でしたので、Docker Desktopを切り替えてQemu上にDockerを立ち上げることにしようかと考えています。

また、最近はVirtualboxはホスト側のネットワーク周りで問題が発生することが多く、使用しなくなりました。UTM（Universal Turing Machine）については興味がありますが、Gentooが起動しないという問題があるため、残念ながら関心はありません。

これからは、Qemuを中心に使用していこうと思います。新しいテクノロジーに挑戦することで、より良い開発環境を作り上げることができると信じています。
