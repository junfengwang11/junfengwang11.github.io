---
title: centos安装git2.3
date: 2018-09-06 17:56:53
tags:
    - centos
    - git
categories:
    - 中间件
---

<center>![](Git-Logo-2Color.png)</center>

##### 安装依赖的包

```bash
sudo yum -y update
sudo yum install -y curl-devel expat-devel gettext-devel openssl-devel zlib-devel gcc perl-ExtUtils-MakeMaker
```

##### 下载git源码并解压缩
```bash
wget https://www.kernel.org/pub/software/scm/git/git-2.3.0.tar.gz
tar -zxvf git-2.3.0.tar.gz
cd git-2.3.0
```
##### 编译安装
```bash
make prefix=/usr/local/git all
sudo make prefix=/usr/local/git install
```
##### 将git安装路径添加到PATH变量
```bash
sudo vim /etc/profile

## 在最后一行添加
export PATH=/usr/local/git/bin:$PATH 保存退出
```
##### 验证是否安装成功
```bash
source /etc/profile
git --version
```


