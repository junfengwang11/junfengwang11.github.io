---
title: docker安装jenkins
date: 2018-08-06 22:01:08
tags:
    - docker
    - jenkins
    - centos7
categories:
    - docker
---
## 拉取长期支持版镜像
```bash
docker pull jenkins/jenkins:lts
```
## 创建jenkins的工作目录并赋予权限
```bash
sudo mkdir /data/jenkins
sudo chown 1000:1000 /data/jenkins
```
## 新建并启动Jenkins
```bash
sudo docker run -p 8080:8080 -p 50000:50000 -v /data/jenkins:/var/jenkins_home --name jenkins -d jenkins/jenkins:lts
```

## 其他命令
```bash
docker jenkins start # 启动jenkins
docker jenkins stop # 停止jenkins
docker jenkins restart # restart jenkins

docker exec -it jenkins /bin/bash # 进入jenkins容器
```

