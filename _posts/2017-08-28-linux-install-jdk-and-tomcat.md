---
title: Linux安装JDK和Tomcat
date: 2017-08-28 14:30:18
avatar: Jason Wang
categories:
- Linux
- Java
tags: 
- Linux
- Java
- JDK
- Tomcat
---
## 1. 安装JDK

- 下载JDK安装包，并解压到对应目录下
```bash
mkdir java
tar -zxvf jdk-8u144-linux-x64.tar.gz -C /java
```

- 配置环境
```bash
vim /etc/profile

export JAVA_HOME=/java/jdk1.8.0_144
export PATH=$JAVA_HOME/bin:$PATH 
export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar 

source /etc/profile #生效配置

java -version #查看版本信息
```
## 2. 安装Tomcat

- 下载Tomcat7,并解压到对应目录下
```bash
mkdir tomcat7
tar -zxvf apache-tomcat-7.0.81.tar.gz -C /tomcat7
```

- 启动Tomcat
```bash
cd /tomcat7/apache-tomcat-7.0.81/bin
./startup.sh
```
  访问地址`http://localhost:8080`查看tomcat是否运行正常


- 根据需要自行配置tomcat和jdk的关联，在startup.sh中添加配置
```bash
chmod -R 777 /tomcat7/apache-tomcat-7.0.81 #修改权限，自行配置
cd /tomcat7/apache-tomcat-7.0.81/bin
./startup.sh
vim startup.sh
JAVA_HOME=/java/jdk1.8.0_144
PATH=$JAVA_HOME/bin:$PATH
CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
```