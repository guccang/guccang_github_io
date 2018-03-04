---
title: docker
date: 2018-02-26 18:46:14
tags: 
- docker
- all
---

1: centos 下安装docker
docker version出错
显示docker -d xxxxx
yum update 后ok centos6.5 下出的问题。
centos7下没有问题。

2:私有库建立后push时错误 docker -d xxxxx
cd /etc/docker 创建daemon.json文件
内容如下
{"insecure-registries":["192.168.211.128:5000"]}

3：尽情享受docker吧。

、、、、、、、、、、、、、、、、、
镜像改变后保存镜像改变
docker commit -m "centos add ssh" -a "Docker newbee" 容器Id centos:1.1

私有仓库
docker run -d -p 5000:5000 registry
docker push localhost:5000/centos
curl localHost:5000/v2/_catalog

搜索mono镜像
docker search mono
显示所有镜像
docker images
获取镜像(DockerHub)
docker pull mono:tag
删除镜像
docker rmi mono:tag
上传镜像
docker push registryAddress/mono:tag


创建容器 运行镜像
docker run -itd mono /bin/bash
开始容器
docker start containerId
停止容器
docker stop containerId
移除容器（容器需要停止）
docker rm containerId 
打标签
docker tag mono:1.0 mono:1.1
进入容器，挂在宿主文件件到docker容器中
docker exec -it -v /root/data:/data containerId /bin/bash
进入容器
docker attach containerId
