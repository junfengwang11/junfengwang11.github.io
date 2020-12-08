---
title: centos时钟同步
date: 2018-08-10 09:50:00
tags:
    - centos
    - 时钟同步
    - ntpdate
    - crontab
categories:
    - 服务器
---
在使用centos服务器的时候，有时会遇到时间不准确的问题，尤其是在搭建服务器集群的时候会因服务器时间不准确给集群服务器的搭建带来各种未知的问题，下面介绍一种centos服务器使用NTP与互联网上的时间服务器进行时钟同步的方法。

### 安装ntpdate
```bash
yum install -y ntpdate
```
### 将服务器的时区调整为东八区
```bash
cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
```
### 执行时钟同步动作
```bash
ntpdate us.pool.ntp.org
```
### 利用crontab，定时同步时钟

```bash
crontab -e #编辑当前用户的定时任务
```
```bash
0-59/10 * * * * /usr/sbin/ntpdate us.pool.ntp.org | logger -t NTP #设置为每十分钟同步一次
```

经过以上4步，centos服务器时间不准确的问题即可得到解决，当然你也可以在服务器集群上搭建一个时间服务器，其他的服务器与该服务器进行时钟同步即可。


