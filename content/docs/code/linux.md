---
title: Linux
linktitle: Linux
type: book
data: 2023.10.31
weight: 1
---

## Linux

### Installation

1. 制作启动盘

- 下载镜像
```
官网下载
https://www.ubuntu.com/download
清华大学镜像站下载
https://mirrors.tuna.tsinghua.edu.cn/ubuntu-releases/18.04/
```

- 下载U盘制作软件
```
rufus
https://rufus.ie/
```

2. 安装


```sh
# 小鱼一键安装
wget http://fishros.com/install -O fishros && . fishros
```

### Autostart

**Service**

```sh
cd /etc/systemd/usr/
touch test.service
sudo chmod 664 test.service
```

```sh
[Unit]
Description=autostart service

[Service]
Type=oneshot
ExecStart=/bin/su unitree -c 'sh /home/unitree/test.sh'

[Install]
WantedBy=default.target
```

```sh
sudo systemctl enable test.service
```

### Serial

ubuntu打开串口需要sudo权限

解决办法:
更改串口设备的权限：你可以更改串口设备文件的权限，使当前用户具有对其的读写权限。执行以下命令将设备文件的所有者更改为当前用户：
```bash
sudo chown $USER:$USER /dev/ttyUSB0
```