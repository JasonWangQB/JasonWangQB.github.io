---
title: RXTXcomm串口使用及IDEA GUI Form，Maven打包
date: 2018-04-12 14:30:18
avatar: Jason Wang
categories: 
- Java
- IDEA
tags: 
- RXTXcomm 
- IDEA GUI Form 
- bat
---

## 1. RXTXcomm.jar的使用
- 下载`RXTXcomm.jar`文件，压缩包解压后在文件夹下有`RXTXcomm.jar`，`rxtxParallel.dll`，`rxtxSerial.dll`这三个文件。
- 将`RXTXcomm.jar`复制到%JAVA_HOME%\jre\lib\ext文件夹下，将`rxtxParallel.dll`，`rxtxSerial.dll`复制到%JAVA_HOME%\jre\lib文件夹下。JDK是`x86`的，复制`x86`版本的文件；JDK是`x64`的，复制`x64`版本的文件，jar包可能不会有什么差异，dll文件是存在差异的。
- 项目中引入jar包即可使用

## 2. IDEA GUI Form，Maven打包问题
添加如下依赖，用于处理GUI Form，maven生成的jar包才可以运行，反之运行会报错。
```java
<dependency>
    <groupId>com.intellij</groupId>
    <artifactId>forms_rt</artifactId>
    <version>7.0.3</version>
</dependency>
```

## 3. Windows下复制文件bat问题
由于手动复制`RXTXcomm.jar`，`rxtxParallel.dll`，`rxtxSerial.dll`这三个文件比较麻烦，就编写了个bat文件执行。
```bash
echo java目录 %JAVA_HOME%
echo 当前目录 %cd%

copy "%cd%\mfz-rxtx-2.2-20081207-win-x64\RXTXcomm.jar" "%JAVA_HOME%\jre\lib\ext"
copy "%cd%\mfz-rxtx-2.2-20081207-win-x64\rxtxSerial.dll" "%JAVA_HOME%\jre\bin"
copy "%cd%\mfz-rxtx-2.2-20081207-win-x64\rxtxParallel.dll" "%JAVA_HOME%\jre\bin"

java -jar GUI.jar

pause
```
这里出现了命令执行失败错误，是因为之前路径中有` `空格导致的错误，为路径加上`""`引号后问题解决
