 # sql注入

注入攻击：将用户输入的信息当做代码执行

sql注入：用户输入的数据当作sql代码进行执行

xxs：用户输入的数据当作前端代码执行

xxe：用户输入的数据当作xml代码执行

代码执行：用户输入的数据当作后端代码执行 

命令执行：用户输入的数据当作系统代码执行

 1998年创造出sql漏洞

随着GET传参的不同，网站的内容也不同 

## sql注入攻击过程

* 检测漏洞是否存在
  * and 1=1:正常   and 1=2：不正常，如果显示正常表示这个网站有传参强转
    * 如果都为不正常就进行URL编码再放进URL栏中执行
    * 因为网站会对特殊的字符进行拦截
    * 也可以尝试转换如-1=-1或-9999=-9999
  * 可以用运算符号检查漏洞是否存在
    * 要判断传参是否被强转，1a3s强转为1
  * 数据库会对用户输入的语句进行运算
    * 如：select 8+1
    * 数据库的显示就是9
    * 所以可以用select*from news where id=2-1;
    * 进行检测漏洞是否存在
    * 所有的GET传参都是要进行url编码，+在url编码后是空格
* 利用漏洞获取数据





* union:联合查询，将两条sql语句的结果一同输出（满足条件：相同字段数，相同类型）
* order by：排序，存在数据库注入的网页字段数量
* database()：系统自带的函数，查看当前所在数据库的名称 
* information_schema：系统自带库，这个库里面存在着表和库的关联，这个中存在着tables表，这个表中存在着库和表的关联 
  * 库.表.字段：代表选择x库中的x表中x字段
* limit：查看字段名称（分页）
  * limit 0，1
  * limit 1，1





# sql注入顺序

1，检测是否出现sql注入漏洞

2，URL+空格+order by  1检测字段数量

3，一直扩大order by数量直到网页显示不正常为止

4，运用union联合查询（如果有两个字段的话，union select 1,2并且把之前的id改成9.9999999，因为一般id数据类型都是整数int类型改成这样前面正常的内容就输出不了只能输出后面我们查询的内容）

5，数据库会选择性的输出输入的内容，只要把选择性输出的内容的地方改写成想要查询的sql语句 

6，库，表，字段，输出

7，寻用database（）系统自带函数检测当前所在数据库的名称（如：union select 1,database()）例子中输出点为2的位置所以只要把id的数量改写成9.99999并且把2的位置写上sql的语句就可以

8,union联合查询表，如：union select 1,table_name from information_schema.tables where table_schema=database()  查询表名\

9,union联合查询字段，如union select 1,colum_name from information_schema.columns where table_name='admin' and table_schema=database()

10,union查询数据，如：union 1,password from admin