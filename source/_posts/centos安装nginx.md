---
title: centos安装nginx
date: 2018-08-05 10:06:42
tags:
    - centos
    - nginx
categories:
    - 中间件
---

<center>![](bg2018022701.png)</center>

### 在/etc/yum.repos.d/目录下创建nginx.repo
```bash
cd /etc/yum.repos.d/ 
vim nginx.repo
```
### 填写如下内容
```bash
[nginx]
name=nginx repo
baseurl=http://nginx.org/packages/centos/$releasever/$basearch/
gpgcheck=0
enabled=1
```
保存，则会产生一个/etc/yum.repos.d/nginx.repo文件
### 安装nginx
```bash
yum install nginx -y
```
### 启动nginx
```bash
service nginx start
```
### 将nginx加入开机启动
```bash
chkconfig nginx on
```
### 开放防火墙
```bash
iptables -I INPUT 5 -i eth0 -p tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
 
service iptables save
 
service iptables restart
```
### nginx常用命令
```bash
service nginx start # 启动
service nginx stop # 停止
service nginx restart # 重启
```


