##### 1、 安装mingw
安装 配置环境变量即可

还可以通过msys2来安装mingw，msys2是一个windows包管理工具
```shell
pacman -Syu
pacman -Su
pacman -S --needed base-devel  mingw-w64-x86_64-toolchain
```
##### 2、加载c/c++插件
done