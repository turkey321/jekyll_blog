---
layout: post
title:  "符海飞NIIT课堂笔记"
date:   2016-3-6
categories: 笔记 niit
duoshuo: true
---


* content
{:toc}

#板块一:J 2 S E基础

---

##第一部分:JAVA概述

###一.开发语言
1.所有的开发语言都需要经过编译转化成机器指令执行。
2.低级语言接近硬件，编译处理的过程减少，直接可以向硬件发出指令，执行速度快，编码困难，不容易掌握。
高级语言在低级语言的基础上做了更进一步的封装提供了更简便的方法接口便于使用，执行的速度降低。

###二.JAVA分类与内涵
1.JAVA有：J2SE,J2EE,J2ME
J2EE(Java 2 Platform Enterprise Edition ) :
开发企业环境下的应用程序，主要针对web程序开发；
J2SE（Java 2 Platform Stand Edition） :
完成桌面应用程序的开发，是其它两者的基础；
J2ME(Java 2 Platform Micro Edition ) :
开发电子消费产品和嵌入式设备，如手机中的程序；

2.JAVA内涵(3点)
编程语言
开发环境
运行环境

###三.JAVA特点
1.开源
2.跨平台：在各个操作平台的操作系统上引入JVM(java虚拟机)来解决跨平台问题。
（JVM实行步骤：1.载入class文件 2. 验证 3. 解析翻译。）
3.面向对象
4.简单
5.安全性
6.多线程
7.兼顾解释性与编译性语言的特点 

###四.JRE 
 释义:Java Runtime Environment:
java程序的运行环境，java运行的所需的类库+JVM(java虚拟机)。

###五.JDK目录结构  
1.释义:Java Development Kit :java的开发和运行环境，java的开发工具和jre。
2.bin目录：存放可执行的指令文件。   例： java.exe   javac.exe

###六.配置环境变量
1.目的:让java jdk\bin目录下的工具，可以在任意目录下运行，原因是，将该工具所在目录告诉了系统，当使用该工具时，由系统帮我们去找指定的目录。

环境变量的配置：
    1）：永久配置方式：JAVA_HOME=%安装路径%\Java\jdk
	                  path=%JAVA_HOME%\bin
	2）：临时配置方式：set path=%path%;C:\Program Files\Java\jdk\bin
特点：系统默认先去当前路径下找要执行的程序，如果没有，抛出不是内部或外部命令，也不是		可运行的程序错误。再去path中设置的路径下找。
classpath的配置:
    1）：永久配置方式：classpath=.;c:\;e:\
	2）：临时配置方式：set classpath=.;c:\;e:\

PS:1).path:由多个包含可执行指令文件的路径组成，路径之间用；间隔。
 	2).将路径存放至path，查找时会根据path环境变量设定的路径,自动由前往后依次查找。
 	3).找不到指令设置path       
4).找不到类设定classpath

PS2:在定义classpath环境变量时，需要注意的情况
如果没有定义环境变量classpath，java启动jvm后，会在当前目录下查找要运行的	类文件；
如果指定了classpath，那么会在指定的目录下查找要运行的类文件。
还会在当前目录找吗？两种情况：
	1）：如果classpath的值结尾处有分号，在具体路径中没有找到运行的类，会默认在当前目录再找一	次。
	2）：如果classpath的值结果出没有分号，在具体的路径中没有找到运行的类，不会再当前目录找。
	一般不指定分号，如果没有在指定目录下找到要运行的类文件，就报错，这样可以调试程序。

###七.DOS中JAVA命令 
1.DOS中的java命令的作用的有效范围在当前命令窗口中。
操作例:java  java-verbose   set		set path		set path=xxxxxx

2.javac命令和java命令:
	要知道java是分两部分的：一个是编译，一个是运行。
	javac：负责的是编译的部分，当执行javac时，会启动java的编译器程序。对指定扩展名的.java	文件进行编译。生成了jvm可以识别的字节码文件。也就是class文件，也就是java的运行程序。
	java：负责运行的部分.会启动jvm.加载运行时所需的类库,并对class文件进行执行.
	一个文件要被执行,必须要有一个执行的起始点,这个起始点就是main函数.

###八.JAVA开发的步骤
编写源程序文件 *.java
javac编译
java在DOS中运行  java [-options] class [args...]

###九.变量的生命周期与作用域
PS:变量的有效范围看他定义所在的括号内。

###十.常用操作
1.单行注释 ctrl+/
2.多行注释 ctrl+shift+/
3.代码补全 alt+/
4.代码导入 ctrl+shift+o 