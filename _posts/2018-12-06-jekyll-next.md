---
title: Jekyll + NexT
date: 2018-12-06
categories:
- Jekyll
- NexT
tags:
- Jekyll
- NexT
---

## 1. 安装Ruby

* 下载安装包
![](/assets/images/jekyll/1.png)

* 这里安装路径不要有空格，不然之后的安装会报错，中文路径也不建议。
![](/assets/images/jekyll/2.png)

* 把`MSYS2 ...`勾选上，默认应该是选中的，下一步
![](/assets/images/jekyll/3.png)

* 选中`Run 'ridk install...'`，直接`Finish`
![](/assets/images/jekyll/4.png)

* 弹出命令窗口后，键入`1`enter，等待安装完成
![](/assets/images/jekyll/5.png)
![](/assets/images/jekyll/6.png)

## 2. 安装Jekyll
```bash
gem install jekyll

jekyll -v //查看版本，验证是否安装成功
```
## 3. 安装NexT
```bash
gem install bundler //安装Bundler

git clone https://github.com/Simpleyyt/jekyll-theme-next.git //下载 NexT 主题
cd jekyll-theme-next

bundle intall //安装依赖

bundle exec jekyll server //运行Jekyll
```
* 运行`Jekyll`前需要对`_config.yml`做一些简单配置，不然会因为某些字段缺失值而启动不成功
![](/assets/images/jekyll/7.png)

> 1. [使用Github pages+jekyll搭建自己的博客（windows版）](https://www.cnblogs.com/zjjDaily/p/8695978.html)
> 2. [NexT](http://theme-next.simpleyyt.com/getting-started.html)