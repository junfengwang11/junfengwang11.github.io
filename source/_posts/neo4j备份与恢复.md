---
title: neo4j备份与恢复
date: 2018-08-28 10:06:04
tags:
    - neo4j
categories:
    - 知识图谱
---
<center>![](neo4j_notag_whitebg.png)</center>

**tips 本文涉及到的备份和恢复命令均在社区版的neo4j中验证通过，执行命令前需要先关闭neo4j数据库**

* 在实时应用程序中，我们需要定期备份应用程序数据库，以便在任何故障点恢复到某种工作状态
* 社区版neo4j不支持热备份，备份和恢复都需要停止neo4j的服务
* 企业版neo4j支持热备，第一次是全量备份，后续是增量备份


Neo4j的neo4j-admin工具提供 dump 和 load 功能，可使用neo4j-admin进行数据的备份和导出

##### 备份

```bash
neo4j-admin dump --database=graph.db --to=/opt/neo4j/backup
```
##### 恢复
```bash
neo4j-admin load --from=/opt/neo4j/backup --database=graph.db --force
```

**注意：**
如果还原后数据库无法启动，则到 neo4j.conf中将如下属性前的#号去掉，使其生效
<center>![](Fv-Xt1PjUcMFJWZXc90BOt5_LO7H)</center>


