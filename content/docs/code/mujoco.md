# Mujoco

## Installation

```sh
cd ~
mkdir .mujoco # 将下载的安装包解压于此

# bashrc 中添加
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/agnel/.mujoco/mujoco-3.0.1/bin
```

## New robot

urdf中添加如下标签。mujoco不支持dae
```xml
  <mujoco>
        <compiler 
        meshdir="path/to/meshes"
        balanceinertia="true" 
        discardvisual="false" />
  </mujoco>
```


```sh
# urdf 转 xml
cd .mujoco/mujoco-3.0.1/bin
./compile path/to/urdf {path}/robot.xml

# 测试
./simulate path/to/xml
```


如果含有浮动基座，data.qpos的前7位是xyz+四元数， data.vel的前6位是基座速度