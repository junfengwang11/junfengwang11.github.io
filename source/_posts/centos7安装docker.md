---
title: centos7安装docker
date: 2018-08-06 18:36:56
tags: 
    - centos7
    - docker
categories:
    - docker
---
## 更新系统
```bash
sudo yum -y update
```
## 添加 yum 仓库
```bash
sudo tee /etc/yum.repos.d/docker.repo <<-'EOF'
[dockerrepo]
name=Docker Repository
baseurl=https://yum.dockerproject.org/repo/main/centos/$releasever/
enabled=1
gpgcheck=1
gpgkey=https://yum.dockerproject.org/gpg
EOF
```
## 安装docker包
```bash
sudo yum -y install docker-engine
```
## 启动 docker 守护进程
```bash
sudo  systemctl start docker.service
```
## 配置让 docker 服务随系统自动启动
```bash
sudo chkconfig docker on
```
## 验证 docker 是否安装成功
```bash
sudo systemctl enable docker.service
```

