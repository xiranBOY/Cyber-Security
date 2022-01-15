# 后端基础PHP简介及基本函数下

* 循环语句

  * 满足某个条件下一直循环

  * while循环

    * 布尔值

    * ~~~php
      <?php
      
        while(条件)
        {
          // code
        }
        
      ?>
      ~~~

    * 编码问题就在PHP代码之前加一行html代码

    * <meta chartea = "utf_8 ">

  * for循环

    * 主要用于进行代码审计工作

* 传参

  * GET传参
    * 获取：搜索栏，获取数据
    * 
  * POST传参
    * 上传：上传数据，评论栏
  * $_GET:数组获取GET方式传参
  * $_POST
  * $_COOKIE
  * 传参方式

* php操作mysql数据库

  * $conn = mysqli_connect("127.0.0.1","root","root","db_name")
  * 连接数据库
  *  
  * mysqli_close($conn);
  * 关闭mysql数据库
  * $row = mysqli_fetch_row();
  * 返回一行数据
  * $table = mysqli_fetch_all();
  * 返回所有数据
  * $row = mysqli_fetch_array($result);
  * mysqli_cluse($conn);
  * 关闭数据库   c