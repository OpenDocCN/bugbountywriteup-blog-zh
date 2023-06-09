# 通过优惠券打破商业逻辑——我的第一个有效 Bug 赏金的故事

> 原文：<https://infosecwriteups.com/breaking-business-logic-via-coupons-the-story-of-my-1st-valid-bug-bounty-89c30ff214dc?source=collection_archive---------0----------------------->

我在一个私人程序上发现的第一个有效漏洞的故事——

在这篇文章中，我将分享:

1.  **我是如何开始**信息安全和 bug bounty 的，我的挣扎和矛盾以及我从中学到了什么。
2.  在学习了一些东西后，我不得不采用一种**不同的方法**。
3.  然后我会进一步讨论我是如何发现我的第一个有效 bug 的，**发现 Bug。**
4.  我将以**一些从发现**中得到的收获或教训来结束我的演讲。

# 我是如何开始的

2015 年听说了 bug bounty，我 [***采访了我的一个好朋友***](https://www.editweaks.com/2015/02/exclusive-interview-with-laxman-meet.html) ，后来 2017 年对信息安全产生了兴趣。

我从 2017 年开始学习 Infosec，以及脸书和谷歌等公共项目的漏洞奖金，但在整个学习阶段，我非常“不一致”。这可能是因为我把它作为一种爱好，也就是说，只有当我从搜索引擎优化顾问、数字营销人员和信息企业家的主要工作中解脱出来的时候。

所以我最初开始在脸书上打猎， [**拉克斯曼**](https://thezerohack.com/) **和** [**Phwd**](http://twitter.com/phwd) 是我的灵感，他们从一开始就很有帮助，我也认识了这个领域里一些更牛逼的人。

我读了一些电子书，试图发现和报告错误，但没有成功，事实是我开始的那些公共程序是最具挑战性和最难破解的；因为事实上，世界上大多数最好的安全研究人员/怀特哈特黑客已经在测试它们，并发现了大多数漏洞。

随着时间的推移，我的报告总是以“不适用”、“信息丰富”或“重复”而告终。每次回复后，我经常会休息很久。

我还注意到，新手(有时甚至是专家或 1337)也会有这种挫败感。

我对有效 bug 知之甚少或一无所知，直到我遇到了一个代号为 [**F007573P**](https://twitter.com/_sawzeeyy) 的朋友，他总是在那里回复我关于在 web 应用程序中寻找 bug 的问题。

# 不同的方法

在这一点上，我觉得有必要在再次寻找困难的公共项目之前积累知识。一些好朋友和信息安全社区的一些推文建议安全研究人员也可以尝试不在 bug bounty 平台上的私人程序。

哇，也许我可以在其他地方试试我的小知识。所以我决定搬出去，尝试一种不同的方法——我想到了**逻辑缺陷**，这是我目前最喜欢的方法。

我决定继续调查 [***违反商业逻辑***](https://owasp.org/www-community/vulnerabilities/Business_logic_vulnerability) 的问题，直到我更有知识或足够熟练去捕捉更严重的更高技术错误(在野外)。

# 寻找 BUG

我们将假设私人程序的网站被称为编辑

这个 bug 存在于处理优惠券的端点，这些优惠券只能一次性使用。

根据我收到的邮件，当你注册时，你会得到一张优惠券，目的是鼓励顾客购买东西，优惠券将在几个小时后到期，我最初忽略了这张优惠券。

**两周后**

我想在这个网站上购物，所以我在 2 周后使用了优惠券，优惠券仍然有效，这引发了我的好奇心，我决定深入测试一下。

10 分钟后，我意识到我可以想用多少次优惠券就用多少次。

有了这个，我就可以欺骗被篡改的支付系统，这可能会导致公司的财务损失。

**概念验证**

要求:新用户的新帐户和一次性使用的优惠券。

1.登录到修订的帐户

2.复制您的优惠券代码

让我们假设优惠券代码是> > REDCOP300

3.我在不同的标签上打开了每一件我想买的东西

4.在我给每个标签下订单之前，在每个标签上应用代码

这将降低每个标签上每个项目的价格。

5.在我的一个订单中，我点击了结账，选择了 PayPal 作为结账选项，并在 PayPal 网站上为订单付款。

在这一点上，我知道我可以为其他标签上的其他项目下订单(我已经在它们中应用了相同的折扣)，因为 PayPal checkout 是外部编辑的，编辑的网站不能再控制价格了。

我举报了。

团队工作人员回答——我只在一件商品上试过，我没有充分证明我是否可以用相同的优惠券在其他标签上下单，因此他们不确定付款是否会成功。

我的回答是——我回答说再次下订单会花费我一些钱，但我接受了挑战，继续执行步骤 1-5，并使用“一次性使用”优惠券为其他标签中的许多商品付款。

**影响，**

示例:

价值 2000 美元的商品我可以得到 100 美元的折扣

价值 3000 美元的商品可以获得 300 美元的折扣

价值 5000 美元的商品可获得 500 美元的折扣

我可以用一张优惠券统治他们

几个月后，他们回复说安全小组已经调查过了，他们对我的报告表示感谢，并奖励了我奖金。

## 报告时间表:

报告已发送—2020 年 2 月 9 日，

团队成员回应——2020 年 2 月 10 日——他们怀疑这个 bug 是否有效。然后，我提出了新的概念，以显示充分利用。

经过几周和几个月的延迟沟通，我放弃了这份报告——2020 年 3 月 28 日

团队工作人员回应 bug 有效—4 月 26 日，奖金奖励 2020 年 6 月

# 外卖:

**高级部分可能有 Bug**——这一点怎么强调都不为过，我看到研究人员说了很多，这是真的。一个网站的免费部分通常更安全或者已经被修复，但是当你付费访问研究人员不常去的付费部分时，就有更高的几率在那里发现漏洞。

**总是练习耐心:**我非常想找到一个有效的 bug，但是我等了很久才努力实现。我甚至发现并向一些随机的公司报告了错误，他们默默地修复了他们的问题，但甚至没有回复我说谢谢，但这是另一天的故事:)

其次，即使你发现了一个有效的漏洞并报告了它，这些公司也有他们的做事方式。伤检分类和缺陷修复会经历各种各样的过程，这意味着你必须等待或者在等待的时候做其他事情。

**始终检查端点在不同选项卡中的反应** s —当您在浏览器上打开多个选项卡并执行动作 A，然后在另一个选项卡上执行动作 B 时，动作 A 是否会在其他选项卡中反映出来？或者，动作 B 是否阻止动作 A 执行您在其他单独的选项卡中执行的操作，或者您是否可以执行这些操作而不受影响。

就这样，我作为信息安全和 bug bounty 爱好者的旅程正式开始了…

感谢 [**F007573P**](https://twitter.com/_sawzeeyy) 帮我校对&这篇评论