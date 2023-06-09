# 我在 hackerone 上的第一笔奖金的故事。

> 原文：<https://infosecwriteups.com/story-of-my-first-cash-bounty-on-hackerone-acad282ae962?source=collection_archive---------0----------------------->

再次问候 bugbounty 社区！我的名字是韦丹特(在推特上也被称为[贝吉塔](https://twitter.com/_justYnot)😁)我是一名网络安全爱好者，也是一名有抱负的 bug 猎人:)今天我将与大家分享一个关于我最近发现的一个有趣 Bug 的故事，它帮助我在 [hackerone](https://www.hackerone.com/) 平台上获得了我的第一笔赏金。我肯定你会喜欢它的，所以别再废话了，让我们开始吧。

![](img/170fef3602dd45cfaa9482fec51650c1.png)

# 第 1 部分:背景故事

自从我开始学习 bug bounty 以来，我一直认为 Hackerone 是最难的平台，在那里很难找到有效的 bug。但在今年年初，我决定将更多的精力放在 Hackerone 平台上，并尝试解决至少一个 bug，是的，我做到了。在《H1》上花了近 3 个月的时间，我在国家排行榜[上排名第 53 位](https://twitter.com/_justYnot/status/1374941311120207874?s=20)，这真的增强了我的信心，所以我的下一个目标是获得我的第一笔奖金，所以我决定黑一个 bug 奖金计划。

# 第二部分:发现

所以我选择了一个范围内只有主 web 应用程序的目标。每次当我开始侦察这样的目标时，我都会使用 waybackurls 收集许多端点，但这次我决定尝试一些别的方法。我第一次使用 [Linkfinder](https://github.com/GerbenJavado/LinkFinder) 工具，命令是，

`**python linkfinder.py -i https://example.com -d**`

当执行完成时，我开始一个接一个地检查结果。有很多网址，大约 10 分钟后，一个网址引起了我的注意，它是这样的:

**https://www . example . com/image？id = somelinkwithouttp . com**

所以上面的网址让我很好奇，因为没有 http://或 https://。在看到这些接受 URL 作为参数的参数后，大多数 bug 猎人会选择 SSRF，我也是。我很快启动了 Burp collaborator，复制了一个有效载荷，没有预先考虑 http 或 https，我只是将它粘贴到 Id 参数中，并按 enter 键，期待 SSRF，但遗憾的是，我在 collaborator 中得到以下响应。

![](img/d49735b1884ecdf509e4fdb24ecee94d.png)

😔

我只收到 DNS 请求😔。在尝试了一些事情之后，我有了一个主意。我决定在我的 collaborator 有效负载中预先添加@符号(我不知道我是如何得到这个想法的，我只是自然而然地这么做了😂)然后我按了回车键，这一次令人惊讶的是我得到了下面的响应，

![](img/3b5c25df3abe8d45fd45ac7ab4f88c15.png)

😁

IP 是 AWS 的，所以我试图获取 AWS 元数据，我尝试了很多很多不同的技术(如重定向，DNS 重新绑定等。)几乎持续了 3-4 天，但没有任何效果。我决定无论如何都要报告这件事，两天后我得到了 triager 的回复，说我需要展示一下影响。此时我真的很沮丧。

# 第三部分:剥削

所以第二天，带着全新的想法，我决定再试一次。这一次，我试图用一些错误链接 SSRF。由于该参数是获取图像，我试图使用 brutelogic 的 XSS 概念链接。你猜怎么着？成功了！XSS 突然出现了😁。我使用了以下有效载荷:-

![](img/d1db7a2701fbf0a40a1ae2b6981f2551.png)

当 poc.svg 被成功获取时，我试图创建一个包含 XSS 有效载荷的 HTML 文件来窃取受害者的会话 cookies。我创建了那个文件，并使用 [ngrok](https://ngrok.com/) 在我的本地主机上托管它。所以为了测试这个漏洞，我在那个网站上创建了两个账户，并尝试使用那个有效载荷。成功了！！！我拿到了受害者的饼干😎。我使用了以下代码:-

![](img/b286bcd3db4c2e009fc5e8c4ccf0a33c.png)

😎

我很快向程序报告了这一情况，不到一天，报告就通过了审查，差不多 20 天后，我获得了我在[黑客龙](https://medium.com/u/6f816e37be2c?source=post_page-----acad282ae962--------------------------------)上的第一笔赏金！在发现和利用这个问题的过程中，我学到了很多新东西。如果你对这篇文章有任何疑问，你可以点击这里联系我

我希望你通过阅读这篇文章学到了一些新东西，如果你愿意，你可以买咖啡😇。感谢您阅读本文。下次见，再见，黑客快乐！