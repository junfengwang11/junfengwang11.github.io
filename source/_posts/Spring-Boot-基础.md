---
title: Spring Boot 简介
date: 2018-08-13 17:00:02
tags:
    - springboot
categories:
    - springboot
---

Spring Boot 是一个轻量级框架，可以完成基于 Spring 的应用程序的大部分配置工作。在本教程中，将学习如何使用 Spring Boot 的 starter、特性和可执行 JAR 文件结构，快速创建能直接运行的基于 Spring 的应用程序。
### Spring Boot 是什么？
Spring Boot 的目的是提供一组工具，以便快速构建容易配置的 Spring 应用程序。Spring Boot 使您能轻松地创建独立的、生产级的、基于 Spring 且能直接运行的应用程序。基本上讲，这意味着您只需极少的配置，就可以快速获得一个正常运行的 Spring 应用程序，而且这些极少的配置采用了注释的形式。
### 关键点
#### Starter
starter 是 Spring Boot 的一个重要组成部分，用于限制您需要执行的手动配置依赖项数量。starter 实际上是一组依赖项（比如 Maven POM），这些依赖项是 starter 所表示的应用程序类型所独有的。所有 starter 都使用以下命名约定：spring-boot-starter-XYZ，其中 XYZ 是想要构建的应用程序类型。下面是一些常用的starter及时说明
* spring-boot-starter-web 用于构建 RESTful Web 服务，它使用 Spring MVC 和 Tomcat 作为嵌入式应用程序容器。
* spring-boot-starter-jersey 是 spring-boot-starter-web 的一个替代，它使用 Apache Jersey 而不是 Spring MVC。
* spring-boot-starter-jdbc 用于建立 JDBC 连接池。它基于 Tomcat 的 JDBC 连接池实现。

#### 自动配置
Spring Boot 会使用其 @EnableAutoConfiguration 注释自动配置您的应用程序。自动配置基于类路径中的 JAR 和定义 bean 的方式：
* Spring Boot 使用您在 CLASSPATH 中指定的 JAR，形成一个有关如何配置某个自动行为的观点。例如，如果类路径中有 H2 数据库 JAR，而且您没有配置任何其他 DataSource bean，您的应用程序会自动配置一个内存型数据库。
* Spring Boot 使用您定义 bean 的方式来确定如何自动配置自身。例如，如果您为 JPA bean 添加了 @Entity 注释，Spring Boot 会自动配置 JPA，这样您就不需要 persistence.xml 文件。

#### 运行
Spring Boot 旨在帮助开发人员快速创建能直接运行的应用程序。为实现该目的，它会将应用程序及其依赖项包装在一个可执行 JAR 中。你可以以jar的形式直接运行你的程序，如：
```bash
java -jar PATH_TO_EXECUTABLE_JAR/executableJar.jar
```
### 优势|劣势
#### 优势
* 使用 Spring 项目引导页面可以在几秒构建一个项目
* 方便对外输出各种形式的服务，如 REST API、WebSocket、Web、Streaming、Tasks
* 非常简洁的安全策略集成
* 支持关系数据库和非关系数据库
* 支持运行期内嵌容器，如 Tomcat、Jetty
* 强大的开发包，支持热启动
* 自动管理依赖
* 自带应用监控
* 支持各种 IED，如 IntelliJ IDEA 、NetBeans

#### 劣势
集成度过高，没有一定的经验你根本就不知道springboot自动做了什么，对于新入门的程序员来说这是件很可怕的事情

参考资料：
* [Spring Boot 基础](https://www.ibm.com/developerworks/cn/java/j-spring-boot-basics-perry/index.html)
* [Spring Boot 优缺点](https://www.zhihu.com/question/39483566)




