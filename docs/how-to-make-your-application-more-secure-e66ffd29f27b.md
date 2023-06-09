# 如何为应用开发者开发更安全的应用？

> 原文：<https://infosecwriteups.com/how-to-make-your-application-more-secure-e66ffd29f27b?source=collection_archive---------0----------------------->

银行应用程序的安全性至关重要，使用当前的银行移动应用程序只会让人感到不安全。银行应用程序提供的安全性与黑客攻击这些应用程序的回报相比实在是微不足道。所以我决定发表这篇文章，其中包括我设计的三个要点，以提高应用程序的安全性，任何开发人员都可以使用这些技巧来使他们的应用程序更加安全。这三点是增强安全性的概念验证，同时几乎不影响用户的易用性。

![](img/b984fdd6a088f221ba452f6e12c43082.png)

信贷-应用投资 iv

# 头脑风暴

因此，首先我们需要了解项目的要求，即通过对应用程序进行非常轻微的更改来增强应用程序的安全性，以便用户体验不会被大量修改，但安全性方面仍会得到多倍增强。

为此，我们需要了解大多数消费者可以获得的现有技术的范围，无论是农村农民还是城市商人，以及我们如何使用它来增加额外的安全功能。

# 三步过程

我想出了三点，乍一看似乎没什么大不了的，我们大多数人都默认了这一点，但请记住，支付应用程序的这些功能不仅适用于技术极客，也适用于几乎不会操作智能手机的人。

## 想法 1 -三层安全(在任何交易开始时)

这里的想法是，我试图整合三层安全，而不是使用典型的一个步骤，只需要我们输入一个 4 位数的 pin。

![](img/28ed5b599abcfba8241b5abe5fc1e74f.png)

想法 1 -三层安全

无论何时启动交易，都需要执行这些步骤。因此，我们可以确保发起交易的人是合法的人，因为现在我们已经可以从手机上访问我们的整个银行账户，我们需要确保我们的账户是安全的，即使它们在我们不信任的人手中。

## 想法 2 -推进动态口令(在动态口令验证过程中)

在这里，我试图通过设计一种新型的 OTP 验证过程来提高安全级别。

![](img/ff0e2ee3de6153370d694b18d4aaa1d3.png)

想法 2 -推进检察官办公室

在此过程中，未知方的盗窃和交易可以完全停止，因为我们已经使他们很难开始交易过程，并且在引入高级 OTP 检查后，有人绕过这些安全检查的难度会成倍增加。

## 想法 3 -网格事务(离线事务时的身份验证)

互联网在印度的大部分地区仍然不可用，至少不是高速互联网，为此，我们看到谷歌引入了离线支付系统来扩大其覆盖范围，但迫切需要加强正在发生的离线交易的安全性。

![](img/9ba9530e9d509f78760637d6794df597.png)

想法 3 -网格交易

以这种方式，离线交易过程可以变得容易，因为使用它的人可以在他们需要的任何时候生成这些数字组，并且增强了安全性。为了创建这些密钥，他们需要通过各种安全检查以在进行交易之前正确地认证他们自己。

# 准备，就位，安全！

我希望所有的开发人员都关注他们应用程序的安全性，在设计应用程序时将安全性放在第一位，而不是把它当作一个事后的想法。需要更多信息的开发者可以和我联系，我会给他们一个详细的解释，告诉他们如何实现这些功能，并根据他们的需求进行调整，让世界变得更加美好和安全。

如果你喜欢，请鼓掌让我们合作吧。获取、设置、破解！

网址:【aditya12anand.com】T2|捐赠:【paypal.me/aditya12anand】T4

电报:[https://t.me/aditya12anand](https://t.me/aditya12anand)

推特:[twitter.com/aditya12anand](https://twitter.com/aditya12anand?source=post_page---------------------------)

领英:[linkedin.com/in/aditya12anand/](https://www.linkedin.com/in/aditya12anand/?source=post_page---------------------------)

电子邮件:aditya12anand@protonmail.com