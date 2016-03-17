---
layout : post
title: Java开发人员最常用19个Linux命令
categories : linux
duoshuo: true
---

不解释,题目代表一切

1.查找文件

	find / -name filename.txt

根据名称查找/目录下的filename.txt文件。

2.查看一个程序是否运行

	ps –ef|grep tomcat

查看所有有关tomcat的进程

3.终止线程

	kill -9 19979

终止线程号位19979的线程

4.查看文件，包含隐藏文件

	ls -al

5.当前工作目录

	pwd

6.复制文件包括其子文件到自定目录

	cp -r sourceFolder targetFolder

7.创建目录

	mkdir newfolder

8.删除目录（此目录是空目录）

	rmdir deleteEmptyFolder

9.删除文件包括其子文件

	rm -rf deleteFile

10.移动文件

	mv /temp/movefile /targetFolder

扩展重命名 mv oldNameFile newNameFile

11.切换用户

	su -username

12.修改文件权限

	chmod 777 file.java

//file.java的权限-rwxrwxrwx，r表示读、w表示写、x表示可执行

13.压缩文件

	tar -czf test.tar.gz /test1 /test2

14.列出压缩文件列表

	tar -tzf test.tar.gz

15.解压文件

	tar -xvzf test.tar.gz

16.查看文件头10行

	head -n 10 example.txt

17.查看文件尾10行

	tail -n 10 example.txt

18.查看日志文件

	tail -f exmaple.log

//这个命令会自动显示新增内容，屏幕只显示10行内容的（可设置）。

19.启动Vi编辑器

	vi

