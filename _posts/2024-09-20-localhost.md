---
layout: post
title: localhost
date: 2024-09-20 10:55:37 +0800
categories: [web]
---

其他题已结很舒服暂不记录

#### 302跳转
     暂时不会
 需要抓包

ctfhub那个应该是把index.hxml改成index.php然后抓包可得
然后那个页面还有可以跳转的，就是相当于按键的东西，看源代码给以提示

这个hubu网站localhost的
就这么句话
This is a HTML page for 23CTF.
      开始思路把结尾的fun.html改了23CTF.html
      改.php改index.php都试过
      源码，抓包都试过没什么反应和特殊的。。。求大佬吧


[302](https://so.csdn.net/so/search?q=302&spm=1001.2101.3001.7020)跳转，http状态码302表示临时性重定向，即访问一个url时，被重定向到另一个网址上。

301：永久移动。请求的资源已被永久的移动到新URI，返回信息会包括新的URI，浏览器会自动定向到新URI。今后任何新的请求都应使用新的URI代替

302：临时移动。与301类似。但资源只是临时被移动。客户端应继续使用原有URI

![](https://i-blog.csdnimg.cn/blog_migrate/6b7d8ca7d89f964c31090ed242d03aee.png)

curl -i参数打印出服务器回应的 HTTP 标头。

curl -i https://www.example.com 上面命令收到服务器回应后，先输出服务器回应的标头，然后空一行，再输出网页的源码。



#### **查看源码**
一般常用
- <mark>F12</mark>，
- <mark>Ctrl+U</mark>，
- <mark>鼠标右击网页</mark>，选择查看源代码

以及 在浏览器中打开你要查看源代码的网页，然后在网址https或http前输入view-source:，
比如：view-source:https:// w w w. baidu.com/ 浏览器将显示该网页 HTML 源代码

***F12和右键选择用不了或者被阻止的时候，用ctrl+u说不定可以***

#### 暴力破解
    这个暴破吧，我也不知道我解出来没，以后问问别人
开始输的admin和password
显示Invalid username or password
意思是无效的用户名或者密码
所以可能有个是错的
一般先默认用户名对暴破密码
发现密码admin是302 1266不同
觉得密码应该是admin
修改密码之后admin admin输入
出现Congratulations！
    出现恭喜！所以应该是正确的？！但是没有找到flag......很奇怪啊，所以我也不确定是不是对了，但是大致思路应该是对的


#### 源码泄露
     待我学成归来



#### Git（）泄露
    同样待学


#### Vim书写中断
    静待研究
