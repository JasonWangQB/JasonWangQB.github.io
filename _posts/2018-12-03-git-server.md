---
title: Git服务器搭建
date: 2018-12-03 14:30:18
avatar: Jason Wang
categories: 
- Git
tags: 
- Git
---

## 1.安装Git
```bash
yum install git
```
创建一个git用户
```bash
useradd git
```

## 2.创建登录证书
```bash
cd /home/git
mkdir /.ssh
chmod 755 .ssh
touch .ssh/authorized_keys
chmod 644 .ssh/authorized_keys
```
## 3.初始化Git仓库
```bash
cd /usr/local
mkdir gitserver
chown git:git gitserver/
cd gitserver

git init --bare share.git

chown -R git:git share.git //把仓库所属用户改为git
```

## 4.克隆仓库
```bash
git clone git@192.168.1.1:/usr/local/share.git
```