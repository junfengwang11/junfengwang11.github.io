---
title: docker安装mysql
date: 2018-08-06 22:24:38
tags:
    - centos7
    - docker
    - mysql:5.7.22
categories:
    - docker
---

## 拉取镜像
```bash
docker pull mysql:5.7.22
```
## 创建mysql的工作目录并赋予权限
```bash
sudo mkdir -p /data/mysql
sudo chown 1000:1000 /data/mysql
```
## 新建并启动mysql
```bash
docker run --name mysql -p 3306:3306 -v /data/mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 -d mysql:5.7.22  --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci 
```
## 其他命令
```bash
docker exec -it mysql bash # 进入mysql容器
docker stop mysql # 停止mysql
```


