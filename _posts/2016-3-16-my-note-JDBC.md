---
layout: post
title:  "符海飞的课堂笔记--JDBC"
date:   2016-3-16
categories: 笔记 JDBC
duoshuo: true
---


* content
{:toc}

# 第一部分:Oracle简介

## 一.简介

1.数据库分类

商用: `oracle db2（IBM） sybase sqlserver（微软）`<br>
开源: `mysql postgresql access（Office）`

2.产品的性能

>1、并发数量<br>
2、数据计算量

3.语言常用数据库

>java：`oracle` `mysql` `postgresql`<br>
.net: `sqlserver`<br>
android:`sqlite`

4.Oracle学习方向

>管理：管理数据的安全，用户的管理、权限的管理、数据的备份、恢复等<br>
开发：使用数据库中的一些逻辑对象(表、视图等)对数据的增、删、改、查的操作

5.Oracle的服务

`TNSLIstener`：监听服务<br>
`OracleServiceXXX`:数据库(实例)服务

## 二.数据库介绍

1.数据存储系统  

数据以文本、数字、图片或声音等形式存储。 

2.数据库概念  

数据库是一组在逻辑上相关的信息的集合 。<br>
表以行和列的形式保存数据。<br>
实现数据库管理任务的软件叫做数据库管理系统(`DBMS`)。

3.两种数据库管理系统 (`DBMS`)是： 

>关系型数据库管理系统 (`RDBMS`) <br>
面向对象的关系型数据库管理系统 (`ORDBMS`) 

三.ER图 

1.实体--关系图<br>
以图形方式表示数据库的逻辑结构 <br>
可被看作是数据库的蓝图 

2.画ER图的指南是：<br>
1).确定各实体 <br>
2).确定实体的属性 <br>
确定实体之间的关系 

3.ER图的组件：

`实体`-----实体是物体、场地、人或可记录其数据 的活动。<br>
`属性`-----是实体的特征

4.联系 : 指实体之间的关联

1).联系的类型 

	一对一 
	一对多或多对一 
	多对多 
	
2).标定联系或非标定联系

每个实体类型都有自己的标识符，如果两个实体集之间发生联系，其中一个实体类型的标识符进入另一个实体类型并与该实体类型中的标识符共同组成其标识符时，这种联系则称为标定联系，也叫依赖联系。反之称为非标定联系，也叫非依赖联系。

------------------------------------------------------------

# 第二部分:SQL语句

## 一.SQL定义
SQL:`Structured Query Language`

SQL用来检索和维护数据库中数据 <br>
1.使用SQL的优点 ：

>SQL是所有RDBMS使用的公共语言 。<br>
SQL不遵循任何特定的执行模式，它一次可以访问多个记录 。<br>
SQL使用简单的维护数据的命令。<br>
SQL语句非常接近英语自然语言，因此，易学易懂。

## 二.数据类型
1. `Char`

char的长度是固定的，比如说，你定义了char(20),即使你你插入abc，不足二十个字节，数据库也会在abc后面自动加上17个空格，以补足二十个字节char是区分中英文的，中文在char中占两个字节，而英文占一个，所以char(20)你只能存20个字母或10个汉字<br>
char适用于长度比较固定的.一般不含中文的情况比如身份证 查询效率快 定长匹配

2.`Varchar`/`Varchar2`

varchar是长度不固定的，比如说，你定义了varchar(20),当你插入abc，则在数据库中只占3个字节。varchar同样区分中英文，这点同char<br>
varchar2基本上等同于varchar，它是oracle自己定义的一个非工业标准varchar，不同在于，varchar2用null代替varchar的空字符串

3.`Nvarchar`/`Nvarchar2`

nvarchar和nvarchar2是长度不固定的 <br>
nvarchar不区分中英文，比如说：你定义了nvarchar(20),你可以存入20个英文字母/汉字或中英文组合，这个20定义的是字符数而不是字节数

