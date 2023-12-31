---
title: Docker
linktitle: Docker
type: book
data: 2023.11.1
weight: 2
---

# 使用安装18.04用作版本生成

1. 安装docker

```bash
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

2. 拉取Ubuntu 18.04镜像

```bash
docker pull ubuntu:18.04
```

3. 运行Ubuntu 18.04容器

```bash
docker run -it --name my-ubuntu ubuntu:18.04
```

这个命令将启动一个新的Ubuntu 18.04容器，并在容器内启动一个交互式shell。-it选项允许你与容器交互，--name my-ubuntu选项将容器命名为my-ubuntu。

之后可以直接运行
``` bash
docker start my-ubuntu
docker attach my-ubuntu
```

4. 安装低版本gcc

一般Ubuntu16是gcc-5, Ubuntu18是gcc-7, Ubuntu20是gcc-9

为了更好的兼容性，我们安装gcc-5

```bash
apt update
apt install -y gcc-5 g++-5 cmake vim libboost-dev libeigen3-dev libyaml-cpp-dev
```

如果cmake找不到
```bash
update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-5 1
update-alternatives --install /usr/bin/c++ c++ /usr/bin/g++-5 1
update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-5 1
update-alternatives --install /usr/bin/cc cc /usr/bin/gcc-5 1
```

5. 编译

```bash
docker cp /path/to/your/code my-ubuntu:/root #放入代码
docker cp my-ubuntu:/root/my_program /path/on/host # 拷回主机
```

## 在X86架构上安装arm64镜像

```bash
sudo apt-get install qemu qemu-user-static binfmt-support

# 在docker中注册qemu的二进制格式(每次关机后都需重新执行次命令)
docker run --rm --privileged docker/binfmt:a7996909642ee92942dcd6cff44b9b95f08dad64

# 拉取并运行ARM64的docker镜像
sudo docker pull arm64v8/ubuntu:18.04
sudo docker run -it arm64v8/ubuntu:18.04
```
