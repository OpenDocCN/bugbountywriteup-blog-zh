# facebook 事件中不可移除的客人——脸书(Meta) bug bounty

> 原文：<https://infosecwriteups.com/irremovable-guest-in-facebook-event-facebook-bug-bounty-e10e03c98cd5?source=collection_archive---------2----------------------->

大家好，我是来自尼泊尔布特瓦尔的 Rajiv Gyawali。这是我在 facebook 上发现的一个故事。

**故事**:我正在阅读 facebook bug bounty 的文章，其中写道无法从 facebook 事件中删除成员，当时的情况是“受邀用户阻止事件的所有者”，我起初测试了相同的场景，但无法重现，后来我去了我的一个测试组，在正常场景中创建了一个事件(我起初认为这是一个正常场景)，并试图从该事件中删除一个成员，我无法从该组中删除该成员，我对这种想法感到高兴，就像…哦，错误…事情:)

我在几个小组中测试了这个问题，有些失望，我无法在一些小组中重现它，我非常不确定是否要报告这个问题，因为有 fb 团队不重现它的风险，但我还是报告了。

正如所料，facebook 团队无法重现该问题，我自己对重现 bug 的场景感到困惑(这是 facebook 安全:D 的公平回复)，我再次从零开始测试该问题，并…最终找出重现该问题所需的场景…大松一口气:P :P

**实际上，要重现该问题，需要以下场景:**

*   当事件的所有者是其 facebook 页面所在群组的成员时，他不能从事件中删除来宾。

因此，我向他们发送了重现该问题所需的附加信息，他们能够重现该问题(PoC:【https://youtu.be/MhC97tJxk0Q】T4)

**时间线:**

> 报告已发送—2021 年 9 月 17 日
> 
> facebook 的初步回应——2021 年 9 月 22 日(无法复制)
> 
> 发送附加信息和场景—2021 年 9 月 23 日
> 
> 转载—2021 年 9 月 24 日
> 
> 审判—2021 年 9 月 29 日
> 
> 赏金奖励—2021 年 10 月 7 日
> 
> 已确定和确认—11 月 21 日

然而，这个问题在 FB4A 中仍然存在，甚至可能存在，但 facebook 团队表示，他们不接受 FB4A 中的这种问题。

**感谢您阅读到最后，我们在这里连线** [**拉吉夫·加瓦利**](https://www.facebook.com/rajiv.gyawali.5)

*来自 Infosec 的报道:Infosec 上每天都会出现很多难以跟上的内容。* [***加入我们的每周简讯***](https://weekly.infosecwriteups.com/) *以 5 篇文章、4 个线程、3 个视频、2 个 Github Repos 和工具以及 1 个工作提醒的形式免费获取所有最新的 Infosec 趋势！*