4.`Clob`

字符型大对象 最大4G

5.`Number`

也可以表示小数<br>
number(5,2)表示5位有效数,2位小数-999.99<br>
number(5)表示5位整数-99999

6.`Date`

用于存储日期，精确到秒

7.`Timestamp`

用于存在日期与时间信息，这个类型比Date更精确，最小能精确到小数点后9位

8.`Blob`

二进制数据 存放图片/声音...出于安全的考虑可以

## 三.综述SQL数据语言

1.数据定义语言 (`DDL`) : 包含一组命令，用来创建数据库对象，如表等 。
 
DDL可用于： 

>创建对象 
改变对象 
撤消对象 

2.数据操纵语言 (`DML`) : 用来操纵表数据 ，包含`INSERT`、`UPDATE`和 `DELETE`等命令 。

DML 可用于： 

>存储数据 
更新数据 
删除数据

3.数据查询语言 (DQL) : 用来对数据库表中的数据进行查询。

数据查询 使用select 语句

	select {* | select_list} from tablename;  

4.数据控制语言 (`DCL`) : 用来对数据库的使用者赋予和撤销数据库的权限设置。

DCL可用于

>授予权限
回收权限 

## 四.DDL (数据定义语言)

1.`create TABLE`语句<br>
用来创建数据库中表。 
	
	create table Students
	(
	cStudentCode char(4) not null,
	vFirstName varchar2(20) not null,
	vMiddleName varchar2(5),
	vADDress varchar2(35),
	cCity char(20),
	 ); 

2.添加列

`ALTER TABLE` 语句中`ADD` 子句用于在表结构中添加列。

	ALTER TABLE tablename ADD (columnname datatype [DEFAULT expression]);
	ALTER TABLE Students ADD(xxx number default 0); 

3.修改列

`ALTER TABLE` 语句中`MODIFY`子句用于更改列的属性。

	ALTER TABLE tablename MODIFY (columnname datatype [DEFAULT expression]);

修改操作会影响已有数据，可能会修改失败

4.撤消列

`ALTER TABLE` 语句中`DROP COLUMN`子句可除去表中的列。

	ALTER TABLE tablename DROP COLUMN columnname; 
	ALTER TABLE Students DROP COLUMN xxx;

5.重命名表

`RENAME`语句用于重命名表.

	RENAME <old_table_name> TO <new_table_name>;

6.`DROP TABLE`语句

`DROP TABLE`语句用于从数据库中删除表。 


	DROP TABLE table_name;

7.`Truncate` 格式化

	truncate table student1;

## 五.DML (数据操纵语言)

1.添加表中行

	INSERT INTO table_name(Column_List) VALUES(VALUES_list);

>每次插入一行记录<br>
缺省列表时，要插入所有字段的值<br>
指定赋值的字段列表，只为指定部分设置新值，其余字段被缺省赋值为`null`

2.数据拷贝插入

	INSERT INTO table_name(Column_List) select Column_List from table;
	INSERT INTO emp2(no,name) select dno,name from emp;

子查询的值列表要与insert子句中的字段列表相对应

3.update语句

用于改变表中存储的数据。 

	update tablename SET columnname = value [, columnname = value][where condition];  

可使用`where`子句限定要更新的记录，如果没`where`子句，则更新表中所有记录

	update student set age = age + 1 where age is not null;

4.语句  

表中冗余行可被用删除。

	delete table_name where condition; 

用`where`子句限定要删除的记录，如无`where`子句，则删除表中所有记录

5.约束 

用于实施数据完整性，以确认表中的数据。<br>
可从表中加入，撤消，删除，禁用和启用。
  
1).不能为空约束   `not null`

	name varchar2(20) not null
	name varchar2(20) constraint name_nn not null

2).唯一性约束	`unique key`

>a.确保所有字段(字段组合)不出现重复值<br>
b.允许出现空值<br>
c.字段级定义，表级定义

	sno number(3) unique,
	sno number(3),constraint student_sno_un unique(sno),

