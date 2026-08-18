---
layout: post
title: 山河SHCTF（restu
date: 2024-12-17 22:56:29 +0800
categories: [ctf赛集（）]
---

#### 1z_flask
前面很正常
robots
然后/s3recttt
得到这个python文件
应该是这个的源码
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-13 110358.png)
访问/api得到
![]({{ site.baseurl }}/assets/images/Pasted image 20241013110456.png)

这个一看就是把目录给出来了
所以想得到flag
就得查看里面的
cat语句（linux

因为不知道咋办所以卡这了

现在看wp才知道直接
/api?SSHCTFF=cat /flag
直接get然后cat /flag（注意cat后面空格）
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-13 110358 1.png)
所以直接用get传参，cat指令查看


#### MD5-Masters
这题wp说不能用hackbar（微笑
很不巧我就用了无果
（应该也用了bp，不过可能传参传错了hh

<mark>注意：</mark>
<mark>post传参分号；可以连接两层</mark>
<mark>注意传参连接一般用&，就是和，不要记错了，分号应该也可以</mark>


#### 蛐蛐?蛐蛐!

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-13 113000.png)
看到源码

![]({{ site.baseurl }}/assets/images/Pasted image 20241013113224.png)
不知道为啥我这个是乱码
不过通过猜测和操作，这几个乱码都是文字呵呵

if ($_GET['ququ']  == 114514  &&  strrev($_GET['ququ']) != 415411)
    get传参ququ
    检查通过 GET 方法获取的参数`ququ`的值是否为 114514，并且检查将这个值反转后的结果不等于 415411。
		<mark>strrev（）这个是把值反转的函数</mark>

所以我们要ququ的值等于114514，同时满足反转不等于415411
所以加上字母就可以了，ququ=114514a
（而且这里是弱等于）
  ![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-13 113616.png)


 if($_POST['ququ']!=null){
        $eval_param = $_POST['ququ'];
        if(strncmp($eval_param,'ququk1',6)=== 0){
            eval($_POST['ququ']);
    <mark>`strncmp()`函数用于比较两个字符串的前若干个字符。</mark>
      在这里，它比较变量`$eval_param`的前六个字符与字符串`ququk1`是否相同。如果相同，则返回值为 0。

（这里用的强比较）
eval_param这个是post传参的ququ
要实现的话，就得用post传参ququ一个值
让它等于ququk1前六个字符（直接相等就可以）
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-13 114818.png)

好像是给了目录？
所以cat可以直接得到
wp：分号连接哦
；==system=（‘cat /flag’）;==
【这个语句好像常用欸，system=（‘ ’），然后cat /flag】
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-13 114933.png)





#### poppopop
