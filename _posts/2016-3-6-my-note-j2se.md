---
layout: post
title:  "符海飞的课堂笔记--J2SE"
date:   2016-3-6
categories: 笔记 j2se
duoshuo: true
---


* content
{:toc}

# 第一部分:JAVA概述

## 一.开发语言
1.所有的开发语言都需要经过编译转化成机器指令执行。<br>
2.`低级语言`接近硬件，编译处理的过程减少，直接可以向硬件发出指令，执行速度快，编码困难，不容易掌握。<br>
&nbsp;&nbsp;&nbsp;`高级语言`在低级语言的基础上做了更进一步的封装提供了更简便的方法接口便于使用，执行的速度降低。


## 二.JAVA分类与内涵
1.JAVA有：J2SE,J2EE,J2ME<br>

`J2EE`(Java 2 Platform Enterprise Edition ) :<br>
开发企业环境下的应用程序，主要针对web程序开发；<br>
`J2SE`（Java 2 Platform Stand Edition） :<br>
完成桌面应用程序的开发，是其它两者的基础；<br>
`J2ME`(Java 2 Platform Micro Edition ) :<br>
开发电子消费产品和嵌入式设备，如手机中的程序；<br>

2.JAVA内涵(3点)<br>
	
>编程语言<br>
开发环境<br>
运行环境<br>

## 三.JAVA特点

>1.开源<br>
2.跨平台：在各个操作平台的操作系统上引入JVM(java虚拟机)来解决跨平台问题。<br>
`（JVM实行步骤：1.载入class文件 2. 验证 3. 解析翻译。）`<br>
3.面向对象<br>
4.简单<br>
5.安全性<br>
6.多线程<br>
7.兼顾解释性与编译性语言的特点 

## 四.JRE 
 释义:`Java Runtime Environment`:<br>
java程序的运行环境，java运行的所需的类库+JVM(java虚拟机)。

## 五.JDK目录结构  
1.释义:`Java Development Kit `:java的开发和运行环境，java的开发工具和jre。<br>
2.`bin目录`：存放可执行的指令文件。   例： java.exe  javac.exe

## 六.配置环境变量
1.目的:让java jdk\bin目录下的工具，可以在任意目录下运行<br>
2.原因是，将该工具所在目录告诉了系统，当使用该工具时，由系统帮我们去找指定的目录。

3.环境变量的配置：<br>
    1）：永久配置方式：`JAVA_HOME=%安装路径%\Java\jdk
	                  path=%JAVA_HOME%\bin`<br>
	2）：临时配置方式：`set path=%path%;C:\Program Files\Java\jdk\bin`<br>
