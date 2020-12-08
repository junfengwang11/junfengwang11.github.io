---
title: Spring Cloud 微服务架构
date: 2019-05-01 23:34:56
tags:
    - Spring Boot
    - Spring Cloud
    - 微服务
    - 架构
categories:
    - 微服务
    - Spring Cloud
---
### 架构图
<center>![](20180815110816876.png)</center>
### 名词解释
#### Sleuth-链路跟踪
为服务之间的调用提供链路追踪。通过Sleuth可以很清楚的了解到一个服务请求经过了哪些服务，每个服务处理花费了多长。从而让我们可以很方便的理清各微服务间的调用关系。
#### 断路器（Hystrix）
在微服务架构中，根据业务来拆分成一个个的服务，服务与服务之间可以相互调用（RPC），在Spring Cloud可以用RestTemplate+Ribbon和Feign来调用。为了保证其高可用，单个服务通常会集群部署。由于网络原因或者自身的原因，服务并不能保证100%可用，如果单个服务出现问题，调用这个服务就会出现线程阻塞，此时若有大量的请求涌入，Servlet容器的线程资源会被消耗完毕，导致服务瘫痪。服务与服务之间的依赖性，故障会传播，会对整个微服务系统造成灾难性的严重后果，这就是服务故障的“雪崩”效应。Netflix开源了Hystrix组件，实现了断路器模式，SpringCloud对这一组件进行了整合。
#### Turbine集群监控
Turbine 是聚合服务器发送事件流数据的一个工具，用来监控集群下 hystrix 的 metrics 情况；通过turbine可以监控集群的请求量，可以知道系统的请求高峰期，从而更好的知道系统的短板在哪里。
#### Consul服务治理 和Eureka服务治理 
由于Spring Cloud为服务治理做了一层抽象接口，所以在Spring Cloud应用中可以支持多种不同的服务治理框架，比如：Netflix Eureka、Consul、Zookeeper。 
Spring Cloud Consul项目是针对Consul的服务治理实现。Consul是一个分布式高可用的系统，它包含多个组件，但是作为一个整体，在微服务架构中为我们的基础设施提供服务发现和服务配置的工具。它包含了下面几个特性： 服务发现、 健康检查、 Key/Value存储、 多数据中心。由于Consul自身提供了服务端，所以我们不需要像之前实现Eureka的时候创建服务注册中心，直接通过下载consul的服务端程序就可以使用。Consul比Eureka注册支持的更多一些。
#### config配置管理
引入spring cloud config后，我们的外部配置文件就可以集中放置在一个git仓库里，再新建一个config server，用来管理所有的配置文件，维护的时候需要更改配置时，只需要在本地更改后，推送到远程仓库，所有的服务实例都可以通过config server来获取配置文件，这时每个服务实例就相当于配置服务的客户端config client,为了保证系统的稳定，配置服务端config server可以进行集群部署。
#### Nginx
用来做反向代理、负载均衡，当有请求的时候，根据配置的调度策略（加权轮询、IP哈希、最少连接数、一致性哈希）给请求者返回相应的服务器IP。
#### Zuul服务网关
zuul的核心是一系列的filters, 其作用可以类比Servlet框架的Filter；Zuul的主要功能是路由和过滤器。是各种服务的统一入口，同时还会用来提供监控、授权、安全、调度等等；可以通过扩展ZuulFilter，在执行方法之前，做各种检查工作。
### Spring Cloud项目简介
　spring Cloud是基于Spring Boot的一整套实现微服务的框架。他提供了微服务开发所需的配置管理、服务发现、断路器、智能路由、微代理、控制总线、全局锁、决策竞选、分布式会话和集群状态管理等组件。最重要的是，跟spring boot框架一起使用的话，会让你开发微服务架构的云服务非常好的方便。SpringBoot旨在简化创建产品级的 Spring 应用和服务，简化了配置文件，使用嵌入式web服务器，含有诸多开箱即用微服务功能。
Spring Cloud子项目包括：
#### Spring Cloud Config
配置管理开发工具包，可以让你把配置放到远程服务器，目前支持本地存储、Git以及Subversion。
#### Spring Cloud Bus
事件、消息总线，用于在集群（例如，配置变化事件）中传播状态变化，可与Spring Cloud Config联合实现热部署。
#### Spring Cloud Netflix
针对多种Netflix组件提供的开发工具包，其中包括Eureka、Hystrix、Zuul、Archaius等。
#### Netflix Eureka
云端负载均衡，一个基于 REST 的服务，用于定位服务，以实现云端的负载均衡和中间层服务器的故障转移。
#### Netflix Hystrix
容错管理工具，旨在通过控制服务和第三方库的节点,从而对延迟和故障提供更强大的容错能力。
#### Netflix Zuul
边缘服务工具，是提供动态路由，监控，弹性，安全等的边缘服务。
#### Netflix Archaius
配置管理API，包含一系列配置管理API，提供动态类型化属性、线程安全配置操作、轮询框架、回调机制等功能。
#### Spring Cloud for Cloud Foundry
通过Oauth2协议绑定服务到Cloud Foundry，Cloud Foundry是VMware推出的开源PaaS云平台
#### Spring Cloud Sleuth
日志收集工具包，封装了Dapper,Zipkin和HTrace操作。
#### Spring Cloud Data Flow
大数据操作工具，通过命令行方式操作数据流
#### Spring Cloud Security
安全工具包，为你的应用程序添加安全控制，主要是指OAuth2
#### Spring Cloud Consul
封装了Consul操作，consul是一个服务发现与配置工具，与Docker容器可以无缝集成。
#### Spring Cloud Zookeeper
操作Zookeeper的工具包，用于使用zookeeper方式的服务注册和发现。
#### Spring Cloud Stream
数据流操作开发包，封装了与Redis,Rabbit、Kafka等发送接收消息。
#### Spring Cloud CLI
基于 Spring Boot CLI，可以让你以命令行方式快速建立云组件。


　

