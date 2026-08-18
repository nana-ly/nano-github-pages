---
layout: post
title: knowalittle
date: 2024-07-18 11:24:41 +0800
categories: [knowlittle]
---

**ctf**  
（主要分web和pwn方向）
###### **web安全**   比较广题型多  知识点杂
         sql注入，xss，文件包含，代码执行
         
crypto密码学  做题可以先了解
misc杂项   广度很高，需要积累，很多没见过
         很多常用工具winhex查看文件头，stegsolve用于图片（图片中反色处理比如二维码），silenteye，
reverse逆向   靠关键的算法，输入校验
          静态分析和动态调试，一般给的是二进制文件，
          逆向工具IDA pro 和OD（ollydbg）/x64dbg
          逆向技术是pwn的前置技术，主要是发现关键过程
###### **pwn二进制漏洞挖掘与利用**   需要深入研究 靠关键的函数
                    常规：栈溢出，堆溢出，格式化字符串漏洞
                    给定编译好的二进制程序（win下exe文件，linux下elf文件）
                     栈溢出比如gets函数漏洞很大禁止使用
                    要会汇编，python，习惯Linux

团队一般分工：
web+misc   web+crypyo
pwn+re   re+crypto

可以学习
windows，linux

python可以先学脚本，下学期有课
数据库基本操作可以学，原理算了
http计算机网络基础可以看看基础的
常用工具
熟练应用搜索引擎包括ai

windows基础命令应该是在cmd
dir
ping 
ipconfig

linux基础命令 Is，cat
其他linux命令  ping，ifconfig，whoami，ps -aux
vim编辑器按住i插入字符，esc键然后


*是指所有内容，数据库所有列
传参用？问号直接·网站名后面加上/？id
用mysql必须要记得加；分号
