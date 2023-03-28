# 入侵内部(Tryhackme)

> 原文：<https://infosecwriteups.com/hacking-the-internal-tryhackme-42939bd3f5d6?source=collection_archive---------2----------------------->

嘿，伙计们，这个帖子是关于我最近在 Tryhackme 中提到的机器的，它确实是一个很好的侵入机器，因为它涵盖了真实世界的 pentest 示例，而且你也会了解到真实的 pentest 环境是什么样子的。务必记下这台机器里的一切。

![](img/eb25e9d93cacdede143865d9a8ae8d5d.png)

内部的

难度:难

内容:

1.  扫描和信息收集(Nmap、Nikto、Dirb、Wordpress)
2.  识别缺陷。
3.  强制登录页面(wpscan)。
4.  获得反向外壳。
5.  枚举计算机。
6.  获取 user.txt
7.  隧道技术
8.  权限提升

因为这就像一个真实的测试环境，我们必须遵循一定的规则。这里有一份简报可能会有所帮助。

![](img/7f460e6a8117cafb37a4599874f03c42.png)

交战规则

我们将对此机器进行详细扫描，即针对开放端口和服务的密集 Nmap 扫描。

还有一件事，确保编辑/etc/hosts 文件，IP 应该反映到 ***internal.thm***

![](img/8176f7f181fdff39ffc40f2304fc721b.png)

Nmap 扫描结果

如您所见，我们在端口 80 上运行 web 服务器，为了进一步列举，我们将使用 dirb 和 nikto。

目录扫描结果:

![](img/87f3461da9e5abe59bddc956bcb82d6f.png)

目录扫描结果

Nikto 扫描结果:

![](img/2e2031994b0e0b7e72a4cdd96e4e8e15.png)

Nikto 扫描结果

从 dirb 和 nikto 的扫描中没得到什么。有一个 wordpress 网站正在运行，我们可以执行 wpscan 来列举用户和易受攻击的插件。

![](img/d0cc16ad1232ad9211d2548e91793646.png)![](img/bf496a24eddebdc9669a2d3e12dc805f.png)

我们发现了一个用户管理员，我们可以使用 rockyou.txt 作为默认单词列表对登录页面进行暴力攻击。

![](img/ddfdda1253c1874b64a5a03fa57884cd.png)

成功执行暴力破解

我们唯一剩下的就是登录到网页，通过主题编辑器得到反向外壳。让我们首先使用凭据登录。

![](img/4454c30a25f3393677c800b90d494b09.png)

现在我们在，让我们编辑主题文件来获得反向外壳。跟我来🚀

进入外观->主题编辑器-> 404.php

由 [pentest monkey](https://github.com/pentestmonkey/php-reverse-shell) 用恶意 php 代码替换 404.php 的内容。

![](img/b2524e1177c6e088aff79c465b1a7763.png)

编辑 404.php

更新文件并访问以下 URL:

> http://internal . thm/blog/WP-content/themes/twenty seven/404 . PHP

![](img/aa9838312e5e660f96da5ef43d9d8077.png)

获取反向外壳

为了生成一个稳定的 shell，我们总是可以使用 python。

![](img/1642c1a6aa13f2e51e9198f767d462f3.png)

使用 python 获得稳定的外壳

所以要获得 user.txt，我们必须将我们的特权升级到 ***aubreanna*** 。尝试运行 linpeas 脚本或手动枚举会很好。我在/opt 目录中找到了这个文件，这是我们需要的文件，因为它包含了用户 ***aubreanna*** 的凭证。

![](img/8eb82a584e2f5f37dae413fec2fff196.png)

aubreanna 的证书

![](img/e0024c0d7d76b3fea745c6a213cd5be2.png)

获取 user.txt

和 user.txt 一起，我也得到了这个文件。让我给你看看它的内容。

![](img/dc7aa60eac3b512a26be10fb51e374c5.png)

端口 8080 上运行着一个内部 web 服务。在这里，我们可以使用 socat 在任何端口号监听它，这样我们就可以访问它。

socat 实用程序是两个独立数据通道之间双向数据传输的中继。

![](img/27cbacd9f6b6bef0d889169381ffb850.png)

从[这里](https://github.com/andrew-d/static-binaries/blob/master/binaries/linux/x86_64/socat)获取 socat 的二进制版本。

![](img/4d401e7f220c96bfc34eaeb1afd847f1.png)

看到它的工作。所以现在我们可以浏览网络服务器，看看我们是否能得到什么有趣的东西。

![](img/9dd6044c47aed8b4e908943f5ec22798.png)

登录页面

啊，又来了😧。我尝试了默认用户名/密码，但不起作用。暴力是我们唯一的选择。我将在这里使用九头蛇。

![](img/b15a530910ba02ae20ad9fa146dce911.png)

蛮力成功

所以登录之后，我们得想办法去拿东西。所以我谷歌了一下我们能对詹金斯做些什么。所以我找到了这个脚本控制台，它允许人们编写和执行 Groovy 脚本。

[](https://blog.pentesteracademy.com/abusing-jenkins-groovy-script-console-to-get-shell-98b951fa64a6) [## 滥用 Jenkins Groovy 脚本控制台获取 Shell

### Jenkins 是领先的开源自动化服务器，用于部署和自动化任何项目。

blog.pentesteracademy.com](https://blog.pentesteracademy.com/abusing-jenkins-groovy-script-console-to-get-shell-98b951fa64a6) ![](img/d74f9dbec961092bfe7a2e43a22e1667.png)

运行脚本，并在相应的端口上等待传入的连接。

![](img/5c38607b239f8df46c58f241e469ae0c.png)

反向外壳

枚举了一会儿，扫描了一下系统，得到了这个 note.txt，这个文件包含了 root 用户的密码。轻松右转😙

![](img/802163d8f636f53567791dc15a742418.png)![](img/0e584ed7b56288cf83468bef8e4e2138.png)

我希望你们能理解，随时给我发不和谐的短信

谢谢你😃快乐黑客💻