特点：系统默认先去当前路径下找要执行的程序，如果没有，抛出不是内部或外部命令，也不是可运行的程序错误。再去path中设置的路径下找。<br>
classpath的配置:<br>
    1）：永久配置方式：`classpath=.;c:\;e:\`<br>
	2）：临时配置方式：`set classpath=.;c:\;e:\`

PS:<br>
1).path:由多个包含可执行指令文件的路径组成，路径之间用；间隔。<br>
 	2).将路径存放至path，查找时会根据path环境变量设定的路径,自动由前往后依次查找。<br>
 	3).找不到指令设置path<br>
4).找不到类设定classpath<br>

PS2:<br>
在定义classpath环境变量时，需要注意的情况<br>
如果没有定义环境变量classpath，java启动jvm后，会在当前目录下查找要运行的类文件；<br>
如果指定了classpath，那么会在指定的目录下查找要运行的类文件。<br>
还会在当前目录找吗？<br>两种情况：<br>
	1）：如果classpath的值结尾处有分号，在具体路径中没有找到运行的类，会默认在当前目录再找一次。<br>
	2）：如果classpath的值结果出没有分号，在具体的路径中没有找到运行的类，不会再当前目录找。<br>
	一般不指定分号，如果没有在指定目录下找到要运行的类文件，就报错，这样可以调试程序。<br>

## 七.DOS中JAVA命令 
1.DOS中的java命令的作用的有效范围在当前命令窗口中。
操作例:<br>`java`  `java-verbose`   `set`		`set path`		`set path=xxxxxx`

2.javac命令和java命令:<br>
	要知道java是分两部分的：一个是编译，一个是运行。<br>
	`javac`：负责的是编译的部分，当执行javac时，会启动java的编译器程序。对指定扩展名的.java文件进行编译。生成了jvm可以识别的字节码文件。也就是class文件，也就是java的运行程序。<br>
	`java`：负责运行的部分.会启动jvm.加载运行时所需的类库,并对class文件进行执行.<br>
	一个文件要被执行,必须要有一个执行的起始点,这个起始点就是main函数.<br>

## 八.JAVA开发的步骤

编写源程序文件 `*.java`<br>
javac编译<br>
java在DOS中运行  `java [-options] class [args...]`<br>

## 九.变量的生命周期与作用域
PS:变量的有效范围看他定义所在的括号内。

## 十.常用操作
1.单行注释 `ctrl+/`
2.多行注释 `ctrl+shift+/`
3.代码补全 `alt+/`
4.代码导入 `ctrl+shift+o`

---------------

# 第二部分:JAVA基础

## 一.基本语法
1.java是严格区分大小写的<br>  
2.java代码分为结构定义语句和功能执行语句<br>
`(功能执行语句的最后必须用分号结束)` 

## 二.标识符和关键字
1.java中的标识符 <br>
java中的包、类、方法、参数和变量的名字，可由任意顺序的`大小写字母`、`数字`、`下划线(_)`和`美元符号($)`组成，但标识符不能以数字开头，不能是关键字。<br>

2.java中的关键字
![1]({{"/images/NIITNOTE/1.png"| prepend: site.baseurl }}) 

PS：java 无`sizeof` ,`goto`, `const` 关键字，但不能作为变量名用

## 三.常量
1.整型常量(int)<br>
`十进制（12）` ，`十六进制（0x12）`，`八进制（012）`

2.长整型常量(long)<br>
`13L`

3.单精度浮点数 (float)(后面加f)<br>
例:`5.1f`，.`4f` ，`2e3f` ，`0f`

4.双精度浮点数(double) <br>
	例:`5.1`，`.4`，`2e-3`，`0d`

5.布尔常量(boolean) <br>
例:`true`和`false `

6.字符常量(char) (用单引号表示)<br>
例: `‘a’` ，`‘8’`<br>
`‘\r‘`表示接受键盘输入，相当于按下了回车键；<br>
`‘\n‘`是换行；<br>
`‘\t‘`是制表符，相当于table键；<br>
`‘\b‘`是退格键，相当于Back Space；<br>
`‘\‘‘`是单引号;<br>
`‘\“‘`是双引号；<br>
`‘\\‘`是一个斜杠“\”。<br>

7.字符串常量(String) (用双引号表示)<br>
	`“Hello World“`，`”123”`， `"Welcome \nXXX"`

8.null常量 <br>
	null常量只有一个值，用null表示，表示对象的引用为空

## 四.变量及数据类型
1.变量的概念与作用:<br>变量就是系统为程序分配的一块内存单元，用来存储各种类型的数据。根据所存储的数据类型的不同，有各种不同类型的变量。变量名代表这块内存中的数据 。
例:`int x=0,y`;	 `y=x+3`

2.变量大小及取值范围<br>
`byte`占用一个字节，数字大小为-27—27-1<br>
`short`占用两个字节，数字大小为-215—215-1 <br>
`int占`用四个字节，数字大小为-231—231-1 <br>
`long`占用八个字节，数字大小为-263—263-1 <br>
`float`占用四个字节，数字大小为1.4E-45~3.4E+38 , -1.4E-45~-3.4E+38 。用二进制的指数形式表示一个浮点数的格式，如：101*22  , 101*2-3<br>
`double`占用八个字节，数字大小为4.9E-324~1.7E+308, -4.9E-324~-1.7E+308 。<br>
`char`占两个字节，数字大小为0—216-1，是unicode编码。<br>
`Boolean`占一个字节，其取值只有两个，true和false。<br>

从小到大: `byte,char,short(这三个平级)-->int-->float-->long-->double`

3.基本数据类型<br>
![2]({{"/images/NIITNOTE/2.png"| prepend: site.baseurl }}) 

4.基本数据类型转化<br>
自动类型转换（也叫隐式类型转换） ` 自小向大 `<br>
强制类型转换（也叫显式类型转换） ` 自大向小 `<br>
例:<br>

	public static void testConvert() {
		byte b = 126;
		int i = b;	// byte->int 自动转换
		i = i + 1;
		b = (byte) i; // int ->byte  强制类型转换
		System.out.println(b);
	}

5.引用数据类型 :  `数组`、`类`、`接口`。

6.变量的生命周期<br>
只能在定义它的复合语句中(大括号中)使用

## 五.运算符
1.算术运算符<br>

![picture]({{"/images/NIITNOTE/3.png"| prepend: site.baseurl }}) 

PS:<br>
1).`“+”`除字符串相加功能外，还能把非字符串转换成字符串 ，<br>
例:`“x”+123;结果:“x123”` 。 <br>
2).如果对负数取模，可以把模数负号忽略不记，<br>
例：`5%-2=1`。
3).`++a`为先加后算,`a++`为先算后加;

	int x1 = 3,x2 = 3, y1 = 0,y2=0;
		y1 = (x1++) + (x1++) + (x1++);
		y2 = (++x2) + (++x2) + (++x2);
		System.out.println(x1+" "+y1);    //6 12
	System.out.println(x2+" "+y2);    //6 15

2.赋值运算符<br>
![picture]({{"/images/NIITNOTE/4.png"| prepend: site.baseurl }}) 

3.比较运算符<br>
![picture]({{"/images/NIITNOTE/5.png"| prepend: site.baseurl }}) 

4.逻辑运算符<br>
![picture]({{"/images/NIITNOTE/6.png"| prepend: site.baseurl }}) 

PS:<br> 1). `^` 表示异或,即两个相同为false,不同为true<br>
 2). `“&”`和`“&&”`的区别:<br>
`“&”`，那么无论任何情况，“&”两边的表达式都会参与计算。<br>
`“&&”`，当左边为false，则将不会计算其右边的表达式。<br>
 3).`“|”`和`“||”`的区别	同上。<br>

例:对两个变量的数据进行互换。不需要第三方变量。<br>

	int a  = 3,b = 5;-->b = 3,a = 5;
	a = a + b; a = 8;
	b = a - b; b = 3;
	a = a - b; a = 5;
	a = a ^ b;//
	b = a ^ b;//b = a ^ b ^ b = a
	a = a ^ b;//a = a ^ b ^ a = b;

5.运算符的优先级<br>
![picture]({{"/images/NIITNOTE/7.png"| prepend: site.baseurl }}) 

PS:<br>
1). `System.out.println(3<<2);`//3的二进制下左移两位。  //12<br>
2). `>>>`  (无符号右移)<br>
3). 我们可以使用括号改变运算赋的优先级<br>

例:	高效的算出 `2*8 = 2<<3`;

## 六.流程控制语句
>选择结构<br>
>循环结构<br>
>顺序结构<br>

1.选择结构<br>
1.1. `If语句`<br>
用法一:<br>

<pre><code>if (表达式)  语句；</code></pre>

用法二:<br>

<pre><code>if (表达式)  语句1； else  语句2；</code></pre>

用法三:<br>

	if (表达式1)  语句1；
	else if (表达式2) 语句2；
	else if (表达式2) 语句3；
		…
	 else  语句n;

用法四(嵌套用法):
	
	if (表达式1)  
		if (表达式2) 语句1；
		else语句2；
     esle  
		if (表达式2) 语句3；
		else语句4；

PS:每个语句可以是使用`{ }`组成的复合语句

1.2.三目运算符:`变量 ＝ 布尔表达式？语句1:语句2`；<br>
  (解释:布尔值为true时执行语句1,为false时执行语句2)<br>

  例://获取两个整数中的较大的整数。
  
		int a,b;
		int max = a>b?a:b;
		
   //获取三个整数中的较大的整数。
   
		int o,p,q;
		int temp = o>p?o:p;
		int max2 = temp>q?temp:q;

1.3. Switch语句

	int key = 3;
	switch (key) {      // key值可选类型:byte short int char
	case 1:
		System.out.println("case1");
		break;
	case 2:
		System.out.println("case2");
		break;
	case 3:
	case 4:
		System.out.println("case3,4");        //得到的结果是:case3,4
		break;
	default:
	System.out.println("default");
	break;
	}

工作原理：<br>
1).用小括号中的变量的值依次和case后面的值进行对比，和哪个case后面的值相同了就执行哪个case后面的语句，如果没有相同的则执行default后面的语句；<br>

>1).break是可以省略的，如果省略了就一直执行到遇到break为止；<br>
2).switch 后面的小括号中的变量是byte,char,short,int四种类型中的一种；<br>
3).default语句是可选的，它接受除上面接受值的其他值，通俗的讲，就是谁也不要的都归它。<br>
4).default可以写在switch结构中的任意位置；如果将default语句放在了第一行，则不管expression与case中的value是否匹配，程序会从default开始执	行直到第一个break出现。<br>
5).case后面可以跟多个语句，这些语句可以不用大括号括起来 。 <br>
6).一旦碰到第一次case匹配，就会开始顺序执行以后所有的程序代码，而不管后面的case条件是否匹配，后面case条件下的代码都会被执行，直到碰到break语句为止。我们可以利用这个特点来用同一段语句处理多个case条件 <br>

2.循环结构<br>

一)当循环次数明确的时候<br>
`for语句`<br>

二)当循环次数不明确的时候<br>
1)`while`先判断条件后执行<br>
2)`do...While`先执行后判断<br>

2.1. While语句    

	while (x < 3) {				//当表达式为true时执行
		System.out.println("x=" + x);
		x++;
	}

2.2. Do...while   
 
	do {
			System.out.println("ok2");
			y++;
	} while (y == 0);			//一直执行,直到表达式为true

2.3. for语句<br>
第一种:

	for(int i=0;i<x.length ;i++) {
	SYstem.out.println(i);
	}

第二种(增强for:适用于数组,集合):<br>
(增强for循环注意问题：在使用增强for循环时，不能对元素进行赋值)

	Animal[] animals=new Animal[];
	for(Animal animal:animals){
	SYstem.out.println(animal);
	}

特殊:
无限循环:

	for(;;){}

2.4.break关键字<br>
`break`：结束整个循环语句<br>
break语句可以中止循环中的子语句和switch语句。<br>
一个无标号的break语句会把控制传给当前(最内)循环(while，do．for或Switch)的下一条语句。如果有标号，控制会被传递给当前方法中的带有这一标号的语句。

	st:while(true)
	{
		 while(true)
		 {
		   break st;
		 }
	}

PS:当break语句单独存在时，下面不要定义其他语句，因为执行不到。

2.5.continue关键字<br>
`continue`:结束本次循环，执行下一次循环<br>
continue语句只能出现在循环语句(while,do，for)的子语句块中，无标号的continue语句的作用是跳过当前循环的剩余语句块，接着执行下一次循环。<br>
PS:如果continue单独存在时，下面不要有任何语句，因为执行不到。<br>

## 七.函数
1.函数的表达式<br>

	返回值类型 函数名（参数类型 形式参数1，参数类型 形式参数2，….）
	｛
	  程序代码
	  return 返回值；
	｝
	
>形式参数：在方法被调用时用于接收外部传入的数据的变量。<br>
参数类型：就是该形式参数的数据类型。<br>
返回值：方法在执行完毕后返还给调用它的程序的数据。<br>
返回值类型：函数要返回的结果的数据类型。<br>
实参：调用函数时实际传给函数形式参数的数据。<br>

PS:<br>1). 当函数没有具体的返回值时，返回的返回值类型用void关键字表示。<br>
2). 如果函数的返回值类型是void时，return语句可以省略不写的。<br>
3).return的作用：结束函数。结束功能。<br>

2.定义函数:
	函数其实就是一个功能，定义函数就是实现功能，通过两个明确来完成：<br>
	1). 明确该功能的运算完的结果，其实是在明确这个函数的返回值类型。<br>
	2). 在实现该功能的过程中是否有未知内容参与了运算，其实就是在明确这个函数的参数列表(参数类型&参数个数)。<br>
3.函数的作用：<br>
1). 用于定义功能。<br>
2). 用于封装代码提高代码的复用性。<br>
注意：函数中只能调用函数，不能定义函数。<br>

4.主函数：<br>
	1). 保证该类的独立运行。<br>
	2). 因为它是程序的入口。<br>
	3). 因为它在被jvm调用。<br>

## 八.函数的重载
1.应用形式 : java多态的一种应用<br>
`(多态：对同一个消息产生不同的结果反映出多种状态。)`<br>

	对于同一个消息：getArea
	得到不同的结果：根据参数的类型以及个数返回不同的结果
	getArea（矩形 ）{
	 return 矩形.x*矩形.y
	}
	getArea（圆形 ） {
		return 圆形.r*圆形.y*3.14
	}

## 九.内存的划分
1：`寄存器`。<br>2：`本地方法区`。<br>3：`方法区`。<br>4：`栈`。<br>5：`堆`。<br>

>栈：<br>存储的都是局部变量 ( 函数中定义的变量，函数上的参数，语句中的变量 )；<br>
	只要数据运算完成所在的区域结束，该数据就会被释放。<br>
堆：<br>用于存储数组和对象，也就是实体。啥是实体啊？就是用于封装多个数据的。<br>
1：每一个实体都有内存首地址值。<br>
2：堆内存中的变量都有默认初始化值。因为数据类型不同，值也不一样。 <br>
3：垃圾回收机制。<br>
对比:堆内存容量比栈内存大，但读写速度栈内存更快。<br>

## 十.数组
1.定义<br>
数组是一种存放（同一种类型）数据的容器。<br>
数组是一种引用(地址)数据类型，提供了相关的句柄可以引用或者操作容器中的数据。<br>
数组是不可变长的。<br>
实例化数组，是会根据数组类型对数组中的元素进行默认的初始化。<br>
			`(初始化值:  数字型：0;  应用数据类型：null)`<br>

2.一维数组<br>
	例:`Int[] a=new int[10]`;   `int a[]=new int[]{3,4,5}`;  `int[] a={3,4,5};`

3.二维数组<br>
	二维数组由多个一维数组组成<br>
	例:`int[][] b=new int[10][10]; `<br>

4.二分排序:

	public static int halfSeach_2(int[] arr,int key){
		int min,max,mid;
		min = 0;
		max = arr.length-1;
		mid = (max+min)>>1; //(max+min)/2;
		while(arr[mid]!=key){
			if(key>arr[mid]){
				min = mid + 1;
			}
			else if(key<arr[mid])
				max = mid - 1;
			if(max<min)
				return -1;
			mid = (max+min)>>1;	
		}
		return mid;
	}

5.冒泡排序

	public static void test1() {
		int[] ints = { 63, 4, 24, 1, 3, 13 };
		int temp = 0;
		for (int i = 1; i < ints.length; i++) {
			for (int j = 0; j < ints.length - i; j++) {
				if (ints[j] > ints[j + 1]) {
					temp = ints[j];
					ints[j] = ints[j + 1];
					ints[j + 1] = temp;
				}
			}
		}
		for (int a : ints) {
			System.out.println(a);
		}
	}
	
6.选择排序

	public static void test2() {
		int[] ints = { 10, 5, 11, 1, 3, 13 };
		int index = 0;
		int temp = 0;
		for (int i = 1; i < ints.length; i++) {
			index = 0;
			// 获取待排序数列中最大的数字
			for (int j = 0; j <= ints.length - i; j++) {
				if (ints[j] > ints[index]) {
					index = j;
				}
			}
			// 将最大数字与ints.length-i位置上的数字进行交换
			temp = ints[ints.length - i];
			ints[ints.length - i] = ints[index];
			ints[index] = temp;
		}
		for (int a : ints) {
			System.out.println(a);
		}
	}

	public static void getMax() {
		int[] ints = { 4, 63, 24, 1, 3, 13 };
		int index = 0;
		for (int i = 1; i < ints.length; i++) {
			if (ints[i] > ints[index]) {
				index = i;
			}
		}
		System.out.println(ints[index]);
	}
	
7.插入排序

	public static void sum(){
		int[] ints = { 4, 63, 24, 1, 3, 13 };
		int j;
		int temp=0;
		for(int i=1;i<ints.length;i++){
			temp=ints[i];
			for(j=i-1;j>=0&&ints[j]>temp;j--){
				ints[j+1]=ints[j];
			}
				ints[j+1]=temp;
		}
		for(int i=0;i<ints.length;i++){
			System.out.println(ints[i]);
		}
	}

8.数组排序  Arrays.sort();

	int[] ints={3,5,2,7,1,10};
		Arrays.sort(ints);
		for(int a:ints){
			System.out.print(a+" ");   //1 2 3 5 7 10 
		}	

9.数组复制  arraycopy();

	int[] ints1={1,2,3,5};
		int[] ints2=new int[4];
		System.arraycopy(ints1, 0, ints2, 1, 2);  
	for (int i : ints2) {
			System.out.print(ints2[i]);   //0 1 2 0
		}

## 十一.Main函数<br>
`Public`：访问权限最大。<br>
`static`：不需要对象，直接类名即可。<br>
`void`：主函数没有返回值。<br>
`Main`：主函数特定的名称。<br>
`(String[] args)`：主函数的参数，是一个字符串数组类型的参数，jvm调用main方法时，传递的实际参数是 new String[0]。<br>

jvm默认传递的是长度为0的字符串数组，我们在运行该类时，也可以指定具体的参数进行传递。可以在控制台，运行该类时，在后面加入参数。参数之间通过空格隔开。jvm会自动将这些字符串参数作为args数组中的元素，进行存储。


---------------

# 第三部分:面向对象

## 一.面向对象的理解

1.面向对象与面向过程的区分

>1.1.面向对象								|  1.2.面向过程
例:`Window w=new Window();	w.move();`		|  例:`Move Window（Window w）;`
主谓结构									|  动宾结构
强调（主体）和（动作），					|  强调是过程和步骤;

2.方法:

>世界中的物体-->class;<br>
物体的特征-->类的属性;<br>
动作行为-->类的方法;<br>
过程-->函数；<br>
对象-->函数的封装;

3.软件建模（建立模型）

用软件来描述现实世界中的问题，一个抽象的过程。

## 二.面向对象的实例理解

>面向过程	|	面向对象
问题		|	问题
1 step1		|	主体1.动作
2 step2		|	主体2.动作
3 step3		|	主体3.动作

例:大象放入冰箱问题

>面向过程:	|	面向对象:
打开冰箱	|	冰箱.开门	
放入大象	|	冰箱.存储
关闭冰箱	|	冰箱.关门

PS:面向对象更符合人的思维方式。

## 三.面向对象的三大特征

`封装` `继承` `多态`  

## 四.类与对象

1.定义

类是对某一类事物的描述，其实类就是将对象共性的内容进行抽取。<br>
对象是实际存在的该类事物的每个个体，因而也称实例(`instance`)。<br> 
面向对象程序设计的重点是类的设计，而不是对象的设计。<br>

	如果将对象比作汽车，那么类就是汽车的设计图纸。

2.类的格式

	class Person{
			int age;
			void shout()
			{
			System.out.println(“oh,my god! I am “ + age);
			}
	}
	
`age`是类的属性 ，也叫类成员变量 。<br>
`shout`是方法也叫类的成员函数。<br>
`shout`方法可以直接访问同一个类中的`age`变量 ，如果一个方法中有与成员变量同名的局部变量，该方法中对这个变量名的访问是局部变量，而不再是成员变量。<br>  

3.对象产生的过程

`Person p1 = new Person();` 两层含义(实例化,初始化)<br>
实例对象创建后，会对其成员变量进行默认的初始化。<br>

![picture]({{"/images/NIITNOTE/8.png"| prepend: site.baseurl }}) 

4.对象的使用

创建新的对象之后,我们就可以使用`对象名.对象成员`的格式，来访问对象的成员（包括属性和方法） 

	class TestPerson{
			public static void main(String[] args)
			{
	    		Person p1 = new Person();
			Person p2 =new Person();
			p1.age = -30;
			p1.shout();
			p2.shout();
			}
	}

5.对象的生命周期

	对象的生命周期取决于其是否还有引用变量引用它。

6.匿名对象

定义:不定义对象的句柄，而直接调用这个对象的方法,这样的对象叫做匿名对象。<br>
用法:如果对一个对象只需要进行一次方法调用，那么就可以使用匿名对象。

	new Person().shout();
	
PS:我们经常将匿名对象作为实参传递给一个函数调用。

## 五.类的封装

1.将类内部实现的一些细节进行 【隐藏(`private`）】，【提供统一的接口】给外界使用，提供程序的安全性。

2.实现类的封装性 <br>
2.1.为了实现良好的封装性，我们通常将类的成员变量声明为`private`，再通过`public`的方法来对这个变量进行访问。<br>
2.2.对一个变量的操作，一般都有读取和赋值操作，我们分别定义两个方法来实现这两种操作，一个是`getXxx()`用来读取这个成员变量操作，另外一个是`setXxx()`用来对这个成员变量赋值。

	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	
2.3.模块设计追求`强内聚`（许多功能尽量在类的内部独立完成，不让外面干预），`弱耦合`（提供给外部尽量少的方法调用）。

3.优点

>隐藏类的实现细节；<br>
让使用者只能通过事先定制好的方法来访问数据，可以方便地加入控制逻辑，限制对属性的不合理操作；<br>
便于修改，增强代码的可维护性；<br>

4.总结：

开发时，记住，属性是用于存储数据的，直接被访问，容易出现安全隐患，所以，类中的属性通常被私有化，并对外提供公共的访问方法。

## 六.成员变量和局部变量的区别：

>1： 成员变量直接定义在类中。<br>
    局部变量定义在方法中，参数上，语句中。<br>
2： 成员变量在这个类中有效。<br>
	局部变量只在自己所属的大括号内有效，大括号结束，局部变量失去作用域。<br>
3： 成员变量存在于堆内存中，随着对象的产生而存在，消失而消失。<br>
	局部变量存在于栈内存中，随着所属区域的运行而存在，结束而释放。<br>

## 七.构造函数

1.构造方法的特征

它具有与类相同的名称；<br>
它不含返回值；

PS：在构造方法里不含返回值的概念是不同于`void`的，在定义构造方法时加了`void`，结果这个方法就不再被自动调用了

2.构造方法的作用

>当一个类的实例对象刚产生时，这个类的构造方法就会被自动调用，我们可以在这个方法中加入要完成初始化工作的代码。

3.构造方法的重载

和一般的方法重载一样，重载的构造方法具有不同个数或不同类型的参数，编译器就可以根据这一点判断出用`new` 关键字产生对象时，该调用哪个构造方法了。产生对象的格式是：`new 类名(参数列表)；`

4.构造函数部分细节

4.1.在java每个类里都至少有一个构造方法，如果程序员没有在一个类里定义构造方法，系统会自动为这个类产生一个默认的构造方法，这个默认构造方法没有参数，在其方法体中也没有任何代码，即什么也不做。<br>

>PS:当自定义构造函数后,默认无参构造函数就不再提供了,需要用,需要写出来;<br>

4.2.声明构造方法，如无特殊需要，应使用`public`关键字,不能使用`private`,`private`修饰后,外界就不可以调用了

5.当子父类中出现成员函数一模一样的情况，会运行子类的函数。

这种现象，称为覆盖操作。这时函数在子父类中的特性。

6.函数两个特性：

>1.重载。同一个类中。`overload`<br>
2.覆盖。子类中。覆盖也称为重写，覆写。`override`
	
7.覆盖注意事项：

>1.子类方法覆盖父类方法时，子类权限必须要大于等于父类的权限。 <br>
2.静态只能覆盖静态，或被静态覆盖。

## 八.This的使用

>1.引用变量指向当前实例对象 `this.xxx;`<br>
2.调用当前类中的其他构造函数 `this.(xxx,xxxx);`

3.this引用句柄的应用

3.1.一个类中的成员方法可以直接调用同类中的其他成员;<br>
3.2.让类的成员变量名和对其进行赋值的成员方法的形参变量同名是必要的。<br> 
3.3.构造方法是在产生对象时被java系统自动调用的，我们不能在程序中象调用其他方法一样去调用构造方法。但我们可以在一个构造方法里调用其他重载的构造方法，不是用构造方法名，而是用`this(参数列表)`的形式，根据其中的参数列表，选择相应的构造方法。 

4.当成员变量和局部变量重名，可以用关键字`this`来区分。

注意：用`this`调用构造函数，必须定义在构造函数的第一行。因为构造函数是用于初始化的，所以初始化动作一定要执行。否则编译失败。

## 九.垃圾回收  

1.finalize() 和 System.gc

>1.1. `finalize()`:当垃圾回收器确定不存在对该对象的更多引用时，由对象的垃圾回收器调用此方法。子类重写 `finalize` 方法，以配置系统资源或执行其他清除。 
1.2. `System.gc`:运行垃圾回收器。 调用 `gc` 方法暗示着 Java 虚拟机做了一些努力来回收未用对象，以便能够快速地重用这些对象当前占用的内存。当控制权从方法调用中返回时，虚拟机已经尽最大努力从所有丢弃的对象中回收了空间。 

	Person p1=new Person("tom",30);
	Person p2=new Person("jack",30);
	Person p3=new Person("marry",30);
	p2=p3=null;
	//向jvm发出指令，当jvm执行回收是，会首先调用被回收对象的finalize()方法
	System.gc();

## 十.函数的参数传递

>1.基本数据类型的参数传递==数据的复制<br>
2.引用数据类型的参数传递==传递地址

## 十一.Stasic 关键字

1.static的特点：

>1).`static`是一个修饰符，用于修饰成员。<br>
2).`static`修饰的成员被所有的对象所共享。<br>
3).`static`优先于对象存在，因为`static`的成员随着类的加载就已经存在了。<br> 
4).`static`修饰的成员多了一种调用方式，就可以直接被类名所调用 。 `类名.静态成员` 。<br>
5).`static`修饰的数据是共享数据，对象中的存储的是特有数据。<br>

2.1.可以修饰变量(`静态变量`) //类的变量 <br>
	(如果没有`static`修饰,它是实例的变量,所有类的实例对象共享同一份资源)

	static int a;

2.2.可以修饰方法(`静态方法`) //调用为: 类名.方法名; <br>
(如果没有`static`修饰,它是实例的方法)<br>
//在静态方法中必须访问静态资源

	public static void mehtodA(){};

2.3.可以修饰语句块(`静态语句块`)
	(在类第一次加载的时候被执行,且只执行一次)

	static { System.out.println(“this is static”);}

2.4.可以修饰内部类(`静态内部类`)

3.被`static`修饰的资源不需要实例对象就可以使用;

4.静态使用的注意事项：

>1).静态方法只能访问静态成员。(非静态既可以访问静态，又可以访问非静态)<br>
2).静态方法中不可以使用`this`或者`super`关键字。<br>
3).主函数是静态的。

5.静态用的时机

5.1.成员变量。（数据共享时静态化）

>该成员变量的数据是否是所有对象都一样：<br>
如果是，那么该变量需要被静态修饰，因为是共享的数据。<br> 
如果不是，那么就说这是对象的特有数据，要存储到对象中。 

5.2.成员函数。（方法中没有调用特有数据时就定义成静态）

>如果判断成员函数是否需要被静态修饰呢？<br>
只要参考，该函数内是否访问了对象中的特有数据：<br>
如果有访问特有数据，那方法不能被静态修饰。<br>
如果没有访问过特有数据，那么这个方法需要被静态修饰。

6.成员变量和静态变量的区别：

>1). 成员变量所属于对象。所以也称为实例变量。<br>
	静态变量所属于类。所以也称为类变量。<br>
2). 成员变量存在于堆内存中。<br>
	静态变量存在于方法区中。<br>
3). 成员变量随着对象创建而存在。随着对象被回收而消失。<br>
	静态变量随着类的加载而存在。随着类的消失而消失。<br>
4). 成员变量只能被对象所调用 。<br>
	静态变量可以被对象调用，也可以被类名调用。<br>
	
	总结:成员变量可以称为对象的特有数据，静态变量称为对象的共享数据。

静态代码块、构造代码块、构造函数同时存在时的执行顺序：`静态代码块  构造代码块  构造函数`

## 十二.单例设计模式

1.设计模式：解决问题最行之有效的思想。是一套被反复使用、多数人知晓的、经过分类编目的、代码设计经验的总结。使用设计模式是为了可重用代码、让代码更容易被他人理解、保证代码可靠性。java中有`23`种设计模式;

2.解决的问题：保证一个类在内存中的对象唯一性。<br>
比如：多程序读取一个配置文件时，建议配置文件封装成对象。会方便操作其中数据，又要保证多个程序读到的是同一个配置文件对象，就需要该配置文件对象在内存中是唯一的。

3.模式要求:

>1).构造函数使用private修饰;<br>
2).实例的创建在类的内部创建;<br>
3).类的内部提供接口方法,将实例对象返回给外部;

4.步骤：

>1).因为创建对象都需要构造函数初始化，只要将本类中的构造函数私有化，其他程序就无法再创建该类对象；<br>
2).就在类中创建一个本类的对象；<br>
3).定义一个方法，返回该对象，让其他程序可以通过方法就得到本类对象。（作用：可控）

5.代码体现：

>1).私有化构造函数；<br>
2).创建私有并静态的本类对象；<br>
3).定义公有并静态的方法，返回该对象。

6.1.懒汉模式: (`当用户需求时创建`)

	//内部提供接口方法将实例对象返回给外部
	public static synchronized PersonSingleton getPersonInstance2(){
	if(person2==null){
			person2=new PersonSingleton();
		}	
		return person2;
	}

6.2.饿汉(饥汉)模式:(`不管用户用不用,类创建之初就创建了`)

	//定义实例对象的引用变量
	private static PersonSingleton person1=new PersonSingleton();;
	//当第一次获取实例的时候才创建该实例对象
	private static PersonSingleton person2;

## 十三.类的继承

>1.语法` A extends B`  ;`A类`继承`B类`,`A类`是子类,`B类`是父类;<br>
2.通过继承可以简化类的定义 ;<br>
3.java只支持`单继承`，不允许多重继承;<br>
4.可以有多层继承，即一个类可以继承某一个类的子类;<br>
5.在所有类的层次结构中`Object`是所有类的基类;<br>
6.子类不能继承父类的`private`方法;<br>
7.在产生子类的实例对象时，系统默认调用父类无参数的构造方法,总之都会调用父类的构造函数;<br>
9.一个类没有声明构造函数的时候，编译器会自动添加一个不带参数的构造函数；一旦声明了任意一个构造函数则就不添加了。 <br>
10.`A is a B`;(创建子类时,这么读法读通,可以创建子类) <br>
11.对于一个继承体系的使用，查阅顶层父类中的内容，创建最底层子类的对象。<br>
12.当子父类中出现一样的属性时，子类类型的对象，调用该属性，值是子类的属性值。<br>
13.子父类中通常是不会出现同名成员变量的，因为父类中只要定义了，子类就不用在定义了，直接继承过来用就可以了。<br>
14.什么时候使用覆盖呢:当一个类的功能内容需要修改时，可以通过覆盖来实现。<br>
15.子类中所有的构造函数都会默认访问父类中的空参数的构造函数，因为每一个子类构造内第一行都有默认的语句`super();` <br>
16.如果子类构造函数中用`this`来指定调用子类自己的构造函数，那么被调用的构造函数也一样会访问父类中的构造函数。

## 十四.Super的使用

>1.引用变量指向当前实例父类对象 `super();`<br>
2.调用父类中的构造函数 `super(xxx,xxxx);`

## 十五.函数的覆写(`@Override`)

>1.在子类和父类之间<br>
2.相同的方法名称<br>
3.相同的参数列表<br>
4.相同的返回值类型<br>
5.不能使用比父类中被覆盖的方法更加严格的访问权限  访问权限>=父类的访问权限

## 十六.子类对象的实例化过程

>1.在构造函数中默认都会调用父类的无参构造函数`super();`<br>
除非明确指定了调用父类那个构造函数`super(xxx,xxx);`<br>
2.子类->父类->父类->父类......Object<br>
3.`Super()`和`this()`在同一个函数中不能同时出现,并且只能在第一条语句;

4.流程图

![picture]({{"/images/NIITNOTE/9.png"| prepend: site.baseurl }}) 

## 十七.Final 关键字

>1.`final`标记的类不能被继承。<br>
2.`final`标记的方法不能被子类重写。<br>
3.`final`标记的变量(成员变量或局部变量)即成为常量，只能赋值一次。<br>
4.方法中定义的内部类只能访问该方法内的`final`类型的局部变量。 <br>
5.`public static final`共同标记常量时，这个常量就成了全局的常量。

## 十八.抽象类 (`Abstract`)

>1.定义:一些不含方法体的方法，它的方法体的实现交给该类的子类根据自己的情况去实现，这样的方法就是抽象方法，包含抽象方法的类就叫抽象类。<br>
2.抽象方法:父类不实现.交给子类去实现;<br>
3.抽象类必须用`abstract`关键字来修饰；抽象方法也必须用`abstract`来修饰。<br>
3.1.抽象类: `public abstract class 类名{}`<br>
3.2.抽象方法:`public abstract void 方法名();`<br>
4.因为抽象类中包涵没有实现的抽象方法,抽象类不能被实例化，也就是不能用`new`关键字去产生对象。<br>
5.抽象方法只需声明，而不需实现。<br>
6.含有抽象方法的类必须被声明为抽象类，抽象类的子类必须覆盖所有的抽象方法后才能被实例化，否则这个子类还是个抽象类。 <br>
7.子类继承抽象类父类,不一定必须实现父类的抽象方法,没有实现父类抽象方法的子类还是抽象类;<br>
8.`abstract`和`final` ,	`private` , `static` 不可以共存<br>
9.抽象类可以定义非抽象方法:<br>
抽象类和一般类没有太大的区别，都是在描述事物，只不过抽象类在描述事物时，有些功能不具体。所以抽象类和一般类在定义上，都是需要定义属性和行为的。只不过，比一般类多了一个抽象函数。而且比一般类少了一个创建对象的部分。<br>
10.抽象类中可以不定义抽象方法!抽象方法目的仅仅为了不让该类创建对象。<br>
11.相关设计模式:抽象模板设计模式:(父类提供给子类一个行为的模板,规范子类的行为;具体实施交给子类完成)
	
	父母让子女学习,具体学习要子女完成

	abstract class GetTime{
		public final void getTime(){ //此功能如果不需要复写，可加final限定
			long start = System.currentTimeMillis();
			code(); //不确定的功能部分，提取出来，通过抽象方法实现
			long end = System.currentTimeMillis();
			System.out.println("毫秒是："+(end-start));
		}
		public abstract void code(); //抽象不确定的功能，让子类复写实现
	}
	class SubDemo extends GetTime{
		public void code(){ //子类复写功能方法
			for(int y=0; y<1000; y++){
				System.out.println("y");
			}
		}
	}

## 十九.接口(Interface) 

1.定义:接口是抽象方法和常量值的定义的集合，从本质上讲，接口是一种特殊的抽象类，这种抽象类中只包含常量和方法的定义，而没有变量和方法的实现。

2.接口是个抽象类,所以不能被实例化 <br>
	接口的子类必须实现了接口中所有的抽象方法后，该子类才可以实例化。否则，该子类还是一个抽象类。

3.接口中的成员都有固定的修饰符。<br>
	成员变量：`public static final` <br>
	成员方法：`public abstract `
	
	interface Inter{
	public static final int x = 3;
	public abstract void show();
	}

4.我们可以定义一个新的接口用`extends`关键字去继承一个已有的接口 ,一个接口可以继承多个接口;

5.我们也可以定义一个类用`implements`关键字去实现一个接口中的所有方法，我们还可以去定义一个抽象类用`implements`关键字去实现一个接口中的部分方法。 

6.一个类可以继承一个父类的同时，实现一个或多个接口，`extends`关键字必须位于`implemnets`关键字之前 。

7.接口都用于设计上，设计上的特点：（可以理解主板上提供的接口）<br>

>1：接口是对外提供的规则。<br>
2：接口是功能的扩展。<br>
3：接口的出现降低了耦合性。

	视图层代码(view)->业务逻辑层代码(service)->数据访问层代码(dao).面向接口编程;

8.定义接口类型的应用变量     

	Main函数中{    
		接口  变量=new 实现接口的类();
		new 方法的类().方法(接口的变量);
	}
	
	Public void 方法名 (接口  变量){
		接口的变量.接口中方法();
	}

9.接口不管你是什么,只管你想干什么!

10.抽象类和接口的区别：

>1). 抽象类只能被继承，而且只能单继承。<br>
	接口需要被实现，而且可以多实现。 <br>
2). 抽象类中可以定义非抽象方法，子类可以直接继承使用。<br>
	接口中都有抽象方法，需要子类去实现。<br>
3). 抽象类使用的是  `is a 关系`。<br>
	接口使用的 `like a 关系`。 <br>
4). 抽象类的成员修饰符可以自定义。<br>
	接口中的成员修饰符是固定的。全都是`public`的。<br>

## 二十.对象的类型转换

>(变量的类型转换  `大->小(强制)`   `小->大(自动))`<br>
1.产生在子类与父类之间<br>
2.子类(大)->父类(小) (自动)    父类(小)->子类(大)  (强制)<br>
3.子类->父类,无static时,方法是调用的子类的,成员变量是调用的父类的<br>
4.Instanceof 关键字  <br>
	判断对象是否实现了指定的接口或继承了指定的类<br>
格式：`<对象 instanceof 类型>` ，判断一个对象是否所属于指定的类型。<br>

	Student instanceof Person = true;//student继承了person类

父类转子类时,用`Instanceif`判断  
 
	if(父类实例化 Instanceof 子类){
		子类 子类实例化=(子类)父类实例化;
		子类实例化.方法();
	}

## 二十一.类的多态

多态的好处：提高了程序的扩展性。<br>
多态的弊端：当父类引用指向子类对象时，虽然提高了扩展性，但是只能访问父类中具备的方法，不可以访问子类中特有的方法。(前期不能使用后期产生的功能，即访问的局限性)<br>
多态的前提：<br>
	1：必须要有关系，比如继承、或者实现。<br>
	2：通常会有覆盖操作。

多态的出现思想上也做着变化：以前是创建对象并指挥对象做事情。有了多态以后，我们可以找到对象的共性类型，直接操作共性类型做事情即可，这样可以指挥一批对象做事情，即通过操作父类或接口实现。


	class 毕姥爷{
		void 讲课(){
			System.out.println("企业管理");
		}
		void 钓鱼(){
			System.out.println("钓鱼");
		}
	}
	class 毕老师 extends 毕姥爷{
		void 讲课(){
			System.out.println("JAVA");
		}
		void 看电影(){
			System.out.println("看电影");
		}
	}
	class {
		public static void main(String[] args) {
			毕姥爷 x = new 毕老师(); //毕老师对象被提升为了毕姥爷类型。 
		//		x.讲课();
		//		x.看电影();  //错误.
			毕老师 y = (毕老师)x; //将毕姥爷类型强制转换成毕老师类型。 
			y.看电影();//在多态中，自始自终都是子类对象在做着类型的变化。
		}
	}

多态在子父类中的成员上的体现的特点：

>1，成员变量：在多态中，子父类成员变量同名。<br>
	在编译时期：参考的是引用型变量所属的类中是否有调用的成员。（编译时不产生对象，只检查语法错误）<br>
	运行时期：也是参考引用型变量所属的类中是否有调用的成员。<br>
	简单一句话：无论编译和运行，成员变量参考的都是引用变量所属的类中的成员变量。<br>
	再说的更容易记忆一些：成员变量 --- 编译运行都看 = 左边。<br><br>
2，成员函数。<br>
	编译时期：参考引用型变量所属的类中是否有调用的方法。<br>
	运行事情：参考的是对象所属的类中是否有调用的方法。<br>
	为什么是这样的呢？因为在子父类中，对于一模一样的成员函数，有一个特性：覆盖。<br>
	简单一句：成员函数，编译看引用型变量所属的类，运行看对象所属的类。<br>
	更简单：成员函数 --- 编译看 = 左边，运行看 = 右边。<br><br>
3，静态函数。 <br>
	编译时期：参考的是引用型变量所属的类中是否有调用的成员。<br>
	运行时期：也是参考引用型变量所属的类中是否有调用的成员。<br>
	为什么是这样的呢？因为静态方法，其实不所属于对象，而是所属于该方法所在的类。<br>
	调用静态的方法引用是哪个类的引用调用的就是哪个类中的静态方法。<br>
	简单说：静态函数 --- 编译运行都看 = 左边。

## 二十二.异常(`Exception`)

1.所有异常的父类都是`Exception`<br>
2.异常的分类:<br>
2.1. 运行时异常(`checked异常`)(`RuntimeException`),在程序运行时产生异常,不可控 ;<br>
			例:  `IndexOutOfBoundsException` , `ArithmeticException`<br>
2.2. 非运行时异常(`非checked`异常):编译时会提示异常信息,需要处理,否则编译不通过;<br>
3.处理异常的方法<br>
3.1. Try ...catch()语句 

	try {
		需要被检测的代码；
	}
	catch(异常类 变量名){
		异常处理代码；
	}
	fianlly{
		一定会执行的代码；
	}

	catch (Exception e) { //e用于接收try检测到的异常对象。
		System.out.println("message:"+e.getMessage());//获取的是异常的信息。
		System.out.println("toString:"+e.toString());//获取的是异常的名字+异常的信息。
		e.printStackTrace();//打印异常在堆栈中信息；异常名称+异常信息+异常的位置。
	}
	
PS:`try`中异常抛出后,原先后面的代码就不执行,程序转到`catch`语句块执行;<br>
		`finally`中不管`try`中是否有异常,`finally`中的代码都会被执行;  
		
3.2. throws关键字 

	通过throws语句 将异常向上抛出,不在函数内部处理;
	
3.3. 自定义异常与throw关键字 

	编写一个继承exception的java类(非运行时异常);
	编写一个继承RuntimeException的java类(运行时异常);
	
3.4.throw 和throws关键字的区别：

`throw`用于抛出异常对象，后面跟的是异常对象；`throw`用在函数内。
`throws`用于抛出异常类，后面跟的异常类名，可以跟多个，用逗号隔开。`throws`用在函数上。

3.5.异常处理原则：功能抛出几个异常，功能调用如果进行`try`处理，需要与之对应的`catch`处理代码块，这样的处理有针对性，抛几个就处理几个。

4.1.特殊情况：`try`对应多个`catch`时，如果有父类的`catch`语句块，一定要放在下面。

4.2.异常的转换思想：当出现的异常是调用者处理不了的，就需要将此异常转换为一个调用者可以处理的异常抛出。

4.3.记住：`finally`很有用，主要用户关闭资源。无论是否发生异常，资源都必须进行关闭。

	System.exit(0); //退出jvm，只有这种情况finally不执行。

5.在子父类进行覆盖时，当异常出现后，有了一些新的特点：

>1).当子类覆盖父类的方法时，如果父类的方法抛出了异常，那么子类的方法要么不抛出异常要么抛出父类异常或者该异常的子类，不能抛出其他异常。<br>
2).如果父类抛出了多个异常，那么子类在覆盖时只能抛出父类的异常的子集。<br>
3).如果父类或者接口中的方法没有抛出过异常，那么子类是不可以抛出异常的，如果子类的覆盖的方法中出现了异常，只能`try`不能`throws`。<br>
4).如果这个异常子类无法处理，已经影响了子类方法的具体运算，这时可以在子类方法中，通过`throw`抛出RuntimeException异常或者其子类，这样，子类的方法上是不需要`throws`声明的。

6.常见异常汇总:

	6.1. java.lang.NullPointerException	 空指针异常
	6.3. java.lang.RuntimeException     运行时异常
	6.4. java.lang.IndexOutOfBoundsException    数组,排序越界
	6.5. java.lang.ArithmeticException  	   数学运算异常;如，整数“除以零”; 
	6.6. java.lang.CloneNotSupportedException   无法实现 Cloneable 接口异常
	6.7. Java.lang.ClassNotFoundException       指定的类不存在
	6.8. java.lang.ArrayIndexOutOfBoundsException   数组下标越界
	6.9. java.lang.ClassCastException        类型强制转换异常
	6.10. java.lang.NegativeArrayException   数组负下标异常
	6.11. java.lang.SecturityException        违背安全原则异常
	6.12. java.lang.NumberFormatException   字符串转换为数字异常
	6.13. java.lang.IOException     输入输出异常
	6.14. java.lang.NoSuchMethodException     方法未找到异常
	6.15. java.lang.ExceptionInInitializerError    初始化程序错误
	6.16. java.lang.NoClassDefFoundError       未找到类定义错误
	6.17. java.lang.StackOverflowError          堆栈溢出错误
	6.18. java.lang.CloneNotSupportedException  不支持克隆异常
	6.19. java.lang.TypeNotPresentException     类型不存在异常
	6.20. java.lang.InterruptedException		清除原先的中断标记恢复成默认false

## 二十三.包(Package)

1.import进行调用

导入指定包中的类。记住：实际开发时,到的哪个类就导入哪个类，不建议使用`*`.

	import packa.*;//这个仅仅是导入了packa当前目录下的所有的类。不包含子包。
	import packa.abc.*;//导入了packa包中的子包abc下的当前的所有类。

如果导入的两个包中存在着相同名称的类。这时如果用到该类，必须在代码中指定包名。

2.JDK中常用的包

	2,1. java.lang----包含一些Java语言的核心类，如String、Math、Integer、System和Thread，提供常用功能。
	2.2. java.awt----包含了构成抽象窗口工具集（abstract window toolkits）的多个类，这些类被用来构建和管理应用程序的图形用户界面(GUI)。
	2.3. java.applet----包含applet运行所需的一些类。
	2.4. java.net----包含执行与网络相关的操作的类。
	2.5. java.io----包含能提供多种输入/输出功能的类。
	2.6. java.util----包含一些实用工具类，如定义系统特性、使用与日期日历相关的函数。

## 二十四.访问修饰符

1.`private` ,  `default`  ,  `protected`  , `public`    (第三行的子类指其他包中的子类)


## 二十五.JAVA的命名习惯 

>1.包名中的字母一律小写,如：`xxxyyyzzz`。<br>
2.类名、接口名应当使用名词，每个单词的首字母大写，如：`XxxYyyZzz`。<br>
3.方法名，第一个单词小写，后面每个单词的首字母大写，如：`xxxYyyZzz`。<br>
4.变量名，第一个单词小写，后面每个单词的首字母大写,如：`xxxYyyZzz`。<br>
5.常量名中的每个字母一律大写，如：`XXXYYYZZZ`。

## 二十六.Object类

1.所有类的直接或者间接父类，Java认为所有的对象都具备一些基本的共性内容，这些内容可以不断的向上抽取，最终就抽取到了一个最顶层的类中的，该类中定义的就是所有对象都具备的功能。

2.具体方法：

1).boolean equals(Object obj)：用于比较两个对象是否相等，其实内部比较的就是两个对象地址。<br>
而根据对象的属性不同，判断对象是否相同的具体内容也不一样。所以在定义类时，一般都会复写equals方法，建立本类特有的判断对象是否相同的依据。

	public boolean equals(Object obj){
		if(!(obj instanceof Person))
			return false;
		Person p = (Person)obj;
		return this.age == p.age;
	}
	
2，String toString()：将对象变成字符串；默认返回的格式：`类名@哈希值 = getClass().getName() + '@' + Integer.toHexString(hashCode())`

	为了对象对应的字符串内容有意义，可以通过复写，建立该类对象自己特有的字符串表现形式。 

	public String toString(){
		return "person : "+age;
	}

3，`Class getClass()`：获取任意对象运行时的所属字节码文件对象。

4，`int hashCode()：`返回该对象的哈希码值。支持此方法是为了提高哈希表的性能。

通常equals，toString，hashCode，在应用中都会被复写，建立具体对象的特有的内容。

## 二十七.ToString方法

1.toString()方法就是把对象转换成String类型;

	public class A{ 
		public String toString(){
				return "this is A";
		} 
	} 
	
如果某个方法里面有如下句子： 

	A obj=new A(); 
	System.out.println(obj); 
	会得到输出:this is A 
	
	long a=123;   
	Long aa=new Long(a);//使用包装类   
	String ii=aa.toString();//使用aa对象的toString（）方法   
	System.out.println(ii);//输出转换的结果
	//object中的toString方法是对象才能调用的
	输出结果：123
	
PS：`toString()` 只适用于对象的调用，普通的数据类型不可以调用，这也就是使用包装类的原因。

## 二十八.对象的复制 Clone()

1.浅复制：对象的基本数据类型都复制一份，引用数据类型还是指向原先的实例对象。

	class CloneClass implements Cloneable {
		public int aInt;
		// 重写clone方法
		public Object clone() {
			CloneClass o = null;
			try {
				o = (CloneClass) super.clone();
			} catch (CloneNotSupportedException e) {
				e.printStackTrace();
			}
			return o;
		}
	}
	
2.深复制：对象的基本数据类型都复制一份，引用数据类型指向新创建的实例对象上。

	public class A implements Cloneable {
		public String a[];
		public A() {
			a = new String[2];
		}
		public Object clone() {
			A o = null;
			try {
				o = (A) super.clone();
				o.a = (String[]) a.clone();// 属性a的克隆，实现A类的深度克隆
			} catch (CloneNotSupportedException e) {
				e.printStackTrace();
			}
			return o;
		}
	}
	
3.接口Cloneable作用:标记对象可以被复制，否者抛出`CloneNotSupportedException异常`

4.实现Cloneable接口的类通过`super.clone()`调用来实现克隆能力;

## 二十九.内部类

1.如果A类需要直接访问B类中的成员，而B类又需要建立A类的对象。这时,为了方便设计和访问，直接将A类定义在B类中。就可以了。A类就称为内部类。内部类可以直接访问外部类中的成员。而外部类想要访问内部类，必须要建立内部类的对象。

2.内部类分类

>2.1.非静态内部类：内部类是外部类的组成部分。内部类的实例存在必须依赖外部类的实例对象。有内部类实例肯定有其外部类实例，反之不一定。所以内部类可以访问外部类资源，反之不行。<br>
2.2.静态内部类 。静态内部类不需要外部类的实例对象。<br>
2.3.局部内部类<br>
2.4.匿名内部类

3.内部类一些细节

当内部类定义在外部类中的成员位置上，可以使用一些成员修饰符修饰 `private`、`static`。

3.1.默认修饰符。

直接访问内部类格式：`外部类名.内部类名 变量名 =  外部类对象.内部类对象;`

	Outer.Inner in = new Outer.new Inner();//这种形式很少用。

但是这种应用不多见，因为内部类之所以定义在内部就是为了封装。想要获取内部类对象通常都通过外部类的方法来获取。这样可以对内部类对象进行控制。

3.2.私有修饰符。

通常内部类被封装，都会被私有化，因为封装性不让其他程序直接访问。 

3.3.静态修饰符。

如果内部类被静态修饰，相当于外部类，会出现访问局限性，只能访问外部类中的静态成员。

注意；如果内部类中定义了静态成员，那么该内部类必须是静态的。

内部类编译后的文件名为：“外部类名$内部类名.java”；

4.为什么内部类可以直接访问外部类中的成员呢？

>那是因为内部中都持有一个外部类的引用。这个是引用是 `外部类名.this `
内部类可以定义在外部类中的成员位置上，也可以定义在外部类中的局部位置上。
当内部类被定义在局部位置上，只能访问局部中被final修饰的局部变量。

5.匿名内部类

>5.1.没有名字的内部类。就是内部类的简化形式。一般只用一次就可以用这种形式。匿名内部类其实就是一个匿名子类对象。想要定义匿名内部类：需要前提，内部类必须继承一个类或者实现接口。<br>
5.2.匿名内部类的格式：new 父类名&接口名(){ 定义子类成员或者覆盖父类方法 }.方法。<br>
5.3.匿名内部类的使用场景：<br>

当函数的参数是接口类型引用时，如果接口中的方法不超过3个。可以通过匿名内部类来完成参数的传递。其实就是在创建匿名内部类时，该类中的封装的方法不要过多，最好两个或者两个以内。

6.类与类之间数据的传递

>通过函数参数传递<br>
set方法<br>
构造函数

7.内部类应用场合：在java awt swing GUI中处理事件，Android中处理事件。

	class Outer{
		int num = 4;	
		class  Inner {
			void show(){
				System.out.println("inner show run "+num);			
			}
		}
		public void method(){
			Inner in = new Inner();//创建内部类的对象。
			in.show();//调用内部类的方法。 
		}
	}

--------

# 持续更新中...(催更请留言或联系我)

谢谢观看~