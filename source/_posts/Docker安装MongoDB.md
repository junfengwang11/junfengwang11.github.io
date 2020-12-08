---
title: Docker安装MongoDB
date: 2018-08-07 10:21:21
tags:
    - docker
    - mongodb
    - centos
categories:
    - docker
---

## 拉取镜像
```bash
docker pull mongo:3.6.5
```
## 创建mongodb的工作目录并赋予权限
```bash
mkdir -p /data/mongo
chown 1000:1000 /data/mongo
```
## 新建并启动mongodb
```bash
docker run --name mongo -p 27017:27017 -v /data/mongo:/data/db -d mongo:3.6.5 --auth
```
## 新建mongodb管理员
### 进入 mongo shell
```bash
docker exec -it mongo mongo admin
```
### 创建管理员
```bash
db.createUser({ user: 'admin', pwd: '123456', roles: [ { role: 'userAdminAnyDatabase', db: 'admin' } ]});
```


