# IDOR 导致隐私泄露

> 原文：<https://infosecwriteups.com/idor-leads-to-leak-private-details-866563365490?source=collection_archive---------2----------------------->

祝各位读者圣诞快乐，新年快乐。愿这一年带给我们的无非是爱、快乐、幸福、P1、P2 虫子、礼物和笑声😊😊。所以让我们开始吧。

**IDOR 是什么？**

IDOR 漏洞被称为不安全的直接对象引用。

不安全的直接对象引用(IDOR)是一种访问控制漏洞，当应用程序使用用户提供的输入直接访问对象时，就会出现这种漏洞。

让我们假设目标程序是:https://www.program.com

我已经开始侦察了。在这里，我发现它没有很大的范围。它有一个非常少的领域。

# 小提示:当我发现这么小范围的目标时我该怎么办！！

> 1 >使用 Seclists github 库进行模糊化:【https://github.com/danielmiessler/SecLists 
> 
> *2 >捕获&检查所有请求手动在 burpsuit*

如上所述，我已经开始用 Seclists github 知识库的单词列表进行模糊处理，并在目标网站上创建了帐户，并在 burpsuit 中捕获所有请求。然后我开始分析所有的请求，当我处理这些请求时，我知道有一个端点

***/端点/id/信息***

看起来很有趣😎😎。我立刻向入侵者发送了这个请求。

在这个端点中，我开始在 burpsuit 中玩 id。在创建帐户目标程序的时候，给我分配一个唯一的 id。所以我最后的路看起来很像

[***https://target.com/endpoint/xxxx/info***](https://target.com/app/v1/subdomains/xxxx/info)

我在入侵者& booom 的有效载荷中随机添加了一些单词表💥💥💥。

它带有其他用户的详细信息，如 **ID、auth_details、Org_name、私有子域信息。**

我立刻向目标项目报告了这个问题&他们已经发现了这个问题，并给了我几块钱作为感谢。

## 时间线:

## 2021 年 6 月 5 日:据报道

## 2021 年 7 月 6 日:状态-已接受

## 2021 年 6 月 20 日:获得奖励

**结论:狩猎期间不要错过任何终点**

**跟随:**

> **推特**:[**https://twitter.com/OwnRadius**](https://twitter.com/OwnRadius)

非常感谢您的阅读…