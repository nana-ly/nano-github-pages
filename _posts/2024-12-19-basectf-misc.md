---
layout: post
title: basectf (misc
date: 2024-12-19 22:42:00 +0800
categories: [misc]
---

*#### **海上又遇鲨鱼**
     流量分析
        海上遇到鲨鱼比较简单，比起流量分析其实可以直接用记事本打开（可能有点卡）然        后就可以找到flag不过是倒着写的，正着写过来就是flag
用鲨鱼打开
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-02 100952.png)

然后可以导出zip
选中该http请求后，选择区域，右键选择 **导出分组字节流** 即可将响应体内容导出
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-02 101909.png)
直接重命名为zip压缩包文件，戳开发现要密码
（之前因为不知道密码，爆破都试了，这个爆破不出来，因为密码是复杂一点的，后面一直以为是伪加密，修改了09为00，没用，这个应该是真加密，它是前09后09，具体不是特别明白，但是总之都没用所以得找密码）

需要密码，再次<mark>返回去看流量包前面的密码</mark>：
    （找密码的一般思路往前面流量分析找）
<mark>像这种 cannot log in 应该就是登录失败了，所有它前面的密码我们就不用管。</mark>
（这个里面只能看见有flag的zip，提出zip，并没有看见密码，所以可以试试从上面流量分析找到密码）
![]({{ site.baseurl }}/assets/images/Pasted image 20240902095916.png)
看到这边很多都是输入密码，然后最后边会有cannot logged in，那这种密码就都是错的，往下翻直到看见这个logged in，这个密码应该就是真的密码，然后可以试试

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-02 100122.png)
发现可以打开，打开即得flag
![]({{ site.baseurl }}/assets/images/Pasted image 20240902100843.png)

#### base？
     就是解码，这种还怪特殊


![]({{ site.baseurl }}/assets/images/Pasted image 20240902102900.png)
这个玩意用随波逐流解密，不得不说这个好用yy，之前用厨子什么的都没试出来，可恶，现在看出来是XXencode编码，emm一种特殊的编码，





#### ez_crypto
直接解 base64 肯定不行，最开始以为要先转一次埃特巴什，但是转了再解也不行。
![]({{ site.baseurl }}/assets/images/Pasted image 20240902104551.png)
但是它有很强的 base64 特征，我们知道 flag 格式开头是 BaseCTF{，base64 加密看看：
![]({{ site.baseurl }}/assets/images/Pasted image 20240902104559.png)


对比发现是大小写做了转换，我们转回去： 
得到：
QmFzZUNURntUaDFzXzFzXzRuX2V6X2I0c2U2NGRlYzBkZX0=
解 base64 即可：

![]({{ site.baseurl }}/assets/images/Pasted image 20240902104653.png)
拿到 flag：BaseCTF{Th1s_1s_4n_ez_b4se64dec0de}

这里也可以直接在这个里面改，把A-Za-z0-9+/=大小写互换，成这样a-zA-Z0-9+/=，然后就出了
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-22 112509.png)

也可以改成这个abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789+/
然后也能出（这个就是把base64的所有涵盖字符都写出来）

![]({{ site.baseurl }}/assets/images/Pasted image 20240922113208.png)
#### broken.mp4
     给两个mp4，按照第一个找到那个博客，然后下载untrunc，根据博客其实就是提示，其实很明显，自己主要是装了忘记写了泪目

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-06 123147.png)


![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-06 123132.png)
这里把第一个mp4和第二个放到这里，开始修复，得到一个新的mp4
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-06 123126.png)
点开看视频可得flag
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-06 123111.png)






#### 捂住X只耳
     泪目居然是摩斯密码

首先右键分离立体声到单声道，将上下分开
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-22 091230.png)

随便选中一个（这里选的是上面的声道），点效果然后特别鸣谢，反相（其实反相之后不是很明显，但是仔细看可以看出来区别）
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-22 091206.png)
选中全部，Ctrl+A，然后选轨道，选里面的混音，混音并渲染到新轨道

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-22 091151.png)

