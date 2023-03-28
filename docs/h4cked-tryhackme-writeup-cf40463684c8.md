# h4cked Tryhackme 报道

> 原文：<https://infosecwriteups.com/h4cked-tryhackme-writeup-cf40463684c8?source=collection_archive---------6----------------------->

**作者 Shamsher khan 这是一篇关于 Tryhackme room“被黑”的文章**

[![](img/ae8179e491c51ff0b9619c0e7f0c571d.png)](https://www.tryhackme.com/room/h4cked)

【https://www.tryhackme.com/room/h4cked 号

**房间链接:**[https://www.tryhackme.com/room/h4cked](https://www.tryhackme.com/room/h4cked)
**注:此房免费**

**问题 1:** 攻击者试图登录特定的服务。这是什么服务？

![](img/9b764224c12e26e7d8e175f78a57f592.png)

> **答案:FTP**

**问题 2:**Van Hauser 有一个非常流行的工具，可以用来暴力破解一系列服务。这个工具叫什么名字？

![](img/10abcc2c9dce20c37e998a98e0093f27.png)

> **答案:九头蛇**

**问题 3:** 攻击者试图用特定的用户名登录。用户名是什么？

![](img/98bbd2fead1608f6f89b8d2bf0ebacb1.png)![](img/a59cdf82c596fac063d8ae9a74073bd5.png)

> **答案:珍妮**

**问 4:** 用户的密码是什么？

![](img/16bbdc8722076245cc332b98b27cd7da.png)![](img/05e143de6fa17862225b101f27da8c69.png)

**问 5:** 攻击者登录后当前的 FTP 工作目录是什么？

![](img/06dce4030e02ccb34a907cd81c226001.png)

> **答案:/var/www/html**

**问 6:** 攻击者上传了一个后门。后门的文件名是什么？

![](img/837408cec8c4c84d51aec14ed4f7570d.png)

> **答案:shell.php**

**问 7:** 后门可以从特定的 URL 下载，因为它位于上传的文件中。完整网址是什么？

![](img/62acedd8024ae0b4c558fd32a983cad7.png)![](img/44c8c2fa2cbcd246f3795dc455a6e5b3.png)

> **回答:**[**http://pentestmonkey.net/tools/php-reverse-shell**](http://pentestmonkey.net/tools/php-reverse-shell)

**问题 8:** 攻击者在得到一个逆向 shell 后手动执行了哪个命令？

![](img/20010f667a60079829fb7c85a0ef0de9.png)

> **答案:whoami**

**问 9:** 电脑的主机名是什么？

![](img/300ef4d9f2e73af0f113da6e14fcc4f9.png)

> **答案:wir3**

问题 10: 攻击者执行了哪个命令来生成一个新的 TTY shell？

![](img/b88325c5914f495a6ee7695315ceefc5.png)

> **答案:python 3-c ' import pty；pty.spawn("/bin/bash")'**

**问题 11:** 执行了哪个命令来获得根 shell？

![](img/76531221db6c6587e758914e45610cd8.png)

> **答案:须藤苏**

**问题 11:** 攻击者从 GitHub 下载了一些东西。GitHub 项目的名字是什么？

![](img/37e28e1714f616af13e49d03a4352273.png)

> **答案:爬虫**

问题 12: 这个项目可以用来在系统上安装一个秘密后门。很难察觉。这种类型的后门叫什么？

> **答案:rootkit**

部署机器。

攻击者已经更改了用户的密码！能否复制攻击者的步骤，读取 flag.txt？该标志位于/root/爬虫目录中。记住，你可以随时回头看。如有必要，pcap 文件。祝你好运！

在 FTP 服务上运行 Hydra(或任何类似的工具)。攻击者可能没有选择复杂的密码。如果你使用一个普通的单词表，你可能会很幸运。

![](img/eaad47b3c28451a4853ffa8f90fc0078.png)

我们得到了登录 ftp 服务器的密码

![](img/954de14d21372841ba1132b8d60d586d.png)

用我们的 tryhackme ip 地址上传我们的新 shell.php

![](img/338d7ea479f15b861abb806086928a6a.png)![](img/ed4c4ce12a0678c5789384644af7b898.png)

现在在 kali 上启动 netcat 监听器

```
nc -lvp 4444
```

并访问[http://10 . 10 . 82 . 175/shell . PHP](http://10.10.82.175/shell.php)

![](img/1240bd7b95be7873a342f75dea593f12.png)![](img/4807f34a9f0cc16f306cd340c87f4473.png)

我们得到 revershell

**升级外壳**

```
python3 -c 'import pty; pty.spawn("/bin/bash")'
```

![](img/2efa1e12a2173378aa1e0c3782c5b573.png)

嘣！我们得到了根外壳让我们得到标志. txt

![](img/393c8eba9f88721be56e82aa3e403179.png)

你可以在:
**LinkedIn:-**[https://www.linkedin.com/in/shamsher-khan-651a35162/](https://www.linkedin.com/in/shamsher-khan-651a35162/)
**Twitter:-**[https://twitter.com/shamsherkhannn](https://twitter.com/shamsherkhannn)
**Tryhackme:-**[https://tryhackme.com/p/Shamsher](https://tryhackme.com/p/Shamsher)

[![](img/09e5bbba06c7688a702aeec8570d243c.png)](https://tryhackme.com/p/Shamsher)

如需更多演练，请在出发前继续关注…
…

## [点击这里加入电报](https://t.me/tryhackme_writeups)

[![](img/149e778f03405fe40fb89bb9dbc5034d.png)](https://t.me/tryhackme_writeups)

访问我的其他演练:-

感谢您花时间阅读我的演练。如果您觉得它有帮助，请点击👏按钮👏(高达 40 倍)并分享
它来帮助其他有类似兴趣的人！+随时欢迎反馈！