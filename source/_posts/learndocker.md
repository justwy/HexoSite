---
title: docker简易教程
date: 2016-03-05 16:09:05
tags:
    - docker
    - 教程
---



```java
// 查看所有信息
docker info

// 下载镜像
// 以官方提供的nodejs镜像为例
docker pull node

// 列出下载的景象
docker images

// output:
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
node                latest              5e14c005b7f7        2 days ago          644.2 MB

// 在所下载的镜像（名为node）中实例化一个容器并运行‘node --version’命令
docker run -d --name testNodeVersion node node --version
// output:
1221704c1d4fc56c9aa10cfde877bc629a40b9836c4f7502b35a6e5ae3e9e77b
```

`docker run`之后发现并没有输出node version到console。这是因为使用了`-d`。查看输出：
```java
$ docker logs testNodeVersion
v5.7.1
```
值得一提的是，`--name testNodeVersion`会给容器命名，方便后续引用

如果是long run的命令，可以用｀docker stop <container name> 来停止

```java
// remove the container
docker rm testNodeVersion

// Create a new image from a container's changes
docker commit testNodeVersion test_node_version_img

// List images
docker images
// output
REPOSITORY              TAG                 IMAGE ID            CREATED             SIZE
test_node_version_img   latest              583bcfe54705        3 minutes ago       644.2 MB
node                    latest              5e14c005b7f7        2 days ago          644.2 MB
```

[1] [docker run 具体使用说明](https://docs.docker.com/engine/reference/run/)

[2] [参考教程](http://dockone.io/article/102)
