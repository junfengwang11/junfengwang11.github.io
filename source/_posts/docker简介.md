---
title: docker简介
date: 2018-08-03 17:31:26
tags: docker
categories:
    - docker
---

<center>![](whale_0.png)</center>

# 概述
Docker 是世界领先的软件容器平台。开发人员利用 Docker 可以消除协作编码时“在我的机器上可正常工作”的问题。运维人员利用 Docker 可以在隔离容器中并行运行和管理应用，获得更好的计算密度。企业利用 Docker 可以构建敏捷的软件交付管道，以更快的速度、更高的安全性和可靠的信誉为 Linux 和 Windows Server 应用发布新功能。其英文官网为[https://www.docker.com](https://www.docker.com)  ，中文官网为[https://www.docker-cn.com](https://www.docker-cn.com)  

# 架构
<center>![](Framework.jpeg)</center>

## Docker daemon（Docker守护进行）
Docker daemon是一个运行在宿主机（DOCKER_HOST）的后台进程。可通过Docker客户端与之通信。
## client（Docker客户端）
Docker客户端是Docker的用户界面，它可以接受用户命令和配置标识，并于Docker daemon通信。
## Images（Docker镜像）
Docker镜像是一个只读模版，其包含创建Docker容器的说明。它与系统安装光盘类似---使用安装光盘可以安装系统，同理适用Docker镜像可以运行镜像中的程序。
## Container（容器）
容器是镜像的可运行实例。镜像和容器的关系类似于面向对象中，类和对象的关系。可通过Docker API或CLI命令来启停、移动、删除容器。
## Registry（仓库）
Docker Registry是一个集中存储与分发镜像的服务。构建完Docker镜像后，即可在当前宿主机器上运行。但如果需要在其他机器上运行这个镜像，就需要手动复制。此时可借助Docker Registry来避免镜像的手动复制。
一个Docker Registry可包含多个Docker仓库，每个仓库可以包含多个镜像标签，每个标签对应一个Docker镜像。
Docker Registry可以分为共有仓库和私有仓库。最常用的Docker Registry莫过于官方的Docker Hub，其也是默认的Docker Registry。Docker Hub上存放着大量的优秀镜像，可适用Docker命令下载和使用。




