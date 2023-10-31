---
title: Linux
lintitle: Linux
type: book
data: 2023.10.31
weight: 2
---

## Linux

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