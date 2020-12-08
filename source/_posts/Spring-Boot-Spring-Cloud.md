---
title: Spring Boot && Spring Cloud
date: 2019-04-27 19:00:40
tags:
    - Spring Boot
    - Spring Cloud
    - 微服务
categories:
    - 微服务
    - Spring Cloud
---
### 简介
Spring Boot先于Spring Cloud问世，Spring Boot相当于脚手架，借助它可以快速搭建“房子”，它本身不具备任何功能属性，只是普通房间，没有任何其它功能。

### 什么是Spring Boot
Spring Boot简化了基于Spring的应用开发，通过少量的代码就能创建一个独立的、产品级别的Spring应用。Spring Boot为Spring平台及第三方库提供`开箱即用`的设置，这样你就可以有条不紊的开始；大多数的Spring Boot应用仅仅只需要少量的Spring配置。
Spring Boot是由`Pivotal`团队提供的全新框架，其设计目的是用来简化Spring应用的初始搭建及开发工程。该框架采用了特定的方式进行配置，从而使开发人员不再需要定义样板化的配置。换句话来说，你也可以将Spring Boot理解成并不是什么新的框架，它默认配置了很多框架的使用方式，就像maven整合了所有的jar包，Spring Boot整合了所有的框架。
Spring Boot的核心思想就是`约定大于配置，一切自动完成`。采用Spring Boot可以大大的简化你的开发模式，所有你想集成的常用框架，它都有对应的组建支持。

### 什么是Spring Cloud
Spring Cloud是一系列框架的有序集合。它利用Spring Boot的开发便利性巧妙滴简化了分布式系统基础设施的开发，如服`务发现注册`、`配置中心`、`消息总线`、`负载均更`、`断路器`、`数据监控`等，都可以用Spring Boot的开发风格做到一键启动和部署。Spring并未重复制造轮子，它只是将目前各家公司开发的比较成熟、经得起实际考验的服务框架组合起来，通过Spring Boot风格进行再封装屏蔽掉负责的配置和实现原理，最终给开发者留出了一套`简单易懂`、`容易部署和维护`的分布式系统开发工具包。
微服务是可以`独立部署`、`水平扩展`、`独立访问`的服务单元，Spring Cloud就是这些微服务的大管家；采用微服务这种架构之后，项目的数量会变得非常多，Spring Cloud做为大管家就需要提供各种方案来维护整个生态。Spring Cloud本身并不会提供具体功能性的操作，它更专注于服务之间的`通讯`、`熔断`、`监控`等。因此需要很多的组建来完成只一套功能的支持。

### 总结
Spring Boot和Spring cloud的关系如下：Spring Boot是Spring的一套快速配置脚手架，可以基于Spring Boot快速开发单个微服务，Spring Cloud是一个基于Spring Boot实现的云应用开发工具；Spring Boot专注于快速、方便集成的单个微服务个体，Spring Cloud关注全局的服务治理框架；Spring Boot是用了默认大于配置的理念，很多集成方案已经提前帮你选择好了，能不自己配置就不要自己配置，Spring Cloud很大的一部分是基于Spring Boot来实现的。Spring Boot可以脱离开Spring Cloud独立使用来开发项目，但是Spring Cloud则不能离开Spring Boot，属于依赖的关系。
