---
title: jenkins
date: 2018-02-26 18:43:44
tags: 
- jenkins
- all
---
jenkins 使用部署相关

1 jenkins理解
使用jenkins来自动化构建部署工程
开发-git/svn更新-编译-测试-发布
jenkins除了开发外后面的步骤都可以自动化完成
开发完后，监控svn变动，自动跟新svn，编译工程，测试项目，发布项目
jenkins使用起来特别简单易用。
jenkins master-slave架构
master放到linux上易于维护稳定性高
slave1: vs2015项目 放到windows上方便编译测试
slave2: ios项目放到mac上方便编译测试
组成了 master-slave1/slave2这样的mater-slave架构

2 使用到的知识点
linux下安装运行jenkins
linux shell脚本自动化部署使用
windows bat脚本自动化部署使用
mac shell脚本自动化部署使用
jenkins用来管理上述逻辑按照指定步骤顺利的进行。

3 具体步骤

