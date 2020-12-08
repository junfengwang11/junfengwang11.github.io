---
title: docker常用命令
date: 2018-08-07 09:44:07
tags:
    - docker
categories:
    - docker
---
### 将待挂载的本地文件赋予权限
```bash
chcon -Rt svirt_sandbox_file_t /tmp #tmp为待挂载的文件
chown 1000:1000 /tmp #tmp为待挂载的文件
```
### 搜索镜像

 ```bash
 docker search ubuntu:16.04 
 ```
### 下载镜像
 ```bash
 docker pull ubuntu:16.04 
 ```
### 列出本地的镜像
 ```bash
 docker images
 ```
### 删除本地某个镜像
 ```bash
docker rmi 镜像ID # 通过第四部的命令可以查看镜像ID
 ```
#### tip：删除镜像时需要先通知运行该镜像的容器
### 新建并启动容器
```bash
docker run -t -i ubuntu:14.04 /bin/bash
```
上面的命令是启动一个 bash 终端，允许用户进行交互
### 停止运行中的容器
```bash
    docker 容器ID stop 
```
### 删除容器
```bash
    docker rm  容器ID
```
### 提交对容器的修改
```bash
 docker commit 容器ID learn/ping # learn/ping为容器tag
```


