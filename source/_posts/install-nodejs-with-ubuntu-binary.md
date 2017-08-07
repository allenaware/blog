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
Ubuntu默认源里的node版本比较老，node的版本更新的特别快，如果大家希望使用更新一点的版本，我个人比较推荐使用预编译二进制包进行安装。
可以在这里下载到最新的二进制安装包，http://nodejs.cn/download/
二进制包是使用node源码在特定的平台架构预先编译好了可执行文件，所以要根据自己的机器的架构选择合适的包，不然的话ABI不匹配根本无法运行。我的机器是Ubuntu 14.04 64位，所以我选择Linux 64位,安装步骤如下：

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

把node与npm加入系统路径,默认/usr/local/bin已经在系统路径之中了，所以我们只需要通过创建软链接即可，软连接的好处是以后node版本升级，只需要下载新的二进制包，修改软连接指向的文件位置就可以了。

```shell
cd /usr/local/bin
sudo ln -s /usr/local/src/node-v8.2.1-linux-x64/bin/node node
sudo ln -s /usr/local/src/node-v8.2.1-linux-x64/lib/node_modules/npm/bin/npm-cli.js npm
```


4.测试是否安装成功


```shell
node -v
v8.2.1
npm -v
5.3.0
```
job done！

