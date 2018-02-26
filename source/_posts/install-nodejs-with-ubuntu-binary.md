---
title: ubuntu 使用二进制包安装nodejs 
date: 2017-08-03 13:40:45
tags:
- nodejs
- linux
- ubuntu
categories:
- tech
---
Ubuntu默认源里的node版本比较老，node的版本更新的特别快，如果希望使用更新一点的版本，比较推荐使用二进制预编译包进行安装,只需要修改环境变量的指向就可以了。
可以在这里下载到最新的二进制安装包，http://nodejs.cn/download/
二进制包是使用node源码在特定的平台架构预先编译好了可执行文件，所以要根据自己的机器的架构选择合适的包，不然的话ABI不匹配根本无法运行。
我的机器是Ubuntu 14.04 64位，所以我选择Linux 64位,安装步骤如下：

1.下载包

```shell
mkdir /usr/local/src
cd /usr/local/src
sudo wget https://npm.taobao.org/mirrors/node/v8.2.1/node-v8.2.1-linux-x64.tar.xz
```

2.解压包

```shell
sudo tar xvf node-v8.2.1-linux-x64.tar.xz
```

3.添加到系统执行路径

把node与npm加入系统路径环境变量
```shell
vi ~/.bashrc
export PATH="/usr/local/src/node-v8.2.1-linux-x64/bin:$PATH"
source ~/.bashrc
```
4.测试是否安装成功

```shell
node -v
v8.2.1
npm -v
5.3.0
```
job done！
通过npm全局安装的第三方包会放置在你的node-vxxx-linux-x64目录中，没有系统全局的影响。
如果要更换node的版本只需要再下载新版本的node，修改环境变量就可以了。

