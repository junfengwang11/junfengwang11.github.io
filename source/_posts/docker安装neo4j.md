---
title: docker安装neo4j
date: 2018-08-06 17:25:23
tags:
    - docker
    - neo4j
categories:
    - 知识图谱
---
# 拉取镜像
```bash
docker pull neo4j:3.4
```
# 启动镜像
```bash
docker run  --publish=7474:7474 --publish=7687:7687  --volume=/data/docker/neo4j/data:/data --volume=/data/docker/neo4j/logs:/logs 
```

