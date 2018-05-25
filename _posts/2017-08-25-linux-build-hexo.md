---
title: Linux搭建Hexo
date: 2017-08-25 14:30:18
avatar: Jason Wang
categories:
- Linux
- Hexo
tags: 
- Linux
- NodeJS
- Hexo
---
## 1. 安装NodeJS
### 1.1 下载NodeJS安装包，然后将安装包移动到系统目录中；解压到对应的文件夹下，前提是这个文件夹要存在。
```bash
// 不同压缩方式，选择不同解压方式
tar -xvf node-v8.4.0-linux-x64.tar.xz -C /blog
tar -zxvf node-v8.4.0-linux-x64.tar.gz —C /blog
```

### 1.2 添加全局环境变量
- 修改/etc/profile
```bash
vi /etc/profile
export PATH=$PATH:/blog/node-v8.4.0-linux-x64/bin #添加环境变量
source /etc/profile #生效环境变量
echo $PATH #查看环境变量是否添加
```

- 软连接方式
在终端执行echo $PATH可以获取PATH变量包含的内容，系统默认的PATH环境变量包括/usr/local/bin:/usr/bin:/bin:/usr/local/sbin:/usr/sbin:/sbin:，冒号为分隔符。所以我们可以将node和npm链接到/usr/local/bin 目录下如下执行。
```bash
ln -s /blog/node-v8.4.0-linux-x64/bin/node /usr/local/bin/node
ln -s /blog/node-v8.4.0-linux-x64/bin/npm /usr/local/bin/npm
```

## 2. 安装Hexo
- 全局安装 Hexo
```bash
npm install hexo-cli -g
```

- 安装异常Permission denied
```bash
npm config set unsafe-perm true
npm install hexo-cli -g
```

- 初始化博客，并安装依赖包
```bash
mkdir hexo
cd hexo
hexo init
npm install
```
- Hexo常用命令
```bash
hexo server #启动服务
hexo server -s #静态模式
hexo server -p 5000 #更改端口
hexo server -i 192.168.1.1 #自定义 IP
hexo clean #清除缓存 网页正常情况下可以忽略此条命令
```
- 命令缩写
```
hexo n "我的博客" == hexo new "我的博客" #新建文章
hexo p == hexo publish
hexo g == hexo generate #生成
hexo s == hexo server #启动服务预览
hexo d == hexo deploy #部署
```



