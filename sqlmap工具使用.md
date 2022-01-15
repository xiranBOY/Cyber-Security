# 常用渗透工具讲解

## sqlmap工具的使用		

* 打开kali linux 的 terminal
* 输入sqlmap



#### sqlmap -u 目标网站url

* 全面检测网站是否存在sql注入漏洞

#### sqlmap -u 目标网站url --dbs

* 查看此网站的库

#### sqlmap -u 目标网站url - D 指定库名 -- tables





* -D：指定库
* -T：指定表
* -- columns跑字段
* -C指定字段
* -- dump获取数据





## 常用指令

* -- random-agent:防止sqlmap表示的开头请被拦截
* --delay=1:每次访问间隔1秒，防止因为速度过快的访问被拦截
* -- count：查看字段中的数据数量
* --level 1-5:检测等级，等级数量越高检测越细致一般用 --level 3
* --risk:和level相近
* 一般sqlmap的使用方法：--level 3 --risk 2
* --is--dba 
  * 使用方法：sqlmap -u URL --is-dba
  * 当--is-dba检测为TRUE时可以使用
    * --os-shell：直接获得目标网站的cmd权限
    * 可以直接使用网站的cmd

## burp suite的使用

