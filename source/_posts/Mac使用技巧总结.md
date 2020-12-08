---
title: Mac使用技巧总结
date: 2018-11-01 16:53:06
tags:
    - mac
categories: Mac
---
<center>![](2018-MacBook-Pro-Logic-800x514.jpg)</center>
#### 显示|隐藏文件夹
##### 隐藏文件夹/opt
```shell
sudo chflags hidden /opt
```
##### 显示文件夹/opt
```shell
sudo chflags nohidden /opt
```
#### 创建软链
```shell
vim ~/.bash_profile
```

```shell
alias ll='ls -l'
alias la='ls -al'
```
#### 安装软件显示所有来源
```shell
sudo spctl --master-disable

```
