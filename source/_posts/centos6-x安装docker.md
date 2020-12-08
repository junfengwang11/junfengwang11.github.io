---
title: centos6.x安装docker
date: 2018-08-06 18:37:04
tags: 
    - centos6
    - docker
categories:
    - docker
---
# tips
```bash
不建议在centos6系列的服务器上安装，会带来各种未知的问题
```

## 安装EPEL仓库
```bash
rpm -iUvh http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
```
## 更新yum源
```bash
yum update -y
```
## 安装docker包
```bash
yum -y install docker-io
```
## 启动 docker 守护进程
```bash
 service docker start
```
## 配置让 docker 服务随系统自动启动
```bash
sudo chkconfig docker on
```
## 验证 docker 是否安装成功
```bash
docker --version
```



