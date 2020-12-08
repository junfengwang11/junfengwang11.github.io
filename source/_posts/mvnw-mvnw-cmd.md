---
title: mvnw && mvnw.cmd
date: 2019-03-19 11:47:19
tags:
    - mvn
categories:
    - Java
---
当创见一个Spring Boot的应用程序时，在程序的根目录下可以看到 `mvnw` 和 `mvnw.cmd` 这个两个文件，那么这两个文件各自的用途是什么呢？

#### 简介
`mvnw`全程是`maven wrapper`，它的原理是在`maven-wrapper.properties`文件中记录你要使用的`maven`版本，当用户执行`mvnw clean` 命令时，发现当前用户的`maven`版本和期望的版本不一致，那么就可以下载期望的版本，然后用期望的版本来执行`mvn`命令，比如`mvn clean`。
`Maven`是一个常用的构建工具，但是`Maven`的版本和插件的配合并不是那么完美，有时候你需要切换到一个统一的版本，以保证所有东西正常工作。`Gradle`提供了一个`Wrapper`，可以很好解决`maven`版本切换的问题，并且更重要的是不需要预先安装`Gradle`。
#### 安装
```shell
mvn -N io.takari:maven:wrapper
[INFO] Scanning for projects...
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/takari/maven/maven-metadata.xml
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/takari/maven/maven-metadata.xml (662 B at 812 B/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/takari/maven/0.7.4/maven-0.7.4.pom
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/takari/maven/0.7.4/maven-0.7.4.pom (2.3 kB at 4.9 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/takari/takari/27/takari-27.pom
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/takari/takari/27/takari-27.pom (14 kB at 24 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/takari/maven/0.7.4/maven-0.7.4.jar
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/takari/maven/0.7.4/maven-0.7.4.jar (9.0 kB at 24 kB/s)
[INFO] 
[INFO] -------------------------< com.kiwi:kiwismart >-------------------------
[INFO] Building spring-boot-basic 0.0.1-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- maven:0.7.4:wrapper (default-cli) @ kiwismart ---
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/takari/maven-wrapper/0.5.3/maven-wrapper-0.5.3.pom
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/takari/maven-wrapper/0.5.3/maven-wrapper-0.5.3.pom (2.4 kB at 6.8 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/takari/takari-archiver/0.1.9/takari-archiver-0.1.9.pom
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/takari/takari-archiver/0.1.9/takari-archiver-0.1.9.pom (1.8 kB at 4.1 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/takari/takari/15/takari-15.pom
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/takari/takari/15/takari-15.pom (15 kB at 30 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/com/google/guava/guava/14.0.1/guava-14.0.1.pom
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/com/google/guava/guava/14.0.1/guava-14.0.1.pom (5.4 kB at 105 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/com/google/guava/guava-parent/14.0.1/guava-parent-14.0.1.pom
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/com/google/guava/guava-parent/14.0.1/guava-parent-14.0.1.pom (2.6 kB at 12 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/org/apache/commons/commons-compress/1.8.1/commons-compress-1.8.1.pom
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/org/apache/commons/commons-compress/1.8.1/commons-compress-1.8.1.pom (11 kB at 286 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/takari/graph/takari-graph/0.0.3/takari-graph-0.0.3.pom
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/takari/graph/takari-graph/0.0.3/takari-graph-0.0.3.pom (4.7 kB at 13 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/takari/takari/14/takari-14.pom
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/takari/takari/14/takari-14.pom (13 kB at 33 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/org/codehaus/plexus/plexus-utils/3.0.16/plexus-utils-3.0.16.pom
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/org/codehaus/plexus/plexus-utils/3.0.16/plexus-utils-3.0.16.pom (3.4 kB at 9.2 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/com/tinkerpop/blueprints/blueprints-core/2.6.0/blueprints-core-2.6.0.pom
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/com/tinkerpop/blueprints/blueprints-core/2.6.0/blueprints-core-2.6.0.pom (3.6 kB at 8.4 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/com/tinkerpop/blueprints/blueprints/2.6.0/blueprints-2.6.0.pom
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/com/tinkerpop/blueprints/blueprints/2.6.0/blueprints-2.6.0.pom (7.0 kB at 19 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/org/apache/maven/maven-model/3.2.3/maven-model-3.2.3.pom
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/org/apache/maven/maven-model/3.2.3/maven-model-3.2.3.pom (4.1 kB at 9.6 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/org/apache/maven/maven/3.2.3/maven-3.2.3.pom
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/org/apache/maven/maven/3.2.3/maven-3.2.3.pom (23 kB at 45 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/com/github/spullara/mustache/java/compiler/0.8.15/compiler-0.8.15.pom
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/com/github/spullara/mustache/java/compiler/0.8.15/compiler-0.8.15.pom (5.6 kB at 11 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/com/github/spullara/mustache/java/mustache.java/0.8.15/mustache.java-0.8.15.pom
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/com/github/spullara/mustache/java/mustache.java/0.8.15/mustache.java-0.8.15.pom (3.5 kB at 8.6 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/com/squareup/javapoet/1.0.0/javapoet-1.0.0.pom
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/com/squareup/javapoet/1.0.0/javapoet-1.0.0.pom (3.5 kB at 9.4 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/airlift/airline/0.6/airline-0.6.pom
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/airlift/airline/0.6/airline-0.6.pom (6.8 kB at 7.2 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/com/google/guava/guava/12.0/guava-12.0.pom
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/com/google/guava/guava/12.0/guava-12.0.pom (5.3 kB at 152 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/com/google/guava/guava-parent/12.0/guava-parent-12.0.pom
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/com/google/guava/guava-parent/12.0/guava-parent-12.0.pom (2.8 kB at 110 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/org/antlr/antlr4-runtime/4.5/antlr4-runtime-4.5.pom
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/org/antlr/antlr4-runtime/4.5/antlr4-runtime-4.5.pom (2.7 kB at 62 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/org/abego/treelayout/org.abego.treelayout.core/1.0.1/org.abego.treelayout.core-1.0.1.pom
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/org/abego/treelayout/org.abego.treelayout.core/1.0.1/org.abego.treelayout.core-1.0.1.pom (3.1 kB at 6.3 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/takari/maven-wrapper/0.5.3/maven-wrapper-0.5.3.jar
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/takari/takari-archiver/0.1.9/takari-archiver-0.1.9.jar
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/com/google/guava/guava/14.0.1/guava-14.0.1.jar
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/org/apache/commons/commons-compress/1.8.1/commons-compress-1.8.1.jar
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/takari/graph/takari-graph/0.0.3/takari-graph-0.0.3.jar
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/org/apache/commons/commons-compress/1.8.1/commons-compress-1.8.1.jar (366 kB at 2.0 MB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/com/tinkerpop/blueprints/blueprints-core/2.6.0/blueprints-core-2.6.0.jar
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/takari/maven-wrapper/0.5.3/maven-wrapper-0.5.3.jar (51 kB at 87 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/org/apache/maven/maven-model/3.2.3/maven-model-3.2.3.jar
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/takari/takari-archiver/0.1.9/takari-archiver-0.1.9.jar (41 kB at 58 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/com/github/spullara/mustache/java/compiler/0.8.15/compiler-0.8.15.jar
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/com/google/guava/guava/14.0.1/guava-14.0.1.jar (2.2 MB at 2.6 MB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/com/squareup/javapoet/1.0.0/javapoet-1.0.0.jar
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/takari/graph/takari-graph/0.0.3/takari-graph-0.0.3.jar (173 kB at 132 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/airlift/airline/0.6/airline-0.6.jar
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/org/apache/maven/maven-model/3.2.3/maven-model-3.2.3.jar (160 kB at 121 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/org/antlr/antlr4-runtime/4.5/antlr4-runtime-4.5.jar
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/com/github/spullara/mustache/java/compiler/0.8.15/compiler-0.8.15.jar (116 kB at 87 kB/s)
Downloading from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/org/abego/treelayout/org.abego.treelayout.core/1.0.1/org.abego.treelayout.core-1.0.1.jar
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/org/abego/treelayout/org.abego.treelayout.core/1.0.1/org.abego.treelayout.core-1.0.1.jar (26 kB at 19 kB/s)
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/org/antlr/antlr4-runtime/4.5/antlr4-runtime-4.5.jar (374 kB at 250 kB/s)
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/com/tinkerpop/blueprints/blueprints-core/2.6.0/blueprints-core-2.6.0.jar (274 kB at 177 kB/s)
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/io/airlift/airline/0.6/airline-0.6.jar (87 kB at 50 kB/s)
Downloaded from pp-nexus: http://nexus.pengpengla.com:8081/nexus/content/groups/public/com/squareup/javapoet/1.0.0/javapoet-1.0.0.jar (65 kB at 37 kB/s)
[INFO] 
[INFO] Maven Wrapper version 0.5.3 has been successfully set up for your project.
[INFO] Using Apache Maven: 3.6.0
[INFO] Repo URL in properties file: http://nexus.pengpengla.com:8081/nexus/content/groups/public/
[INFO] 
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 13.001 s
[INFO] Finished at: 2019-03-19T11:45:00+08:00
[INFO] ------------------------------------------------------------------------
```
#### 运行
```shell
 mvn -N io.takari:maven:wrapper -Dmaven=3.1.0 ##指定maven版本
./mvnw clean install
```
#### 区别
`mvnw`适用于Linux(bash),`mvnw.cmd` 适用于Windows环境