---
title: mvn常用命令大全
date: 2018-10-10 09:46:45
tags:
    - mvn
categories:
    - Java
---
<center>![](maven-logo.jpg)</center>
maven命令除了常用的几个，大部分经常记不住，整理一下，方便查询。
maven 命令的格式为 mvn [plugin-name]:[goal-name]，可以接受的参数如下：

    -D 指定参数，如 -Dmaven.test.skip=true 跳过单元测试；
    -P 指定 Profile 配置，可以用于区分环境；
    -e 显示maven运行出错的信息；
    -o 离线执行命令,即不去远程仓库更新包；
    -X 显示maven允许的debug信息；
    -U 强制去远程更新snapshot的插件或依赖，默认每天只更新一次。

#### 项目相关
1. mvn archetype:create 创建maven项目

    > 创建maven项目：mvn archetype:create
    指定 group： -DgroupId=packageName
    指定 artifact：-DartifactId=projectName
    创建web项目：-DarchetypeArtifactId=maven-archetype-webapp
2. mvn validate 
    验证项目是否正确
3. mvn package 
    maven 打包
4. mvn jar:jar
    只打jar包
5. mvn source:jar
    生成源码jar包
6. mvn generate-sources
    产生应用需要的任何额外的源代码
7. mvn compile
    编译源代码
8. mvn test-compile
    译测试代码
9. mvn test
    运行测试
10. mvn verify
    运行检查
11. mvn clean
    清理maven项目
12. mvn eclipse:eclipse
    生成eclipse项目
13. mvn eclipse:clean
    清理eclipse配置
14. mvn idea:idea
    生成idea项目
15. mvn install
    安装项目到本地仓库
16. mvn:deploy
    发布项目到远程仓库
17. mvn integration-test
    在集成测试可以运行的环境中处理和发布包
18. mvn dependency:tree
    显示maven依赖树
19. mvn dependency:list
    显示maven依赖列表
20. mvn dependency:sources
    下载依赖包的源码
21. mvn install:install-file -DgroupId=packageName -DartifactId=projectName -Dversion=version -Dpackaging=jar -Dfile=path
    安装本地jar到本地仓库
    
#### web相关命令
1. mvn tomcat:run 
    启动tomcat
2. mvn jetty:run
    启动jetty
3. mvn tomcat:deploy
    运行打包部署
4. mvn tomcat:undeploy
    撤销部署
5. mvn tomcat:start
    启动web应用：
6. mvn tomcat:stop
    停止web应用
7. mvn tomcat:redeploy
    重新部署
8. mvn war:exploded tomcat:exploded
    署展开的war文件

**参考资料**
* [30 个常用 Maven 命令](https://zhuanlan.zhihu.com/p/29208926)
    
    


