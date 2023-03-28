# 现代二进制开发文章-0x03

> 原文：<https://infosecwriteups.com/binary-writeup-0x03-9a9546711ef2?source=collection_archive---------0----------------------->

这是**现代二进制开发**课程的子部分 [RPISEC](https://rpis.ec/) 关于**工具和基本逆向工程**的第三篇综述。

讲座链接:-[http://security.cs.rpi.edu/courses/binexp-spring2015/](http://security.cs.rpi.edu/courses/binexp-spring2015/)

所有的课堂材料和其他必要的文件都可以在上面的链接中找到。

[⬅️](https://medium.com/bugbountywriteup/modern-binary-exploitation-writeups-ii-62c092f7f389) **上一篇报道**_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _**下一篇报道** [➡️](https://medium.com/bugbountywriteup/binary-writeup-0x04-baeed833ddf)

# crackme0x01

```
$./crackme0x01
```

![](img/cea1de8792bd7c778c90fe32d8279705.png)

crackme0x01

**使用雷达 2 进行破解**

```
radare2 crackme0x01 
[0x08048330]> aaa
[0x08048330]> pdf @ main
```

*   **aa:-** 分析全部。
*   aaa:- 分析更多信息。
*   **pdf:-** 打印拆解功能。

![](img/ac72bafe04581c841df413c536187f4b.png)

雷达 2

![](img/b7283c72754c6087ff21d07aff014af5.png)

主要在 radare2

在位置 **0x0804842b** 有 ***local_4h*** 与 ***0x149a 的 cmp(比较)。*** local_4h 是我们存储输入(密码)的变量。

![](img/d81708fc46e50b65013dbe7cbf4ac9ef.png)

转换

将 0x149a(comapred 值)作为 int(5274)输入。

![](img/06e4b1c485a141fa9e2c9543305fca7e.png)

二进制文件

**使用 gdb 破解**

```
**$gdb** crackme0x01
**gdb-peda$** disassemble main
```

![](img/0ebbd75be3aec5aedf50ef81c6361030.png)

```
**gdb-peda$** break *0x0804842b
Breakpoint 1 at 0x804842b
**gdb-peda$** run
```

![](img/5c1ab098ce8755daa1a851516fdc52f7.png)

**0x 804842 b**CMP DWORD***PTR【ebp-0x 4】***， ***0x149a*** 。PTR [ebp-0x4]是接受输入(密码)并与 **0x149a 进行比较的变量。**

**DWORD:-** 它指的是双字，双字是 32 位或 4 字节(8 位=1 字节)。

**PTR:-** 指针的缩写。

**【ebp-0x 4】:-**从 ebp(基址指针)寄存器中减去 4 个字节，所以现在指向子程序的第一个局部变量。

![](img/ba1305e969887875176a66cdbb8dc65c.png)

转换

```
$p/d 0x149a
```

*   **p:-** 打印命令(缩写为 **p** )
*   **d:-** 打印为带符号十进制的整数。

```
$p/u 0x149a
```

*   **p:-** 打印命令(缩写 **p**
*   **u:-** 打印为无符号十进制整数。

使用 python 转换 **'0x149a'**

```
$ python -c "print 0x149a"
```

![](img/8f98a45dede004b3f80bb79a09e9fa34.png)

特别感谢 Aleksey Covacevice 对我的帮助。

*感谢阅读！如果你喜欢这个故事，请* ***点击*** 👏 ***按钮，分享*** *帮助他人！欢迎发表评论*💬*下图。有反馈？下面我们连线上* [*推特*](https://twitter.com/yashanand155) *。*

## ❤️由[增加到](https://twitter.com/yashanand155)