3).主键约束		`primary key`

>a.唯一表示表中的某一行记录，非空唯一<br>
b.一个表中只允许一个主键<br>
c.主键可以是单个字段或多个字段的组合<br>
d.字段级定义，标记定义

	sno number(4) primary key,constraint student_sno_pk primary key(sno),

联合主键

>a.多个字段组合而成的主键<br>
b.每个字段都不能为空<br>
c.组合不能出现重复<br>
d.标记定义约束<br>

	sno number(4),subno number(2),record number(3),constraint student_sno_subno_pk primary key(sno,subno)

4).外键约束		`foreign key`

>a.确保一个字段之间的参照关系，实现参照完整性约束<br>
b.通常来自于不同表的2个字段之间<br>
c.子表外键列的值必须在主表参照列值的范围内，或为空<br>
d.外键参照的必须是主表的主键或者唯一键<br>
e.主表外键值被子表参照时，主表相应记录不能被删除

	constraint emp_dept_fk foreign key(eno) references deot(eno)

5).检查约束

>a.定义每一行的指定字段都必须满足的条件<br>
b.以条件表达式的形式给出数据需要符合的条件

	age number(3) check(age >=0 and age <=120)
	age number(3) constraint age_ck check(age >=0 and age <=120)

6).域完整性约束

	not null
	check

7).实体完整性约束

	unique
	primary key

8).参照完整性约束

	foreign key

9).添加约束

	alter table  tablename add [constraint con_name] constraint_type(column)
	create table student(
	sno number(10),
	name varchar2(20)
	)
	alter table  student add constraint student_sno_pk primary key(sno);

10).非空约束添加

	alter table  student modify(name not null)

11).删除约束

	alter table  tablename drop constraint_name; 
	create table student(
	sno number(10),name varchar2(20) constraint student_sno_pk primary key(sno);
	)
	alter table  student drop constraint student_sno_pk;

主键删除的另一种方法

	alter table  student drop primary key;

12).删除约束—级连

删除一个列上的约束，列本身和所有引用此列的约束

	alter table  table_name drop constriant constraint_name [cascade];

13).删除约束—级连2

删除与此字段相关联的所有约束  `cascade constraints`

	alter table  table_name drop(col) cascade  constriant;

14).禁止，启用约束

	alter table  table_name disable constraints constraints_name; 
	alter table  table_name enable constraints constraints_name;

## 六.范式

>1.第一范式（`1NF`） ：<br>
是指数据库表的每一列都是不可分割的基本数据项，同一列中不能有多个值，即实体中的某个属性不能有多个值或者不能有重复的属性 <br>
PS:不满足第一范式（1NF）的数据库就不是关系数据库 <br><br>
2.第二范式（`2NF`） ：<br>
要求数据库表中的每个实例或行必须可以被惟一的区分 <br>
满足第二范式（2NF）必须先满足第一范式（1NF） <br>
惟一属性列被称为主关键字或主键、主码 <br>
实体的属性完全依赖于主关键字<br> <br>
3.第三范式（`3NF`） ：<br>
要求一个数据库表中不包含已在其它表中已包含的非主关键字信息<br> 
满足第三范式（3NF）必须先满足第二范式（2NF）。<br>
例: (学号) → (姓名, 年龄, 所在学院, 学院地点, 学院电话) <br>
(学号) → (所在学院) → (学院地点, 学院电话) 

------------------------------------------------------------

# 第三部分:查询

## 一.单表查询
1.语法

	select *  from tablename;
	select column_name[, column_name] from tablename;

2.别名

(重命名查询结果，增加可读性)

	select column_name column_heading [, column_name…] from tablename;

列名 与 别名之间可以加 `as` (可加可不加)

