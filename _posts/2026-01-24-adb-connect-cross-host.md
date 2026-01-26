---
tags: [adb]
title: adb-connect-cross-host
created: '2026-01-24T09:48:27.501Z'
modified: '2026-01-24T13:11:57.114Z'
---

有时可能需要在A主机上使用adb远程连接B主机上的android设备或者模拟器，下面针对这两种场景介绍实现的细节。

## 真机场景

默认情况下adb只会监听localhost，所以需要先杀死B主机上的adb server：

```shell
adb kill-server
```

然后以全网监听模式启动adb server：

```shell
adb -a start-server
```

再然后以tcpip模式重启设备中的adbd：

```shell
adb tcpip 5555
```

最后进行端口转发：

```shell
adb forward tcp:5555 tcp:5555
```

这时A主机可以通过如下命令连接B主机上的android设备。

## 模拟器场景

模拟器场景下，由于android studio会自动启动adb server，所以即便杀死adb server，也会立刻被android studio拉起，这时再以全网监听模式启动adb server不会生效，需要保证启动adb server的时候android studio没有运行，使用如下命令启动adb server后，再启动android studio和模拟器：

```shell
adb -a start-server
```

由于android studio启动模拟器时本身就已经启动了tcpip模式，所以不再需要重启模拟器中的adbd，但是android studio将模拟器的5555端口转发到了localhost:5555，所以依然无法远程连接，仍需进行端口转发：

```shell
adb forward tcp:5555 tcp:5555
```

这时A主机可以通过如下命令连接B主机上的android模拟器。

总结：关键在于启动adb server时的-a参数，不带该参数只能在localhost范围内通过tcp连接设备。
