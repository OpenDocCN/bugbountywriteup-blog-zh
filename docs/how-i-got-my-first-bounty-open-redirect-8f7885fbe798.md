# 我是如何得到第一笔赏金的。(打开重定向)

> 原文：<https://infosecwriteups.com/how-i-got-my-first-bounty-open-redirect-8f7885fbe798?source=collection_archive---------3----------------------->

9 月 16 日，我在某个网站搜索一个 bug，姑且称之为“buggyweb.com”。我点击并访问了网站上所有可用的链接。玩了一段时间后，我收集了一些关于它的信息。所以我决定在那个网站上测试开放重定向。

我在 url 中查找类似“URL、路径、重定向等”的参数。过了一段时间，我出现在那个网站的支付页面，看起来像这个
"buggyweb.com/order/checkout.php？redirect = 0/shop URL = buggy web . com/someting "

起初，我试图改变“shopurl ”,但我运气不好。所以我试着编码网址，再试一次，但没有运气。过了一段时间，我注意到 URL 中有一个重定向参数，所以我试图将重定向参数的值改为 1，我希望我会成功，但运气不好。所以我又试了一次，将重定向参数值改为 true，然后嘣！这是一次成功。

这是我的第一个错误，所以我很兴奋，所以只想立即报告。所以我录下了视频，过了一段时间，我收到一封邮件，说这是有效的，我获得了奖金。

非常感谢你阅读这篇文章。这是我的第一个博客，所以处理我的错误。