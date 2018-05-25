---
title: Linux运行jar包
date: 2018-02-09 14:30:18
avatar: Jason Wang
tags: [Linux,Java]
---

### 1. 方式一
```bash
java -jar xxx.jar
```
> 当前ssh窗口被锁定，可按CTRL + C打断程序运行，或直接关闭窗口，程序退出

### 2. 方式二
```bash
java -jar xxx.jar & // &代表在后台运行
```
> 当前ssh窗口不被锁定，但是当窗口关闭时，程序中止运行。

### 3. 方式三
```bash
nohup java -jar XXX.jar &
```
> nohup 意思是不挂断运行命令，当账户退出或终端关闭时，程序仍然运行。

> 当用 nohup 命令执行作业时，缺省情况下该作业的所有输出被重定向到nohup.out的文件中，除非另外指定了输出文件。

### 4. 方式四
```bash
nohup java -jar XXX.jar >temp.txt &
```
> 解释下 `>temp.txt`，`command >out.file`是将command的输出重定向到out.file文件，即输出内容不打印到屏幕上，而是输出到out.file文件中。

### 5. 后台任务处理
```bash
jobs // 查看后台运行任务，列出所有后台执行的作业，并且每个作业前面都有个编号。

fg [编号] // 将某个作业调回前台控制，只需要 fg + 编号即可

netstat -nlp |grep :8080 // 查看某端口占用的线程的pid

kill -9 [pid] // 强迫终止进程
```