---
layout: post
title: DOXbox debug
date: 2024-10-15 13:32:24 +0800
categories: [一些打开方式及处理等常用]
---

开启debug
    mount c: d:\g\masm
    c:
    debug

一些指令：
d 查看地址
e 修改地址
e改完地址然后用d查看，后面都带段地址：偏移地址

u 可以看见汇编语言
q 退出debug

p或者t 按一下执行一下语句
g 一次性执行完
可以用g来试试如果执行完毕会显示Program terminated normally

修改CS：IP可以用r
rcs，rip，rbx等
改完可以用r查看

查看后若想执行之前输入的mov语句可以用t

    在stack segment语句后添加stack，可以让link时不警告no stack segment（前提是代码中有stack segment

**masm编译和link连接时都可以直接加文件名不带后缀**
但是进入debug就不行，虽然会跟踪运行，但是会警告Extended Errors 2
**debug后面得带文件名和后缀，**   注意还不能分开写要一起输入

写汇编代码：

1. 先命名写  xx segment
         1. xx  ends

2. 然后在中间写指令mov，add，pop

3. 接着在最后空行写end

4. 然后开头写假设assume cs：xx或者ds：或者ss：

5. 最后的最后在写的指令后面加上mov ax，4c00h
                           int  21h


mov [si+08h],'$' ；这句出现问题operand must have size  
  
这条传送指令，编译软件不能确定是8位数的，还是16位数的。  
  
应该改成如下：  
  
mov BYTE PTR [si+08h],'$' ;说明是字节传送  
  
另外，还有：WORD PTR。说明是 字　传送。
