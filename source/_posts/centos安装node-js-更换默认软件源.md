---
title: centos安装node.js&更换默认软件源
date: 2018-09-18 11:17:51
tags:
    - node
    - npm
---
<center>![](generate-pdf-using-nodejs-thumbnail.png)</center>
### 安装EPEL库
```bash
sudo yum -y install epel-release
```
### 安装nodejs
```bash
sudo yum -y install nodejs
```
### 安装npm
```bash
sudo yum -y install npm
```
### 校验安装
```bash
node --version
npm --version
```
### 更换软件源
#### 创建文件.npmrc
```bash
vim ~/.npmrc
```
#### 添加以下内容并保存
```bash
registry = https://registry.npm.taobao.org/                                                                                                                 
disturl = https://npm.taobao.org/dist                                                                                                                       
sass_binary_site = https://npm.taobao.org/mirrors/node-sass                                                                                                 
electron_mirror = https://npm.taobao.org/mirrors/electron/                                                                                                  
puppeteer_download_host = https://npm.taobao.org/mirrors                                                                                                    
chromedriver_cdnurl = https://npm.taobao.org/mirrors/chromedriver                                                                                           
operadriver_cdnurl = https://npm.taobao.org/mirrors/operadriver                                                                                             
phantomjs_cdnurl = https://npm.taobao.org/mirrors/phantomjs                                                                                                 
selenium_cdnurl = http://npm.taobao.org/mirrors/selenium                                                                                                    
node_inspector_cdnurl = https://npm.taobao.org/mirrors/node-inspector  
```

参考资料

* [如何在 CentOS 安装 node.js](https://blog.csdn.net/lu_embedded/article/details/79138650)
* [npm淘宝镜像](https://gist.github.com/52cik/c1de8926e20971f415dd)