可用双引号`””`引起来,不加引号时，全部转为大写字母，要不转要加””,包含特殊字符要加””

	select eno 员工标号, name 员工编号 from emp;
	select eno as 员工标号, name as 员工编号 from emp;
	select eno as no, name as name from emp;
	select eno as "No:", name as "Name" from emp;
	select eno as "No:", name as 姓名 from emp;
	select eno as “No:”, name as “姓  名" from emp;

3.显示非重复行 `distinct`

在`select` 语句中用来观看表列中唯一的值

单个字段:

	select distinct column_name from tablename;

	select distinct dept from emp;

多个字段:

	select distinct dept, rat from emp;

4.运算符

对`select`语句中的`number`类型数据使用表达式

算术运算符   `加+，减-，乘 *，除/`

	select eno, name,sal,sal * 12 + 1000 from emp;
	select eno, name,sal,sal * (12 + 1)  from emp;

并置运算符 `||`

合并2个串

	select eno || name from emp;
	select name || ' 的员工编号是:' || eno from emp;

单引号 `转义’’`

	select eno, name || ' ''的工资是奖金是: ' || bonus || '人民币' from emp;
	select eno, name || ' ''的工资是奖金是: ' || bonus || '人民币' from emp;
	select eno, name || ' ''的工资是奖金是: ' || bonus || '人民币', sal * 12 + bonus, '  年薪是' || (sal * 12 + bonus) || '人民币' from emp;

空值  `空值不是空格或0`

算术表达式中如果有空值，则整个表达式结果为空<br>
连接表达式中出现空值，则被当为空字符处理<br>

比较运算符   `=	>	<	>=		<=		!=或<>`

逻辑运算符    `AND`	  `OR`   `NOT`

其他  `between...and...`	`in`

5.`where`

用于检索满足特定条件的数据

	select select_list from tablename where condition

	select * from emp where dno = 1;

字符串和日期要用单引号引起来<br>
字符串大小写敏感<br>
日期格式敏感，缺省 `DD-MON-RR`

	当期日期:select sysdate from emp;

	select * from emp where name = '张三';
	select * from emp where email = ' zhangsan@niit.com';
	select * from emp where sal > 2300;
	select * from emp where sal > 2300 AND dept = 2;
	select * from emp where sal > 4000 or sal < 2000;
	select * from emp where not dno = 2;
	select * from emp where hiredate > = '01-1月-2008';
	select eno, name as 工作已3年 from emp where sysdate - hiredate > = 365 * 3;
	select eno, name, sal from emp where sal between 2000 and 4000;
	select eno, name, dept from emp where dno in (2,3);
	select eno, name,bonus from emp  where bonus is null;
	select eno, name,bonus from emp  where bonus is not null;
	select eno, name, bonus, sal from emp where bonus is not null AND sal > 4000;

6.`like`<br>
`% `表示零或多个字符<br>
`_ `表示一个字符

	select eno, name from emp where name like '周%';
	select eno, name from emp where name like '周_';
	select eno, name,email from emp  where email like '%u%';
	select eno, name,email from emp  where email like '_ha%';
	select eno, name,email from emp  where email like '__a%';
	select * from sc where scname like '/%%'escape '/';

7.`ORDER BY`  (排序)<br>
`ASC` 升序(默认)<br>
`DESC` 降序

	select eno, name, sal from emp order by sal;
	select eno, name, sal from emp order by sal desc;
	select eno, name, sal,dept from emp order by sal desc,dept;
	select eno, name, sal,dept from emp order by sal desc,dept desc;

8.别名

	select eno, name, sal * 12 as 年薪,dept from emp order by 年薪 desc,dept desc;
	select eno, name, email,dept from emp order by email desc;

## 二.多表查询
1.基本语法:

	select table1.column_name, table2.column_name from table1, table2 where table1.column1 join_operator table2.column2; 

2.oracle提供的不同联接类型有:

