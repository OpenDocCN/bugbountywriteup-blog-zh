# 机器人 CTF 先生——报道

> 原文：<https://infosecwriteups.com/tryhackme-mr-robot-ctf-writeup-ff0b3be5bd18?source=collection_archive---------0----------------------->

*TryHackMe 中一个名为* [*机器人先生*](https://tryhackme.com/room/mrrobot) *的房间的特写。*

![](img/8ac49facc4bd13f908161d685ea266d3.png)

## 关于 TryHackMe

[TryHackMe](http://tryhackme.com) 是一个学习网络安全的神奇平台，如果你是新手，不知道从哪里开始，这将是一笔惊人的财富。他们有这些房间，基本上是脆弱的机器，你可以部署和练习你的技能。TryHackMe 最棒的地方在于它非常实用。如果您是安全性新手，请务必尝试一下。

因此，在 TryHackMe 门户上部署该机器后，我们获得了一个访问该机器的 IP。每次部署时都会有所不同，所以您的`ROOM-IP` 可能与我的不同。

## nmap 扫描:

我们需要知道哪些服务在幕后运行，哪些端口是开放的。所以我们将使用一个叫做 **nmap 的工具。**

![](img/c5bc2c82bc0a622a7dcd6832b1442ae1.png)

拥有端口 80 和 443 表明我们有一个网站在运行，所以我们在浏览器上打开`http://10.10.71.122`和`https://10.10.71.122`。

![](img/a320502e68def95a494c0189f9656b31.png)

该网站是机器人先生主题网站。运行图片中提到的命令只是重定向到其他页面，这些页面有机器人先生电视节目的图像和视频。

因为我们有一个网站，我们想列举网站的目录，看看像登录页面，管理门户等存在与否。

**gobuster 扫描:**

因此，我们将使用一个名为 **gobuster** 的工具，它使用一个现有的可能的常用目录名称的单词列表，并尝试加载该单词列表中的每个目录名称，然后查看状态代码。(如果你使用的是 Kali 或 ParrotOS，那么你可以在`/usr/share/wordlists/dirbuster`找到这些词汇表)

![](img/e21d35f5fd402f1f8224af4501a2733c.png)

输出保存在`**directories.txt**`文件中

![](img/a2baf14190e6b537cbcdecb8fac2916f.png)

现在让我们看看状态代码为 200 的目录

![](img/faf13f43dbf24d52c5c4b3e071c070d4.png)

/自述文件

![](img/8709e31aacb857030157ea4ab38ed20d.png)

/许可证

![](img/9411aff243c08d07a7fbc0ebf06c0ac9.png)

/自述文件

![](img/67d3a1bc830d7e0005851bafdd9e5124.png)

/rdf(有意思..？)

![](img/4419e2d4b047c019f4597843e37cd252.png)

/wp-login(看起来像管理员登录页面)

![](img/f987815f5b03869760a7a8acad93d00a.png)

/机器人

头奖。打开`10.10.71.122/key-1–of-3.txt`

![](img/7dfe71cb1dbc3da89869642233af04dd.png)

这是我们的调号 1/3。

**关键一:被俘！**

现在我们来看看 fsociety.dic

![](img/393ebf0c703008a8bfe88b996582d1c8.png)

它看起来像一本字典。

让我们用这个字典对前面看到的登录页面进行字典攻击。

![](img/b6c6b2e2ccb945d35b283f336b3d5871.png)

我们得到错误:**无效的用户名。**

让我们试试 admin:admin 登录:

使用 BurpSuite 拦截登录请求数据包。

![](img/ee38767aa22a5baefbc20be925fd69c0.png)

用户名和密码字段分别由`log`和`pwd`表示。

## 使用 Hydra 执行字典攻击

字典应该是`fsocity.dic`。在这种情况下，我们从他们那里收到了一个文件，在其他情况下，我们会尝试使用 comman 用户名和密码。你可以在 https://github.com/danielmiessler/SecLists 找到这些以及所有其他的清单。

因此，首先我们将尝试找到以密码为常量的用户名，然后我们将使用找到的用户名来获取密码。

**用户名改变，密码不变**

![](img/38ac5ca7de7a6babffc502f59a0e552f.png)

我们得到的用户名是埃利奥特。

让我们尝试用 Elliot:test 登录

![](img/732de34f9be6330e0d51e8f5b697efa9.png)

我们得到错误:**您为用户名 Elliot 输入的密码不正确。**

**用户名不变，密码更改**

![](img/51fa86c21985a20dcd34b39f50cab489.png)

我们得到一个 9 位数的密码:********

使用`Elliot:*********`登录:

![](img/5def75e4fcffbb5df8c548f1462ed69b.png)

网站运行的是 WordPress 4.3.1。

现在我们需要打开一个反向外壳，所以让我们试着打开一个`php-reverse-shell`。卡莉和帕罗托斯已经拿到了。你所要做的就是`locate`它。

![](img/a637c79401cb98cb7d52472edd5d8ea4.png)

如果你没有卡利或 ParrotOS，你可以简单地谷歌一下，很容易找到它。

## **开借壳**

在 wp-admin 中，转到左侧导航栏，选择`Appearance → Editor`，然后选择右侧的`Archives (archive.php)`

![](img/268f578b60a4190b8138730f22eb736e.png)

一次，档案开放。在编辑部分粘贴`php-reverse-shell.php`

![](img/1bcfb533720a2d04178bbe337c9544a2.png)

现在我们必须编辑变量`IP`的值。我们必须将它设置为我们的 IP，这样当反向外壳打开时，它就知道要连接到哪个 IP。

![](img/0a2789445ca33ad1e696a5e03739b68c.png)

运行 **ifconfig** 命令

![](img/954f5da2f4e73e89bcd0a9e212283503.png)

编辑后的 php-reverse-shell.php 文件的外观片段

如果你愿意，你可以改变端口，只要记住你改变的端口。

点击更新，我们打开 netcat 听一下`port 1234`。

现在我们来开`archive.php`。检查它正在运行什么主题，并打开如下所示的主题。

![](img/a38313fb5aafa904dde4fe22b3aa61b9.png)

打开**http://10 . 10 . 162 . 7/WP-content/themes/twenty fifth/archive . PHP**

![](img/d654b4d640d4718502aadee8c607875e.png)

我们打开了一个反向外壳…耶！

![](img/12417f6a11aea6c1761c1975010eae35.png)![](img/4fd1777b22d4186abf7396352aa7209b.png)

我们无法读取 key-2-of-3.txt

我们需要用户`robot`来读取`key-2-of-3.txt`，但是我们仍然可以读取 password.raw-md5。让我们开始吧。

![](img/6edecfe9191160f9360a5171c2240524.png)

让我们用**开膛手约翰**来破解这个 MD5 散列

![](img/4a1e34c00c1dacefb6ad31596d42c657.png)

## 切换到用户机器人

![](img/5a9e033d7ba6e49a617baeed643e7c9c.png)

要切换用户，我们需要一个终端，我们不能使用 **/bin/sh -i** 打开终端

![](img/ad03eea7e1d2c11181a6243c002becd3.png)

所以我们用这种方法打开终端

![](img/0f8a712765b0ba82a2f29e6793b0f301.png)

打开 **key-2-of-3.txt**

**关键二:被俘！**

现在，为了捕获第三个标志，我们需要找到 root 用户，因此我们将执行权限提升，因此我们需要找出哪些程序的 SUID 至少为 4000

![](img/9a2c5fd23b644d47291a28d3937d9d47.png)

我们在这里找到了**nmap**

## 使用 nmap 的权限提升

> Nmap 设置了 SUID 位。很多时候，管理员将 SUID 位设置为 nmap，以便它可以用来有效地扫描网络，因为如果没有 root 权限运行它，所有的 nmap 扫描技术都不起作用。
> 
> 但是，nmap 旧版本中有一项功能，您可以在交互模式下运行 nmap，该功能允许您切换到 shell。如果 nmap 设置了 SUID 位，它将以 root 权限运行，我们可以通过它的交互模式访问“root”外壳。

![](img/c36f3fc332932ee8d973629c93b535d7.png)

**关键三:被俘！**

我在这个房间里度过了一段美好的时光，学到了很多东西。TryHackMe 有很多其他的房间，每个房间都不同，这也提供了一个巨大的学习机会。我会试着上传我感兴趣的房间的报道。当然，我希望你也能从这篇文章中学到一些东西。干杯！🍺

# 现在，让我无耻地要求你

在 [Github](https://github.com/harshitm98) 、 [Twitter](https://twitter.com/fake_batman_) 上关注我，在 [LinkedIn](https://linkedin.com/in/harshitm98) 上连接。

# 参考资料:

1.  打开 PHP-reverse-shell for WordPress([https://pentarot . com/exploit-WordPress-back door-theme-pages/](https://pentaroot.com/exploit-wordpress-backdoor-theme-pages/))
2.  使用 Python 打开终端([https://blog . ROP nop . com/upgrading-simple-shell-to-full-interactive-ttys/](https://blog.ropnop.com/upgrading-simple-shells-to-fully-interactive-ttys/))
3.  使用 nmap([https://payatu.com/guide-linux-privilege-escalation](https://payatu.com/guide-linux-privilege-escalation))的权限提升