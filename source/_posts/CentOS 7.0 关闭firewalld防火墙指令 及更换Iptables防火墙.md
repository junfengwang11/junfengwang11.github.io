---
title: CentOS 7.0 关闭firewalld防火墙指令 及更换Iptables防火墙
date: 2019-03-14 17:29:55
tags:
    - centos
    - 防火墙
categories:
    - 服务器
---
#### Disable Firewalld Service.
```shell
 systemctl mask firewalld
```
#### Stop Firewalld Service.
```shell
 systemctl stop firewalld
 ```
#### Install iptables service related packages.
```shell
 yum -y install iptables-services
```
#### Make sure service starts at boot:
```shell
 systemctl enable iptables
```

#### Now, Finally Let’s start the iptables services.
```shell
 systemctl start iptables
```




