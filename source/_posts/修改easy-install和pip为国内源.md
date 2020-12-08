---
title: 修改easy_install和pip为国内源
date: 2018-08-13 10:06:42
tags:
    - pip
    - easy_install
categories:
    - python
---

因为一些众所周知的原因，easy_install和pip默认的源速度实在是太慢了，严重影响到正常的开发工作，因此需要将其默认源修改为国内的源，以下相关配置采用的是豆瓣的源，若使用其他的源请自行替换，本文的示例仅为Mac和Linux系统，其他版本的系统（Windows）请自行谷歌。
##### pip源修改
```bash
cd ~
mkdir .pip
vi .pip/pip.conf
```
在pip.conf中输入以下内容

```bash
[global]
index-url = http://pypi.douban.com/simple
trusted-host = pypi.douban.com
```
##### easy_install源修改
```bash
cd ~
vi .pydistutils.cfg
```
在.pydistutils.cfg输入以下内容

```bash
[easy_install]
index-url=http://pypi.douban.com/simple
```




