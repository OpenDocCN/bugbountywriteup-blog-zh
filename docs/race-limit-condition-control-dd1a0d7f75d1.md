# 种族限制问题

> 原文：<https://infosecwriteups.com/race-limit-condition-control-dd1a0d7f75d1?source=collection_archive---------3----------------------->

为什么如此重要的控制是一个种族限制问题？

我在网上测试应用程序时发现，很多应用程序容易受到竞争限制攻击，没有任何 src 过滤器作为 ip 地址，或者限制注册帐户提交，或者登录尝试等..

例如，我在 hackerone.com 测试了注册表单，我在 7 月 5 日将此 PoC 发送给他们，他们以重复关闭，并向我解释说他们不关心此问题，并且根据 hist 用户政策，他们不喜欢使用验证码。

视频 PoC 展示了在没有注册用户表单的情况下利用竞赛限制是多么容易:

poc 插入新用户注册、验证确认电子邮件并验证用户，所有这些都是自动进行的:

影响

我们可以以多种形式施加影响:

*   注入无限的注册并在数据库中创建拒绝服务
*   改变参数，如投票或应用程序中的任何功能
*   使用线程增加攻击
*   用这个攻击竞争对手的公司、产品或应用程序
*   任何邪恶或恶意的方式诋毁网站或应用程序的性能

(竞争限制可用于暴力攻击、登录尝试或 API 端点攻击。对于所有这一切是如此重要的过滤和控制种族限制的所有方式。)

一个简单的固定:

同样的报告提交给其他公司，他们支付奖金并解决问题，在他的登录表单或注册表单中输入简单的验证码或验证码，然后就完成了。这很简单。

提示:如果你发现了一个种族限制并利用它，在公司范围内搜索并提交一份报告，如果你幸运，你已经支付了奖金$$$

黑客快乐！:) [Ak1T4](https://medium.com/u/c5b622272cd5?source=post_page-----dd1a0d7f75d1--------------------------------)

[](https://twitter.com/knowledge_2014) [## ak1t4 z3n (@knowledge_2014) |推特

### ak1t4 z3n 的最新推文(@knowledge_2014)。赏金猎人。黑客&和尚禅

twitter.com](https://twitter.com/knowledge_2014) [](https://hackerone.com/ak1t4) [## HackerOne 简介- ak1t4

### 怀特 4t Hack3r &禅宗和尚&赏金猎人-https://twitter.com/knowledge_2014

hackerone.com](https://hackerone.com/ak1t4)