得到一个混音（由于声音太小所以看起来是一条直线，这里就增幅放大）
（wp里面说仔细听，可以发现前45秒没有声音，45秒后有段嘟嘟声）

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-22 091132.png)
发现45秒后这段比较像摩斯密码，记录一下，然后解码

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-22 090230.png)

【然后可以转为多视图（更像线段和点），拖长，可以看的更加明确】
![]({{ site.baseurl }}/assets/images/6b707441fab7e3f74b2155edd97f5008.png)


（一个摩斯密码表）

![]({{ site.baseurl }}/assets/images/Pasted image 20240922085734.png)

（网站，或者厨子里面搜摩斯密码from Morse Code也可以）

![]({{ site.baseurl }}/assets/images/Pasted image 20240922085930.png)

可以用网站直接解码，或者手动解码（看表）
得到flag


#### 二维码1-街头小广告


直接用QR Research可以解出

     （之前QR没反应，可能是电脑有点小bug，但是其实是可以直接查的）

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-22 143645.png)

 https://www.bilibili.com@ qr.xinshi.fun/BV11k4y1X7Rj/mal1ci0us  
?flag=BaseCTF%7BQR_Code_1s_A_f0rM_Of_m3s5ag3%7D

BaseCTF%7BQR_Code_1s_A_f0rM_Of_m3s5ag3%7D
这个应该是flag，然后要解码

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-22 145216.png)


（这里应该是URL编码，这边是采用直接随波逐流很舒服得出）
BaseCTF{QR_Code_1s_A_f0rM_Of_m3s5ag3}
#### 正着看还是反着看

     好像是要写脚本啥的吧，那个点开就知道是反着写的还不是倒转，就是galf这种

首先打开一个flag文件，拖到010中看看二进制

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-22 162030.png)

看看头尾会发现这里发生倒转，就是反着写的，（比如这个结尾FIFJ，按理来说应该是JFIF）
所以需要写个脚本把它反过来（或者用厨子操作，这里是写脚本）

这里创建了一个新项目，然后把之前
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-22 154955.png)
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-22 155007.png)
复制这个图片文件
打开kali
首先创建一个文件夹，这里是叫ctf
然后把图片文件复制过来

开始操作，首先命令指向ctf这个文件夹
（两种方式）
直接找到那个文件夹，拖到这个kali操作界面，回车即可
     （这里开始忘记指向命令了...）
指向命令cd ，cd  ctf，这样cd 加文件夹名就可以直接指向

然后使用分离的命令binwalk这个文件

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-22 161831.png)
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-22 161847.png)

按照上面代码进行
binwalk -e  flag1.jpg（binwalk -e  +文件名）
ls




#### 我要吃火腿！

打开有两个文件，一个图片，一个文档
文档打开发现全是嗷呜嗷呜这种，所以应该是兽音加密
可以用网站解密，也可以打开ToolsFX选择兽音然后解密

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-22 171324.png)

得到

    def xor_with_ham(input_file, output_file):
    ham_bytes = [0x48, 0x61, 0x6D]
    
    with open(input_file, 'rb') as f:
        data = bytearray(f.read())

    for i in range(len(data)):
        data[i] ^= ham_bytes[i % 3]

    with open(output_file, 'wb') as f:
        f.write(data)

代码审计，发现是进行了[异或运算](https://so.csdn.net/so/search?q=%E5%BC%82%E6%88%96%E8%BF%90%E7%AE%97&spm=1001.2101.3001.7020)。异或运算具有对称性，即对某个数据进行两次相同的异或操作后，结果会还原为原始数据，换一下处理对象，再运行一边就成
     这里直接看的wp，自己并不知道是啥，不过查一下可以知道是异或运算

   在之前代码后面加上 xor_with_ham('Hamorl.jpg', 'Ham.jpg')，把这串代码新建一个py脚本，和之前操作一样，把安装包解压到和脚本一起
   运行，发现可得一个新文件

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-22 183201.png)

