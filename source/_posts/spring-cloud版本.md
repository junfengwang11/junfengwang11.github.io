---
title: spring cloud版本
date: 2019-04-23 19:22:34
tags: 
    - spring cloud
    - version
categories:
    - spring cloud
    - 微服务
---
Spring Cloud是一个由众多独立子项目组成的大型综合项目，每个子项目有不同的发行节奏，都维护着自己的发布版本号。Spring Cloud通过一个资源清单BOM（Bill of Materials）来管理每个版本的子项目清单。为避免与子项目的发布号混淆，所以没有采用版本号的方式，而是通过命名的方式。这些版本名称的命名方式采用了伦敦地铁站的名称，同时根据字母表的顺序来对应版本时间顺序，比如：最早的Release版本：Angel，第二个Release版本：Brixton，然后是Camden、Dalston、Edgware，目前最新的是Finchley版本。
当一个版本的Spring Cloud项目的发布内容积累到临界点或者解决了一个严重bug后，就会发布一个“service releases”版本，简称SRX版本，其中X是一个递增数字。当前官网上最新的稳定版本是Edgware.SR5，里程碑版本是Finchley.M9。下表列出了这两个版本所包含的子项目及各子项目的版本号。
<center>![](1556019194673.jpg)</center>