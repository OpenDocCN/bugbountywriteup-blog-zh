# TryHackMe 报道:走廊

> 原文：<https://infosecwriteups.com/tryhackme-writeup-corridor-2ee55095e3fe?source=collection_archive---------0----------------------->

写下描述求解廊道的步骤

挑战名称:[走廊](https://tryhackme.com/room/corridor)由[约翰·哈蒙德](https://tryhackme.com/p/JohnHammond)

![](img/0e1d7677d30860d676f51621c682d8c2.png)

走廊挑战

对于希望了解更多关于 IDOR 漏洞的个人来说，这是一个非常简单的挑战。

> *什么是* ***IDOR*** *？*

使用 HTTP 请求中指定的参数，web 服务器在执行用户请求时识别所请求的资源。要查找和访问某个资源，您需要知道直接对象引用。如果服务器端验证不充分，攻击者可能会在服务器访问资源时修改这些参数并访问内部实现对象的详细信息。此攻击利用了一个**不安全的直接对象引用(IDOR)** 漏洞。

> 你可以参考[这篇](/what-is-idor-vulnerability-and-how-does-it-affect-you-85431d10f8fb)文章来了解更多关于 IDOR 漏洞的信息。

现在让我们回到挑战。挑战描述中提供了完成挑战所需的大部分信息。

最初访问网站时，您会看到一些门。每扇门都有一个显示一些图像的可点击链接。但这里的关键是要注意浏览器的地址栏，那里显示的是网址。

当你点击每个门时，你可以看到以下格式的网址:http:// <ip>/</ip>

你可能已经注意到任务描述中提到了 HASH。取任意一个随机的字符串，试着确定它是什么类型的散列。在谷歌上搜索“哈希标识符”,你可以使用许多在线哈希标识符中的一个。

下一步是在确定 MD5 散列的类型是 MD5 之后解密 MD5 散列。使用在线 MD5 哈希破解程序。你会发现像 7、4、6 等数字。在 URL 包含的散列中使用。因此，请尝试确定随机散列中缺少哪个特殊数字。(注意:只需要破解 1 或 2 个哈希；其他的可以忽略。)只需考虑哪个数字可能相对唯一。

当提到 IDOR 漏洞时，像-1，0，1 这样的数字通常是唯一的，因为管理或测试帐户经常出现在这些端点上。只需通过获取这些单个整数的 MD5 散列(https://<ip>/MD5-string-of-[-1，0，1])来尝试访问这些端点。你会得到你的旗帜。</ip>

希望你能解决阅读这个问题。

感谢您的阅读。知识就是力量，所以不断获取！😈

在 GitHub 上关注我！

## 来自 Infosec 的报道:Infosec 每天都有很多内容，很难跟上。[加入我们的每周简讯](https://weekly.infosecwriteups.com/)以 5 篇文章、4 条线索、3 个视频、2 个 GitHub Repos 和工具以及 1 个工作提醒的形式免费获取所有最新的 Infosec 趋势！