打开发现是一个火腿图片

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-22 183227.png)

拖到010看看，发现这个图片里面藏有WAVE，藏着音频，所以要分离出来

![]({{ site.baseurl }}/assets/images/Pasted image 20240922183135.png)

和之前一样，用kali操作
复制图片过来，然后kali操作分离

这里发现用binwalk分离不了

     ──(kali㉿kali)-[~/ctf]
    └─$ binwalk Hamoral.jpg  

    DECIMAL       HEXADECIMAL     DESCRIPTION
     
    0             0x0             JPEG image data, JFIF standard 1.01

所以改用foremost分离试试
（因为这里foremost没安装所以开始用不了，附一张安装foremost的图片）
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-22 182601.png)

安装好大概就是这样

然后开始用foremost分离，foremost + 文件名（和binwalk类似）

![]({{ site.baseurl }}/assets/images/Pasted image 20240922190529.png)

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-22 182635.png)

可以发现分离出来一个output文件夹（从ctf文件夹中可以看到）
点开文件夹，发现有个wav文件夹，点开就是一段wav音频文件

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-22 182754.png)

听音频只能听出很奇怪的声音
应该是***SSTV***，无线电，
一种解释说Ham不仅有火腿也有***无线电通讯爱好者***的意思
（我觉得很有道理）

然后搜索如何接收即可得
这里是下载一个robot36的软件，它通过听这个wav音频，可以解出flag
（操作就是，打开音频声音，公放，点开软件让软件听到接收到，然后慢慢出现flag）

![]({{ site.baseurl }}/assets/images/bb862771fc73ebbf3f7cd1d147c64130_720.jpg)


#### 反方向的雪


前面和正反看一样的解法
然后得到一个加密的flag文件
![]({{ site.baseurl }}/assets/images/Pasted image 20240924214857.png)


还提示密码是n0secr3t
用这个试试分析不是文件密码
爆破发现密码123456
得到文件夹，上面写no flag here
根据题目中雪的猜测，可能是snow隐写

**注意！！**把得到的flag文件放在和snow一个地方**
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-24 214059.png)

然后点击**空白右键，打开终端**

<mark>snow隐写</mark>
**格式：**
<mark>SNOW.EXE -C -p +密码  +文件名</mark>

按格式来输入这个
SNOW.EXE -C -p n0secr3t flag.txt

得到flag

![]({{ site.baseurl }}/assets/images/Pasted image 20240924213617.png)

#### 根本进不去啊


#### 纯鹿人
      首先一个隐写，emm

打开一个word文档
一句话和一个ikun的颠图
ctrl+A全选，发现那行字下面也被覆盖了，（把图片挪开）所以应该是藏了点什么
直接改颜色，会发现藏了一串字符，应该是要解码
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-22 194958.png)
解码发现给的是密码，所以后面应该是要用到密码
密码：ikunikun
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-22 195143.png)

接着，把整个文档拖入010看看，发现开头PK这串
所以它应该是个压缩包，直接改为zip
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-22 195318.png)

看了半天压缩包里面只有一个图片
打开是ikun颠图

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-22 195551.png)
拖入010发现又是压缩包
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-22 195657.png)
修改输入密码可得flag
![]({{ site.baseurl }}/assets/images/屏幕截图 2024-09-22 195938.png)


#### Base revenge
     看了半天用base64解也没用，给的hint也很懵，提示说是隐写，当时没继续写下去，现在wp说是base64隐写，好吧，第一次听说，涨知识了

打开一堆base64，拖到底发现hint

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-23 162635.png)

随波逐流一下发现是Atbash加密
后面可能会用到

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-23 163005.png)

base64解码出来发现全是含base64的句子
猜测是base64隐写
台上脚本

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-23 163915.png)
得到这一串
按照提示，应该也是Atbash加密

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-23 164058.png)
得到明显的base64全小写版
一个脚本还原
然后base64解密得到flag

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-23 164801.png)

![]({{ site.baseurl }}/assets/images/屏幕截图 2024-11-23 164824.png)