>`EQUIjoin`			（等值联接） 
`NONEQUIjoin`		（非等值联接） 
`NATURAL join` 	（自然联接） 
`CROSS join` 		（交叉联接） 
`outer join` 		（外部联接） 
`SELF join` 		（自联接） 

3.迪卡尔积

(记录个数为两表乘积)

	select * from emp,dept;  
	select empno,emp.ename,emp.deptno,dept.dname from emp,dept;

4.等值联接（`Equijoin`,`inner jion`）

>列名前加表别名为了区分多个表中同列名，如果唯一，可以不加 <br>
用where来指出条件<br>
可以有多个查询条件<br>
使用表别名<br>
有n个表需要联接时，需要n-1个联接条件

PS:有可能会造成记录的丢失,应为该连接方式如果不满足关联条件的记录不显示

例:
只有满足公共列中联接条件的列值行才显示

	select empno,emp.ename,emp.deptno,dept.dname from emp,dept where emp.deptno = dept.deptno;
	select empno,emp.ename,sal,emp.deptno,dept.dname from emp,dept where emp.deptno = dept.deptno and sal > 25;
	select a.empno,a.ename,a.sal,a.deptno,b.dname from emp a,dept b where a.deptno = b.deptno;

5.非等值联接（`NONEQUIjoin`）

联接两个或多个表时，使用如`>`、 `<`、 `>=`、 `<=`、 `!=`、`between…and`或 `in`等比较运算符.

区间查询

	select a.empno,a.ename,a.sal,b.grade,b.losal,b.hisal from emp a, 	salgrade b  where a.sal between b.losal and b.hisal;
	(a.sal >= b.losal and a.sal <= b.hosal)

6.自然联接 （`NATURAL join`）

基于两个表的同名的一个或多个列联接.

不允许使用表名和别名做前缀.

	select empno,ename,deptno,dname from emp natural join dept;

7.用`USING`子句检索记录 

如果两个表中有同名的列，但不想进行自然联接，那么在联接语句里可以使用USING子句指定联接的列.

使用关键字CROSS的包含多个表的联接

相当于笛卡尔积，两表连接时没有使用`where`. 

	select emp.empno,emp.ename,dept.dname from emp cross join dept;
	(select emp.empno,emp.ename,dept.dname from emp,dept;)  `上下一样`

9.外部联接 (`outer join`) 

用于检索一个表的所有记录和另一表中的匹配行

运算符（`+`）

	select column_name, column_name [,column_name] from table_name [left | right | full] outer join table_name ON table_name.ref_column_name join_operator table_name.ref_column_name

	left outer join  (left join) : 返回第一个表的所有行和第二个表中的匹配行
	right outer join  (right join): 返回第二个表的所有行和第一个表中的匹配行
	full outer join   (full join): 返回两个表中的所有行

	select a.empno,a.ename,b.deptno,b.dname from emp a,dept b where a.deptno = b.deptno(+);
	select a.empno,a.ename,b.deptno,b.dname from emp a,dept b where a.deptno(+) = b.deptno;
	select a.empno,a.ename,b.deptno,b.dname from emp a full outer join dept b on a.deptno = b.deptno;

10.自联接（`Self join`） 

联接同一个表内的表的某一行与同一个表中的其他行相关联

	select a.vFirstName “Employee”, b.vFirstName “Supervisor” from Employee a, Employee b where a.cSupervisorCode = b.cEmployeeCode;

11.多表查询的基本分析思路
>1).需要查询的数据分布在哪些表中(确定表)<br>
2).确定表的关联条件(有n个表,需要n-1条关联条件)<br>
3).写查询语句<br>
4).检查结果是否正确(1.记录条数是否正确 2.数据是否正确)

## 三.子查询

>是在另一个查询内指出的查询。<br> 
在主查询内进行处理。<br>
应用圆括弧括起来。

	select outer_select_list from outer_table_name where expression (select inner_select_list from inner_table_name);

--------

# 持续更新中...(催更请留言或联系我)

谢谢观看~