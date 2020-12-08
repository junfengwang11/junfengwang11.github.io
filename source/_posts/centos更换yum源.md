---
title: centos更换yum源
date: 2018-08-10 09:40:42
tags:
    - centos5
    - centos6
    - centos7
    - yum源
categories:
    - 服务器
---

### 备份你的原始镜像源，以免后续出错后可以恢复
```bash
mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
```
### 下载新的CentOS-Base.repo 到/etc/yum.repos.d/
* centos5

```bash
wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-5.repo
```
* centos6

```bash
wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-6.repo
```
* centos7

```bash
wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
```

### 运行yum makecache生成缓存
```bash
yum clean all
yum makecache
```


