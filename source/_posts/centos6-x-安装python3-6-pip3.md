---
title: centos6.x 安装python3.6&pip3
date: 2018-09-17 11:41:54
tags:
    - python3.6
    - pip3
---
<center>![](images-3.jpeg)</center>
### 安装环境准备
```bash
yum -y groupinstall 'Development Tools'
yum install -y zlib-devel bzip2-devel  openssl-devel ncurses-devel
```
### 下载并解压python3.6.1
```bash
wget https://www.python.org/ftp/python/3.6.1/Python-3.6.1.tgz
tar zxvf  Python-3.6.1.tgz
```
### 编译安装
```bash
cd Python-3.6.1
./configure --prefix=/usr/local/python3
make && make install
```
### 设置环境变量
```bash
echo 'export PATH=$PATH:/usr/local/python3/bin' >> /etc/profile
```
### 刷下环境变量

```bash
source /etc/profile
```
### 验证是否安装成功
```bash
python3 -V
pip3 -V
```

