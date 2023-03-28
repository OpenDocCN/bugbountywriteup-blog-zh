# 如何阻止超过 2 亿用户使用谷歌服务

> 原文：<https://infosecwriteups.com/how-to-prevent-more-than-200-million-users-from-using-google-services-136b3b8e221f?source=collection_archive---------2----------------------->

嗨，伙计们，

在谷歌搜索时，我发现谷歌拥有这个域名 appsheet.com 你可以在这里查看[https://whois.com/whois/appsheet.com](https://whois.com/whois/appsheet.com)
所以我开始搜索它的漏洞，所以我发现了一些漏洞，它们可以联合在一起滥用对公司有害的风险，所以让我们开始
第一个漏洞让我们先看看这个概念证明，然后完成

我注意到，在 https://community.appsheet.com[注册时，你应该首先输入你的个人信息，如电子邮件，姓名，用户名，密码和投资组合网址，所以在输入你的信息并注册后，你的信息直接输入到数据库中，这不是注册新帐户的正确方法，正确的方法是首先验证你的帐户，然后你的个人数据作为新用户进入数据库， 所以第一个错误是拒绝服务，因为你可以通过简单地使用电子邮件来阻止用户注册，之后他们会收到验证消息，因为他们没有请求它，他们会忽略它，几个小时后验证电子邮件将过期，之后根本没有办法注册这个帐户，如果电子邮件的所有者试图注册，他会发现消息告诉他(电子邮件已经被 采取)另一种情况是，电子邮件的所有者决定在邮件过期之前点击验证链接并激活帐户，因此现在他的帐户处于攻击者的控制之下，因为他为受害者帐户分配了用户名和密码](https://community.appsheet.com)

现在，我们在第一阶段，让我们进入下一个阶段
作为第一个错误的原因，您可以阻止除 Gmail 用户之外的所有用户注册，他们有一种方法可以注册到 Google，但是还有第二个错误，让我们看看第二个概念验证并完成(您可以将视频速度提高 1.25 倍)

如您所见，您可以向使用谷歌电子邮件注册的用户分配姓名、用户名和应用程序组合 URL，因此，您可以在名称字段(如欢迎消息)和组合 URL 字段中输入钓鱼链接或任何恶意链接，因为新用户会认为这些链接来自谷歌公司，但事实并非如此

现在让我们进入最后阶段

注册表中的速率限制配置错误，开发者给你注册 300 个新帐户的可能性，然后禁止你注册几个小时，注册新帐户你应该发送三个请求，所以我写了这个 python 脚本来完成这项工作

现在让我们来看看攻击场景，做一个小计算:
攻击者首先要做的是收集数据泄漏中的所有电子邮件，然后您可以使用我的脚本并编辑它，使请求通过 tor 代理或任何工具进行 IP 轮换，在大约 3 分钟内注册 300 个新帐户，然后用这种方法更改 IP，您可以在一小时内阻止 6000 个用户使用该子域中的所有服务，而在一天内您 可以防止 6000 个用户在一个小时*一天 24 小时== 108000 个用户使用这个 sub，然后如果你是一名大学生 azure 给你 100 美元使用 2 个 VPS 你可以收集你的朋友的帐户让我们说至少 30 个帐户，所以现在除了你的帐户之外，你还有(31 个帐户* 2 个 VPS * 108000 个用户在一天* 30 天在一个月== 200880000 个用户每个月)所以你可以增加用户的数量

如果你在这篇文章中有不明白的地方，或者需要任何帮助，你可以在 Twitter 或 Linkedin 上给我发消息

感谢阅读

## 保持联系

[**Linkedin**](https://www.linkedin.com/in/omar-1-hashem)|**Youtube**|[**Twitter**](https://twitter.com/OmarHashem666)

## 来自 Infosec 的报道:Infosec 每天都有很多内容，很难跟上。[加入我们的每周简讯](https://weekly.infosecwriteups.com/)以 5 篇文章、4 个线程、3 个视频、2 个 Github Repos 和工具以及 1 个工作提醒的形式免费获取所有最新的 Infosec 趋势！