# ` 后端基础PHP简介及基本函数上

* 功能实现
* PHP标准后端语言
* 后端语言:ASP,JSP,ASPX,PHP

PHP：动态语言，将程序嵌入到HTML代码中执行，在PHP文件中输入HTML代码也可以进行执行，前端的代码也可以写入PHP文件进行执行   

PHP代码常用的两种标记风格：

* ```php
  <?php ?>
  ```

  

* ~~~ php
  <script language="php">
  </script>
  ~~~

* Asp 和 简介风格不常用

PHP代码

~~~ php
<?php

  phpinfo();
  
?>
~~~

PHP代码需要用分号结束一条语句例如：phpinfo();

echo"";

代表输出，双引号内输出内容

PHP变量

~~~php
<?php
 
$sentence = "Hello world";
//声明了一个名为sentence的变量并把它赋值为Hello world的字符串

echo $sentence;
//输出变量sentence  

?>
~~~

PHP常量（不会改变的量）

~~~ php
<?php
    
  define('name',"HanZiyan");
  //定义了一个名为name的常量并且赋值为HanZiyan 
  //name作为一个常量名也要加单音号或双引号  

?>
~~~

双引号和单引号是有区别的

单引号：直接输出内容不进行再次解析

双引号：不直接输出内容，进行再次解析，查看在双引号内的内容是否为变量或是常量，要是就直接输出变量或是常量的值 



函数:

* 功能的封装
* 例子：实现MD5加密
  * MD5（）:利用md5函数进行加密
  * echo md5('admin');
  * 利用上面的代码就可以输出字符串admin进行md5加密后的形式
  * admin => ad5 => 21232f297a57a5a743894a0e4a801fc3 
* 函数标准

~~~php
<?php
  
function functionName()
{
	//需要封装的代码块  
}

?>
~~~

例子

~~~php
 <?php 
  
function a()
{
  echo 'Hello world';
}
//创建函数

a();  
//调用函数

?>
~~~

例子解释：上述例子中定义了一个名为a的函数赋予函数输出字符串，崔后条用定义的函数

参数

可以向函数中传输参数

例子

~~~php
<?php 
  
function functionName($a)
{
  return $a + 1;
}
  
echo functionName(12);

?>
~~~

例子解释：上述例子中创建了一个名为functionName的函数，定义了一个传参变量a，调用函数的时候向函数中传入一个参数12 



代码注释

解释代码

~~~php
<?php 
  
//这是一行代码注释

?>
~~~

多行代码注释

~~~php
<?php 
  
/*
这是一个多注释
这是一个多注释
这是一个多注释
这是一个多注释
*/
  
?>
~~~

运算

= 代表赋值

== 代表比较数值

=== 代表比较类型且比较数值

如果比较成立返回1不成立什么也不返回

例子

~~~php
<?php 
  
$a = 1;
$b = 2;
echo $a === $b;
//什么也没有输出
  
?>
~~~



va r_dump()：函数（输出变量类型）

例子

~~~php
<?php
  
$a = 1;
$b = '1';
var_dump($a);
var_dump($b);
  
?>
~~~

例子解释：上面的代码创建了两个变量然后利用函数查询了两个变量的数据类型





#### 条件分支语句

if

例子

~~~ php
<?php
  
  $password = 070920;
 if($password == 070920)
 {
   echo 'This password is true !';
 }
else
{
  echo 'sorry this password is fales'; 
}
  
?>
~~~

