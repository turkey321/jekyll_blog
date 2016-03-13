---
layout: post
title:  "符海飞NIIT课堂笔记"
date:   2016-3-6
categories: 笔记 NIIT
duoshuo: true
---


* content
{:toc}

#板块一:J 2 S E基础

---

##第一部分:JAVA概述

###一.开发语言
1.所有的开发语言都需要经过编译转化成机器指令执行。<br>
2.`低级语言`接近硬件，编译处理的过程减少，直接可以向硬件发出指令，执行速度快，编码困难，不容易掌握。<br>
&nbsp;&nbsp;&nbsp;`高级语言`在低级语言的基础上做了更进一步的封装提供了更简便的方法接口便于使用，执行的速度降低。


###二.JAVA分类与内涵
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

###三.JAVA特点

>1.开源<br>
2.跨平台：在各个操作平台的操作系统上引入JVM(java虚拟机)来解决跨平台问题。<br>
`（JVM实行步骤：1.载入class文件 2. 验证 3. 解析翻译。）`<br>
3.面向对象<br>
4.简单<br>
5.安全性<br>
6.多线程<br>
7.兼顾解释性与编译性语言的特点 

###四.JRE 
 释义:`Java Runtime Environment`:<br>
java程序的运行环境，java运行的所需的类库+JVM(java虚拟机)。

###五.JDK目录结构  
1.释义:`Java Development Kit `:java的开发和运行环境，java的开发工具和jre。<br>
2.`bin目录`：存放可执行的指令文件。   例： java.exe  javac.exe

###六.配置环境变量
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

###七.DOS中JAVA命令 
1.DOS中的java命令的作用的有效范围在当前命令窗口中。
操作例:<br>`java`  `java-verbose`   `set`		`set path`		`set path=xxxxxx`

2.javac命令和java命令:<br>
	要知道java是分两部分的：一个是编译，一个是运行。<br>
	`javac`：负责的是编译的部分，当执行javac时，会启动java的编译器程序。对指定扩展名的.java文件进行编译。生成了jvm可以识别的字节码文件。也就是class文件，也就是java的运行程序。<br>
	`java`：负责运行的部分.会启动jvm.加载运行时所需的类库,并对class文件进行执行.<br>
	一个文件要被执行,必须要有一个执行的起始点,这个起始点就是main函数.<br>

###八.JAVA开发的步骤
编写源程序文件 `*.java`<br>
javac编译<br>
java在DOS中运行  `java [-options] class [args...]`<br>

###九.变量的生命周期与作用域
PS:变量的有效范围看他定义所在的括号内。

###十.常用操作
1.单行注释 `ctrl+/`
2.多行注释 `ctrl+shift+/`
3.代码补全 `alt+/`
4.代码导入 `ctrl+shift+o`

---------------

##第二部分:JAVA基础

###一.基本语法
1.java是严格区分大小写的<br>  
2.java代码分为结构定义语句和功能执行语句<br>
`(功能执行语句的最后必须用分号结束)` 

###二.标识符和关键字
1.java中的标识符 <br>
java中的包、类、方法、参数和变量的名字，可由任意顺序的`大小写字母`、`数字`、`下划线(_)`和`美元符号($)`组成，但标识符不能以数字开头，不能是关键字。<br>

2.java中的关键字
![1]({{"/images/NIITNOTE/1.jpg"| prepend: site.baseurl }}) 

PS：java 无`sizeof` ,`goto`, `const` 关键字，但不能作为变量名用

###三.常量
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

###四.变量及数据类型
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

###五.运算符
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

###六.流程控制语句
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

###七.函数
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

###八.函数的重载
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

###九.内存的划分
1：`寄存器`。<br>2：`本地方法区`。<br>3：`方法区`。<br>4：`栈`。<br>5：`堆`。<br>

>栈：<br>存储的都是局部变量 ( 函数中定义的变量，函数上的参数，语句中的变量 )；<br>
	只要数据运算完成所在的区域结束，该数据就会被释放。<br>
堆：<br>用于存储数组和对象，也就是实体。啥是实体啊？就是用于封装多个数据的。<br>
1：每一个实体都有内存首地址值。<br>
2：堆内存中的变量都有默认初始化值。因为数据类型不同，值也不一样。 <br>
3：垃圾回收机制。<br>
对比:堆内存容量比栈内存大，但读写速度栈内存更快。<br>

###十.数组
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

###十一.Main函数<br>
`Public`：访问权限最大。<br>
`static`：不需要对象，直接类名即可。<br>
`void`：主函数没有返回值。<br>
`Main`：主函数特定的名称。<br>
`(String[] args)`：主函数的参数，是一个字符串数组类型的参数，jvm调用main方法时，传递的实际参数是 new String[0]。<br>

jvm默认传递的是长度为0的字符串数组，我们在运行该类时，也可以指定具体的参数进行传递。可以在控制台，运行该类时，在后面加入参数。参数之间通过空格隔开。jvm会自动将这些字符串参数作为args数组中的元素，进行存储。




--------

#持续更新中...

催更请按照下面联系我,谢谢~