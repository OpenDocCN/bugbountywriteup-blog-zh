# 智能手机监控和跟踪技术

> 原文：<https://infosecwriteups.com/smartphone-surveillance-techniques-f9e206c5c456?source=collection_archive---------0----------------------->

## 了解威胁、指数和防护

![](img/e939e247e34ef1b7705b737cc657b895.png)

> 以下文章融合了各种关于智能手机监控/安全的公共领域文章的实质性总结和选择性汇编。所有的参考文献都在文章的末尾注明了。

> "“启蒙运动”发现了自由，也创造了纪律."

*――米歇尔·福柯，规训与惩罚:监狱的诞生*

# 智能手机如何被监听？

智能手机在我们的生活中扮演着越来越重要的角色。它们无处不在，因为我们几乎到哪里都带着它们，并把敏感的、有时非常私人的信息托付给它们。我们用它们来执行日常任务，从与家人沟通、在社交媒体应用上社交，到在银行应用上跟踪我们的健康和管理我们的财务。

但它也是一个带有摄像头、全球定位系统和麦克风的设备，你可以随时随身携带。不幸的是，手机不是为隐私和安全而设计的。把这个硬件变成一个监控工具，比你想象的要简单有效得多。它们不仅在保护您的通信方面表现不佳，还会让您面临新的监控风险。

> **在治理实践中，监视是一种传授技术，从这个意义上说，监视总是一种权力的行使。它是对寻求控制和约束的个人的外部影响，带来了被利用和侵犯隐私的风险。**

在这里，我们将描述智能手机可以帮助监控和破坏用户隐私的所有方式。因此，当我们试图检查智能手机监控的每个方面时，请做好深入阅读的准备。

## **1。移动信号跟踪—手机发射塔**

![](img/f91e2365f5451c17606e73e593e78acc.png)

***工作原理***

移动网络/ SIM 卡运营商自己有能力拦截和记录所有关于访问网站的数据，谁在何时给谁打电话或发短信，以及他们说了什么。

您的 Wi-Fi 互联网提供商提供 [*DNS*](https://dyn.com/blog/dns-why-its-important-how-it-works/) 作为您服务的一部分，这意味着您的提供商也可以记录您的 DNS 流量——本质上，记录您的整个浏览历史。

任何移动网络运营商也可以在电话开机并注册到网络时精确计算特定用户电话的位置。这种能力叫做 [*三角测量*](https://wrongfulconvictionsblog.org/2012/06/01/cell-tower-triangulation-how-it-works/) 。

运营商可以做到这一点的一种方法是监控不同塔从特定移动电话观察到的信号强度，然后根据观察结果计算出该电话必须位于何处。运营商计算用户位置的准确度各不相同，这取决于许多因素，包括运营商使用的技术(2G/3G/LTE)和附近的手机信号发射塔数量。

通常只有移动运营商本身可以执行这种跟踪，尽管这些信息可能会通过官方或非正式的安排提供给当地或外国政府。在某些情况下，外国政府也曾入侵移动运营商的系统，以秘密获取用户数据。此外，黄貂鱼(解释如下)可以被你身边的人用来拦截通信数据包。

> 乌克兰政府使用了一个转储塔，列出了所有在反政府抗议中使用手机的人的名单。

另一种相关的监视请求被称为“塔转储”；在这种情况下，政府要求移动运营商提供在特定时间出现在特定区域的所有移动设备的列表。通常，执法机构(lea)使用塔转储来调查犯罪，或建立犯罪关系。

***预防措施***

只要你的手机处于开机状态，并向运营商的网络发送信号，就没有办法“隐藏”这种跟踪。不被发现的最好方法是什么？不要将它连接到网络或任何其他计算机，这种做法被称为*气隙*。然而，在一个几乎每台机器都连接到互联网的世界里，这并不容易。

*然而，对于超敏感的文件和任务*——比如存储比特币或使用机密蓝图——完全离线工作的不便是合理的，尽管有这么多麻烦。对于这些情况，高度谨慎者依赖于**法拉第笼或袋**。这些本质上是金属内衬的手机壳，可以阻挡所有的无线电频率。没有信号可以进出。这些很容易在亚马逊上买到，价格相对便宜。

然而，虽然笼子或袋子可能会阻止你的手机暴露其位置，但如果它已经被间谍软件攻击过，它并不能真正阻止它进行间谍活动——在它被封锁之前。

> 最安全的做法是假设传统的通话和短信没有被窃听或录音。

当您使用安全通信应用程序进行通信(无论是通过语音还是文本)时，情况可能会有所不同，因为这些应用程序可以应用端到端加密(E2EE)来保护您的对话。这类具有可靠的 E2EE 实现和强大的反取证能力的 app 可以提供更有意义的保护。

使用此类应用程序获得的保护级别在很大程度上取决于您使用的应用程序及其工作方式。一个重要的问题是，应用程序开发人员是否有办法撤销或绕过加密，以及他们正在收集的所有聊天元数据。

> **我们推荐** [**Signal**](https://signal.org/) **，一款高度加密的聊天和语音/视频通话 app，由 Signal Foundation 开发。**

## 2.移动信号跟踪—IMSI·凯切

![](img/e438be46053a45fcc3dcecfb7548045b.png)

政府还可以直接用**手机基站模拟器**窥探移动通信，这是一种便携式设备，可以产生假的手机信号塔来“捕捉”特定用户的手机，并检测他们的物理存在和/或窥探他们的通信，有时也被称为 IMSI 捕手或黄貂鱼。然而，IMSI 捕捉器需要被带到特定的位置，以便在该位置找到或监控移动设备。

IMSI 捕手能够确定其附近移动电话的 IMSI 号码，这是其名称来源的商标能力。使用 IMSI，他们可以识别网络上的移动流量，并针对流量进行拦截和分析。

一旦 IMSI 捕捉器完成了到移动设备的连接，它就可以通过发送空的相邻小区塔列表或具有移动设备不可用的相邻基站的列表，来试图阻止该移动设备连接到另一个合法基站(网络塔站)。

根据爱德华·斯诺登泄露的文件，一些先进的 IMSI 捕手甚至可以在手机关机时定位手机。这是通过无线发送命令来实现的，通过 IMSI 捕捉器，到手机的基带芯片，假装关机并保持开机。然后，电话可以被指示只保持麦克风开着，以便偷听谈话，或者定期发送定位脉冲。

> **手机仍处于开机状态的唯一提示是，即使它已经关机，如果它仍然感觉温暖，则表明基带处理器仍在运行。**

这种担忧导致一些人在进行非常敏感的谈话时，会从他们的设备中取出电池。

***工作原理***

对移动网络的攻击包括破解网络加密、被动网络拦截和主动网络拦截。IMSI 捕捉器属于最后一类，通过充当收发器(同时发射和接收)来主动干扰移动电话和基站之间的通信。IMSI 捕手使用“中间人”攻击，通过同时向真实基站伪装成假移动电话和向真实移动电话伪装成假基站。

降级攻击:这是对电子系统或通信协议的一种加密攻击形式，它使电子系统或通信协议放弃高质量的加密连接模式，而支持较旧的较低质量的加密连接模式，这种模式通常是为了与较旧的系统向后兼容而提供的。这种漏洞的一个例子就是 [***SS7 攻击***](https://www.theguardian.com/technology/2016/apr/19/ss7-hack-explained-mobile-phone-vulnerability-snooping-texts-calls) 。

七号信令系统(SS7)——一种用于电信的信令协议技术，在世界上大多数公共交换电话网(PSTN)中实施。SS7 攻击是利用 SS7 设计中的弱点来实现数据窃取、窃听、文本拦截和位置跟踪。

黄貂鱼——机构如何监听你的电话

***预防措施***

目前还没有可靠的防御措施来对付所有的 IMSI 捕手。一些应用程序，例如用于根 Android 设备的 [*SnoopSnitch*](https://play.google.com/store/apps/details?id=de.srlabs.snoopsnitch) ，声称可以检测它们的存在，但这种检测是不完善的。

在允许的设备上，禁用 2G 支持(这样设备只能连接到 3G 和 4G 网络)和禁用漫游(如果您不希望在家庭网络的服务区域之外旅行)可能会有所帮助。这些措施可以提供一些保护，防止某些种类的 IMSI 捕手。

> **我们为安卓推荐**[**Orbot**](https://play.google.com/store/apps/details?id=org.torproject.android)**；一个基于 TOR 的代理应用程序，通过在世界各地的一系列中继加密和反弹您的互联网流量，使其他应用程序能够更安全地使用互联网。同样，** [**洋葱浏览器**](https://apps.apple.com/us/app/onion-browser-secure-anonymous-web-with-tor/id519296448) **是 iOS 设备的替代品。**

## 3.Wi-Fi 和蓝牙追踪

***工作原理***

除了移动网络接口，智能手机还具有各种其他无线电发射器，包括 Wi-Fi 和蓝牙支持。每当 Wi-Fi/蓝牙打开时，智能手机就会发送包含 MAC 地址和移动设备唯一序列号的信号，从而让附近的 Wi-Fi/蓝牙接收器识别出特定设备的存在。

利用这一点，即使设备没有主动连接到特定的无线网络，或者即使它没有主动传输数据，也可以观察到 MAC 地址。这种形式的跟踪可以非常准确地判断一个人何时进入和离开建筑物。

此外，家庭 Wi-Fi 路由器是黑客的主要目标，他们希望通过远程传输有效载荷来渗透您的网络。家庭 Wi-Fi 网络中的一个小漏洞可以让黑客访问几乎所有连接到该 Wi-Fi 的设备。一旦感染了恶意软件/间谍软件，路由器可以执行各种恶意活动，如在访问安全通信服务、银行或其他电子商务网站时将用户重定向到虚假网站。除了窃取个人和财务数据，黑客还可以感染连接到家庭网络的智能物联网设备。

***预防措施***

**了解你的网络:**在你连接之前，一定要知道你连接的是谁的网络，这样你才不会成为 [*Wi-Fi 蜜罐*](https://resources.infosecinstitute.com/hotspot-honeypot/#gref) 的牺牲品。此外，请检查以确保您的智能手机没有设置为自动连接到某些未知的 Wi-Fi 网络，或者设置为在连接前询问您。

**使用 VPN:** 如果你使用 VPN 服务，任何试图窥探的人只会看到加密的数据，即使你使用 HTTP 连接到一些不安全的网站。

> **我们推荐**[**TunnelBear VPN**](https://www.tunnelbear.com)**或**[***Vyper VPN***](https://www.vyprvpn.com/)**适用于*Android 和 iOS 设备。***

***MAC 地址随机化:**某些搭载最新 [*安卓*](https://source.android.com/devices/tech/connect/wifi-mac-randomization) 和 [*iOS*](https://support.apple.com/en-us/HT201395) 版本的智能手机，在 Wi-Fi 设置下有一个名为“MAC 地址随机化”的功能。这项功能会随机改变手机报告的 MAC 地址，这使得追踪变得更加困难，甚至是不可能。*

*这项功能并不是所有的 android 手机制造商都一致使用的，但是，在根 android 设备上， [*物理上可以改变 MAC 地址*](https://www.techjunkie.com/change-mac-address-android/) ，这样随着时间的推移，其他人就不容易识别你的 Wi-Fi 了。*

***停用隔空投送:**隔空投送——iPhone 用户的无线文件共享协议，激活后会向附近的其他 iOS 设备广播 iPhone 的可用性。这使得周围的任何其他 iOS 设备都可以轻松请求发送文件的权限。*

*虽然方便，隔空投送是 [*一个已经被黑过去的*](https://www.intego.com/mac-security-blog/airdrop-bug/) 协议。因此，除非需要，否则建议将该协议的首选项设置为“**接收关闭**”。*

*对于 iOS 11 及以后版本:进入**设置** > **通用** > **隔空投送**。
对于 iOS 10 及更早版本:从 iOS 设备底部向上滑动，在**控制中心**中找到隔空投送的快捷方式。*

## *Wi-Fi 路由器安全性*

***更新路由器固件:**更新路由器固件是一项重要的安全措施，有助于保护路由器免受最新威胁和漏洞的侵害。许多路由器不再获得固件/软件更新。如果你的上一次更新是在几年前，是时候换一个新的路由器了。*

***更改路由器凭证:**传统路由器带有制造商创建的默认密码(不是 Wi-Fi 密码)。虽然它看起来很复杂，并且能够抵御黑客攻击，但是同一款路由器的大多数型号很有可能共享同一个密码。这些密码通常很容易在互联网上被追踪或找到。*

*确保您在设置过程中更改了路由器的用户名和密码。选择包含多个字符的复杂字母数字密码。不要使用字典中的单词作为密码。*

***更改 SSID 和 Wi-Fi 加密:**如果您的 Wi-Fi 网络使用默认 SSID(网络名称)，请更改它。不要选择一个明显表明该网络属于您的名称。*

*对于 Wi-Fi 加密，请配合 AES 使用 WPA2。只要密码很长，它就是绝对安全的，因为密码足够长以抵御暴力攻击是至关重要的。( [*德国政府推荐 20 个字符长的密码*](https://www.bsi.bund.de/SharedDocs/Downloads/DE/BSI/Publikationen/TechnischeRichtlinien/TR03148/TR03148.pdf;jsessionid=01F54E80B004E9BFB194DBC00DE9B961.2_cid360?__blob=publicationFile&v=2) *)。*)还有，禁用 WPS。*

***清除任何有风险或未使用的服务:**关闭不使用的功能可以减少攻击面。您可能应该考虑禁用远程管理(也称为远程管理、远程 GUI 或从 WAN 的 Web 访问)、SNMP、NAT-PMP 和对路由器的 Telnet 访问。*

*如果您没有连接任何物联网设备，关闭 UPnP 服务会更安全。UPnP 服务将路由器暴露给整个互联网，如果路由器易受攻击，就可能被黑客攻击。*

***改变整个局域网侧子网**:这有助于防止许多路由器攻击。 [*引导*](https://routersecurity.org/ipaddresses.php)*

***为智能家居设备设置访客网络:**访客网络有其优势。它为您的访客(物联网设备)提供唯一的 SSID 和密码，并限制外人访问您的主网络。*

## *4.用间谍软件/恶意软件感染手机*

*![](img/2e7ffe2dcd5ddc65011cc7cd7aa353eb.png)*

*间谍软件是一种特定类型的恶意软件，旨在跟踪受感染的智能手机的活动。间谍软件可以使用设备的麦克风来监听和记录智能手机附近发生的一切。这些应用程序还可以跟踪你的 GPS 位置、即时消息和文本，上传你拍摄的照片副本，窥探通过其他应用程序如 Signal、WhatsApp、Telegram、Wickr、Discord、Viber 等进行的对话。，窥探/限制来自预定义号码的来电，记录您输入的所有内容，发送各种触发警报，甚至使用摄像头监视您的身体。这些应用程序收集的所有数据随后被发送到一个门户网站，间谍可以在那里查看这些数据。*

*手机可能会感染间谍软件、病毒和其他类型的恶意软件(恶意软件)，要么是因为用户被诱骗安装了恶意软件，要么是因为有人能够利用现有设备操作系统/安装的应用程序中的安全缺陷侵入设备。这些间谍应用程序经常被爱人、家人、可疑的雇主和政/商竞争对手甚至执法机构使用。*

*到目前为止，公众对手机恶意软件的接触一直由私人经营的间谍软件供应商主导。据报道，这些商业智能手机间谍工具最终落入独裁者手中，他们用它来阻碍言论自由，压制异议，甚至更糟。但现在，一些拥有成熟网络能力的政府也适应并利用了移动威胁格局。*

> ***政府和国家支持的 APT(高级持续性威胁)组织在其现有网络间谍活动中开发和部署移动监控活动的能力已经超过了安全行业检测和阻止智能手机上这些间谍软件的能力。***

****(分配机制)****

## ***零日攻击***

*零日漏洞是软件、硬件或固件中的缺陷，负责修补或修复该缺陷的软件开发人员或安全团队对此一无所知。通常，零日攻击利用易受攻击的软件，而不需要用户的任何交互。*

*最近在 WhatsApp 的 VoIP(互联网协议语音)堆栈中发现了一个零日缓冲区溢出漏洞，使得黑客能够通过向目标电话号码发送一系列特制的 SRTP(安全实时传输协议)数据包来远程执行代码。这意味着攻击者可以在 WhatsApp 调用开始时操纵数据包，导致溢出被触发，攻击者霸占应用程序。然后，攻击者可以在设备上部署监视工具来对付目标。*

*尽管与台式机和服务器上看到的更大的攻击面相比，零日攻击相对较少，但它们的存在表明，即使严格遵守不下载不受信任的应用程序，也不足以避免此类攻击的危害。*

****推荐****

*防范零日攻击非常困难。当制造商提供新的软件更新时，您最好的防线是立即安装新的软件更新，以帮助降低被利用的风险。*

*软件更新允许您安装软件或操作系统的必要修订版。这可能包括修复已经发现的安全漏洞。*

> ***出现带有不可理解的数字和字母的 SMS 消息可能表示该设备被利用，因为有时它们是黑客发送的要在目标设备上执行的命令和指令。***

## ***鱼叉式网络钓鱼攻击***

*![](img/707533737d84dcb32e801a76e04aa37d.png)*

*复杂的间谍软件渗透通常从**鱼叉式网络钓鱼**开始，向目标手机发送定制的消息。它可以作为推文、DM/文本消息或看起来无辜的电子邮件发送——任何说服用户**打开 URL/下载附件的电子邮件**。*

*一旦他们这样做了，手机的网络浏览器就会连接到间谍软件遍布全球的众多匿名服务器中的一个。从那里，间谍软件自动确定设备的类型，然后安装远程和秘密的特定利用。*

> ***与桌面用户不同，移动用户无法看到他们正在访问的网站的完整网址。这为数字骗子对不知情的用户使用网络钓鱼攻击铺平了道路。***

*网络钓鱼者经常利用目标天生的恐惧心理，以便让他们迅速采取行动，而不谨慎行事。这些网络钓鱼信息会催促你匆忙**登录你的帐户或安装更新**而不检查来源——就这样，间谍现在有了他们窥探你的设备所需的东西——帐户凭证或未经授权的管理权限。*

*WhatsApp 和其他社交媒体(Twitter、IG、Telegram、Wickr、Discord 等)等消息应用。)也正迅速成为通过网络钓鱼攻击进行移动监控的最流行的方法。*

*国家支持的黑客现在开始选择越来越模糊的目标，试图将一系列复杂的感染串联起来，最终产生有价值的数据。例如，国家支持的 APT 组织通常选择针对一些次要员工，如私人助理或平面设计师，而不是针对首席执行官，这些人可能在他/她的机器上没有特别有价值的信息，但与拥有有价值数据的机器在同一个网络上，可能被用作感染有价值机器的垫脚石。概括一下:攻破平面设计师的机器，使用他/她的电子邮件地址来攻击首席执行官。*

*另一个趋势是，许多网络钓鱼网站正在利用 HTTPS 验证来掩盖其欺骗性。用户认为 HTTPS 网站是安全的，因此他们不太可能怀疑“网络钓鱼”。意识到这一点后，黑客们使用类似[*letsencrypt.org*](https://letsencrypt.org/)这样的网站为他们不安全的钓鱼网站获得 SSL 认证。*

*此外，*消费者间谍软件*市场的增长令人担忧，因为它反映了“现成”恶意软件的趋势，这种软件不需要任何专业知识就可以使用。其中， [*mSpy*](https://www.mspy.com/) 是最容易辨认的一个，但其他你可能看到的还有 [*FlexiSPY*](https://www.flexispy.com/) ， [*WebWatcher*](http://www.komando.com/tips/294714/free-way-to-track-gps-phone-calls-text-messages-and-web-activity-on-a-phone) 和 [*SpyToMobile*](https://spytomobile.com/en) 。通常，这种软件被那些想要监控配偶活动的人使用，提供了一种追踪每个活动的简单方法。*

****推荐****

*任何安全措施都很难防范网络钓鱼，基本上是因为它通常只是您收到的一个电话，或者您访问的一个可疑网站。防范网络钓鱼的唯一真正障碍是知识和持续的警惕。考虑到这一点，这里列出了您应该注意的 [***14 种网络钓鱼攻击。***](https://blog.syscloud.com/types-of-phishing/)*

## *应用商店分发*

*两个最受欢迎的移动操作系统——谷歌 Android 和苹果 iOS——的官方应用商店对其开发者验证和应用提交流程采取了略有不同的方法，导致用户可能下载间谍软件应用的风险程度不同。虽然苹果要求开发者注册才能向 App Store 提交他们的应用程序(包括支付费用)，但 Android 的开源性质对谁可以为他们的平台开发以及在 Google Play 商店中出现的限制要少得多。*

*尽管苹果似乎采用了更严肃的方法来调查应用程序的恶意意图，但偶尔，恶意软件会被成功提交并通过该公司的应用商店 [*提供下载，至少在一段时间内*](https://www.wired.com/story/adware-doctor-mac-app-store-spyware/) 。*

> ***间谍软件被大量上传到应用商店，以利用数量分布，这与垃圾邮件发送者依赖于他们发送的数百万封电子邮件中的一小部分回复者的方式非常相似。***

*间谍软件作者还可以轻松反编译合法的应用程序，并添加代码来执行正常功能之外的恶意操作。对于普通用户来说，重新编译/修改的应用程序通常与原始应用程序难以区分。通常情况下，它们被添加到应用程序商店，使用合法开发者的名字的细微变化，以进一步建立用户的可信度。当这种情况发生得足够频繁时，在移动设备上无意中安装这些间谍软件应用是不可避免的。*

*![](img/00db11bfef3c0214a047baecf81c99c0.png)*

*例如，一个间谍软件应用程序，名为 Radio Balouch aka RB Music——实际上是一个完全适用于 Balouchi 音乐爱好者的流媒体广播应用程序，只不过它是建立在 AhMyth 的基础上；一款开源间谍软件，窃取用户的个人数据。该应用曾两次潜入安卓官方应用商店，但在安全研究人员发出警告后，两次都被谷歌迅速下架。*

*在另一个这样的例子中，美国网络安全公司 crowd strike Intelligence[*报告了*](https://www.crowdstrike.com/blog/danger-close-fancy-bear-tracking-ukrainian-field-artillery-units/) 关于 FANCY BEAR(一个俄罗斯网络间谍组织)的操作，该操作危害了一个应用程序的用户，该应用程序旨在促进在乌克兰服兵役的人群之间的安全通信。因为该应用程序仅分发给有限数量的个人，所以对手很可能获得了对开发人员计算机的访问权，以便检索源代码，从而可以在重新分发之前对其进行修改。重新分发的行为是使用电子邮件进行的，这些电子邮件被伪装成来自原始开发者，指示收件人从附件中安装新版本的应用程序。*

*Android 用户面临的另一个风险是第三方应用商店的可用性，这些商店主要依赖于用户评论，很容易被操纵。此外，用户可以利用直接在移动设备上加载 APK 文件的能力，而根本不必使用 Play Store。这为恶意行为者在谷歌 Play 商店生态系统之外分发他们的间谍软件应用铺平了道路。*

***推荐 ***

> ***在 Android 上，阻止安装第三方应用。转到*设置* > *安全*并取消勾选*未知来源*选项。***

*除非谷歌提高其安全防护能力，否则任何合法应用程序的受感染克隆或间谍软件的某些衍生物都可能出现在 Google Play 上。*

*虽然关键的安全规则“坚持应用程序的官方来源”仍然有效，但仅靠它无法保证安全。强烈建议个人仔细检查他们打算在设备上安装的每个应用程序。*

***使用沙盒应用:***

*Android 已经在沙盒环境中运行所有的应用程序。然而，这些应用程序仍然可以请求访问手机的不同区域，包括你的个人数据所在的区域，如联系人、通话记录和存储等。如果你真的需要使用一个随机/不可靠的应用程序，同时不确定它的真实性，也不想冒险与它共享你的个人数据，那么你必须适当地隔离它。*

*[*Island*](https://island.oasisfeng.com/) 是一款免费开源的沙盒应用，可以克隆选定的应用，并隔离它们，防止它们访问沙盒之外的个人数据(包括通话记录、联系人、照片等)。)，即使授予了相关权限。虽然，设备绑定数据(短信，GPS 定位，IMEI，设备 ID 等。)仍可访问。*

## *水坑攻击*

*在更复杂的操作中，攻击者首先观察目标个人或群体经常访问哪些网站，并感染其中一个或多个网站来托管恶意应用程序。最终，移动间谍软件的传播可能会通过该受损网站得以实现。这种方法为该活动增加了一层合法性，因为潜在的受害者不太可能认为某个已知的合法网站正试图危害他们的移动设备。这种类型的攻击被称为水坑。*

*例如，谷歌的“零项目”安全专家团队在 2019 年初发现了一些网站，这些网站总共存在 14 个 iOS 漏洞，其中两个在被发现时是零天。这些网站被动地攻击任何访问并能够利用 iOS 10 到 iOS 12 的 iOS 设备。然后，这些水坑会植入间谍软件，可以实时窃取私人数据，如 iMessages、照片和 GPS 定位。考虑到现有的漏洞链，研究人员估计这些网站在两年前就已经悄悄地用苹果设备入侵访问者了。*

***推荐 ***

*不幸的是，对于这个固有的移动设备安全问题，除了让敏感数据完全远离它们之外，没有完美的答案。对于大多数人来说，这是一个不切实际的建议，因此减少危害的最佳策略是严格掌握安全更新。*

## *失去身体控制*

*上述大多数间谍软件部署机制都涉及设备在用户手中时发生的危害，无论这是通过用户交互还是远程利用。虽然在许多情况下，由于缺乏对设备的物理控制而导致设备受损的情况不太可能发生，但它仍然适用于前往敌对地区的个人或组织。*

*然而，可能存在恶意行为者试图利用设备不在用户手中的一段时间的情况。诸如当局在过境时安装的监控软件，或在酒店中无人看管的设备(所谓的“ [*邪恶女仆*](https://en.wikipedia.org/wiki/Evil_maid_attack) ”攻击)等情况，可能仅在非常特定的情况下发生，但根据目标的价值，仍可能发生。*

***推荐 ***

*在某些情况下，通过使用 pin 或密码(除非这些是通过强制手段或通过视频监控或传统的" [*"肩窥*](https://en.wikipedia.org/wiki/Shoulder_surfing_(computer_security)) "技术进行被动监控获得的)或通过使用完全干净的设备(仅携带最少的数据并在用户离开敌对区域后完全重置为其原始设置)可以潜在地避免这类威胁。*

***安装**[***Haven***](https://play.google.com/store/apps/details?id=org.havenapp.main&hl=en_IN)*:*Haven 是一款面向 Android 的免费开源监控应用，旨在使用其内置传感器监控设备附近发生的活动，并向设备所有者发出此类活动的警报。警报可以通过短信、信号或基于 Tor 的网站发送。*

# *间谍软件感染的六个警告信号*

*![](img/76ed6d743ab20a3eaba9e0756e4ff510.png)*

## *1.神秘的来电/去电电话或短信*

*你有没有注意到你的手机发出的任何你知道不是你打的电话或短信？您的手机很可能感染了间谍软件/恶意软件。*

## *2.高于通常的数据使用率*

*你手机上的间谍软件根据他们从 CnC(命令和控制中心)收到的命令行动；远程位置的攻击者。要做到这一点，他们需要一个活跃的互联网连接，所以如果你的设备上隐藏了间谍软件，你的移动数据使用量很可能会因为你不知道的原因而增加。如果发生这种情况，您的移动设备很有可能被感染。*

## *3.电池消耗得更快*

*如果你注意到你的手机电池比平时消耗得更快，特别是在正常使用的情况下，很有可能手机里藏着一个间谍软件。间谍软件在你的手机后台运行而不暴露他们的存在，这会导致你的电池更快地耗尽。*

## *4.性能差*

*糟糕的移动性能不能总是归咎于间谍软件或恶意软件。随着时间的推移，手机的性能开始下降，并随着时间的推移变得杂乱无章。但是，如果您习惯于删除不需要的应用程序，避免使用动态壁纸，并采取所有必要的步骤来优化性能，但仍然会遇到延迟和变慢，那么原因可能是由于间谍软件感染。*

## *5.手机上安装的陌生应用*

*移动恶意软件往往会在你的手机上安装其他恶意应用程序，以便它们可以一起工作，进一步感染你的手机。如果你注意到应用程序不是你自己安装的，或者不是一个常用的应用程序，那么你的手机很有可能感染了恶意软件。*

## *6.过热*

*在玩游戏、不停地上网、充电或不停地打电话时，你的手机过热是正常的，有时甚至是意料之中的。然而，如果你不在使用手机，或者你的手机大部分时间无缘无故地发热，那么你的手机很有可能感染了恶意软件。*

## *5.对缴获的手机进行法医分析*

*![](img/af793924b87df8746226a9f8d7b2c2ad.png)*

****工作原理****

*移动设备的取证分析是一个成熟的专业领域。专家分析员会将一个被扣押的设备连接到一个特殊的取证机器上，即 [*【塞勒布里特】UFED*](https://www.cellebrite.com/en/solutions/pro-series/)[*MSAB XRY*](https://www.msab.com/products/xry/)*[*磁铁公理*](https://www.magnetforensics.com/products/magnet-axiom/) 等。，通过轻松绕过屏幕锁定机制，读取存储在设备中的数据，包括以前的活动记录、电话和短信。取证分析可能能够恢复用户通常无法看到或访问的记录，如已删除的短信，这些短信可能无法恢复。**

****JTAG:** JTAG(联合测试行动小组)取证是一种数据采集方法，它涉及连接到设备上的测试访问端口(tap)，并指示处理器传输存储在连接的内存芯片上的原始数据。在得到支持的情况下，JTAG 是一种极其有效的技术，可以从普通工具无法获取的设备中提取完整的物理图像。**

****芯片外取证:**芯片外取证是一种先进的数字数据提取和分析技术，涉及从目标设备上物理移除闪存芯片，然后使用专用设备获取原始数据。芯片外取证是一项强大的功能，允许收集几乎任何设备的完整物理映像，甚至是那些遭受灾难性损坏的设备。通常，当所有其他取证提取选项(包括 JTAG)都已用尽时，此取证方法是提取数据的首选方法。**

*****预防措施*****

> ****注意:在刑事或监管调查中故意、鲁莽或疏忽地破坏/篡改证据或妨碍调查可能会被指控为犯罪，通常会导致非常严重的后果。****

*   **加密您的全部数据。加密静态数据(而不是动态消息)的最佳方式是整体加密，即加密存储分区或简单地加密整个内存。**
*   **不过，请记住， [*磁盘加密*](https://proprivacy.com/guides/encryption-guide-to-securing-android-phone) 只在手机关机时保护手机(即保护静止数据)。一旦设备被打开，数据被透明地解密，并且解密密钥在存储器中可用。**

> ****我们推荐**[**Keeper:Password Manager&Secure Vault**](https://keepersecurity.com)**应用，作为一个附加的加固措施，Android 和 iOS 设备都适用。****

*   **设置一个难猜的强密码，至少有六位数字和字母数字字符。**
*   **为了增加安全性，不要使用指纹或面部识别系统等生物识别技术，这些技术比强密码更容易被攻破。**
*   **在 Android 上，不要使用模式解锁，这很容易被偷看你手机的人发现，甚至可以通过分析你的屏幕污迹来破解。**
*   **使用数字数据粉碎机彻底清除您希望从移动设备中删除的数据。**

> ****我们推荐** [**PROTECTSTAR 的 is hreder**](https://www.protectstar.com/en/)**应用，适用于 Android 和 iOS 设备。****

## **6.应用数据泄露**

**![](img/9ac3e2095cf62239045dd02a15dac2a4.png)**

*****工作原理*****

**现代智能手机为手机提供了确定自身位置的方法，通常使用 GPS，有时使用 IP 定位和手机信号塔定位等其他服务。安装在该设备中的应用程序可以向手机请求这些信息，并使用它来提供基于位置的服务，如地图、一些社交媒体应用程序、出租车和送餐应用程序，这些应用程序可以在地图上显示您的位置。**

**其中一些应用程序会通过网络将你的位置传输给服务提供商，这反过来为其他人提供了跟踪你的方法。开发者还在他们的应用程序中嵌入第三方追踪器，允许他们收集关于用户的各种其他信息和行为模式，并使用它来显示有针对性的广告。**

**第三方追踪器继承主机应用程序请求的应用程序权限集，允许他们访问大量有价值的用户数据，通常超出他们提供预期服务所需的数据。这些追踪器可以收集个人数据，如 Android IDs、电话号码、设备指纹、MAC 地址、实时位置、各种应用程序的使用模式、浏览器历史、短信、通话记录、电子邮件、社交媒体聊天等。**

**最重要的是，应用商店不要求开发者披露他们对第三方广告和跟踪服务的使用，因此用户对他们在应用中的存在一无所知。因此，应用程序不会告诉我们他们使用了哪些服务，他们的隐私政策声明通常对这些服务的使用含糊其辞。这种缺乏透明度的情况并没有因为他们经常分享或出售大量的移动追踪数据而出现在[](https://theoutline.com/post/2490/why-is-this-company-tracking-where-you-are-on-thanksgiving?zd=1&zi=bc7hldhj)*的新闻中。***

***应用程序开发人员的动机可能不是想要监视用户，但他们最终可能仍然有能力这样做，他们最终可能会向政府或黑客透露用户的敏感个人信息。***

***政府也开始对分析许多用户移动设备的数据感兴趣，以便自动发现某些模式。这些模式可以让政府分析师发现人们以不寻常/可疑的方式使用手机的情况。***

***例如，位置跟踪不仅仅是找到某人现在的位置。也可以是回答关于人们的历史活动、参与事件、他们的信仰和个人关系/联系的问题。它还可以用来发现某些人是否处于浪漫关系中，检测一群人何时一起旅行或定期见面，或者试图识别记者的机密来源。***

***随着智能手机变得无处不在，技术变得更加精确，窥探人们日常习惯的行业已经蔓延开来，变得更加侵入性。***

******预防措施******

***最受数据收集公司欢迎的应用程序是那些提供针对人们位置的服务的应用程序，包括天气、交通、旅游、购物交易和约会，因为用户更有可能在这些应用程序上启用定位服务。***

> *****安装应用时仔细检查应用权限。一个好的隐私做法是限制所有应用程序对个人信息的最低访问权限。请求的权限越多，数据不安全地发送给对手的可能性就越大。*****

***与 iPhones 不同，Android 手机不允许你将应用程序对你位置的访问限制在你使用它的时候。Android 上任何获得你许可追踪你位置的应用程序都可以接收数据，即使你没有使用它。***

***虽然，在 Play Store 上有一个叫 [*Bouncer*](https://play.google.com/store/apps/details?id=com.samruston.permission) 的 app，让安卓用户可以临时授予权限。当一个应用程序关闭时，Bouncer 会自动删除一些与该应用程序相关的权限。***

*****停止 iOS 上的位置跟踪:*****

***打开**设置** > **隐私** > **位置服务** >你会看到一个应用列表，以及每个应用的位置设置。点击您想要调整的应用程序。选择“**从不**”会阻止该应用程序的跟踪。***

***(使用应用程序时的选项**确保应用程序仅在使用时获取位置。选择“**始终**”，允许应用程序在不使用时获取位置数据。)*****

*****停止 Android 上的位置跟踪:*****

***打开**设置** > **安全&位置** > **位置** > **App 级权限** >关闭某个 App 的位置，**向左滑动拨动**。***

***这些说明是针对最近的安卓手机的；Google 在这里 提供了更多的说明 [*。*](https://support.google.com/android/answer/6179507)***

*****监控和停止第三方应用:*****

***一款名为 [*Lumen*](https://play.google.com/store/apps/details?id=edu.berkeley.icsi.haystack) 的安卓应用，通过监控用户设备上运行的应用的网络活动，帮助用户识别并阻止第三方服务。它还告诉我们正在收集什么样的数据，以及哪些组织正在收集特定的数据。***

***[*Blokada*](https://blokada.org/index.html) 是另一个用于 Android 设备的工具，可以有效地阻止广告和追踪器。它也是免费的开源项目。***

****了解有关高级技巧和设置的更多信息，以提高智能手机的隐私和安全性。看看吧，* ***智能手机安全对于隐私的偏执*** *。* *👇****

***[](https://medium.com/@reliancegcs/smartphone-security-for-the-privacy-paranoid-6f2595f12085) [## 对隐私偏执的智能手机安全

### 实用隐私高级指南

medium.com](https://medium.com/@reliancegcs/smartphone-security-for-the-privacy-paranoid-6f2595f12085)*** 

## ***参考资料:***

```
***1\. Featured Image: Photo by Simon Prades via NewScientists
2\. The Problem with Mobile Phones | Surveillance Self-Defense: [https://ssd.eff.org/en/module/problem-mobile-phones](https://ssd.eff.org/en/module/problem-mobile-phones)
3\. Image 1: Photo from Getty Images via Wired.com: [https://www.wired.com/2017/02/verizons-unlimited-data-plan-back-heres-compares-carriers/](https://www.wired.com/2017/02/verizons-unlimited-data-plan-back-heres-compares-carriers/)
4\. Extreme Security Measures For The Extra Paranoid | WIRED: [https://www.wired.com/story/extreme-security-measures/](https://www.wired.com/story/extreme-security-measures/)
5\. How to Keep Your Bitcoin Safe and Secure | WIRED: [https://www.wired.com/story/how-to-keep-bitcoin-safe-and-secure/](https://www.wired.com/story/how-to-keep-bitcoin-safe-and-secure/)
6\. How to Protect Your Privacy on Public Wi-Fi Networks | Techlicious: [https://www.techlicious.com/tip/how-to-protect-your-privacy-on-public-wifi-networks/](https://www.techlicious.com/tip/how-to-protect-your-privacy-on-public-wifi-networks/)
7\. Image 2: Photo from PLAINPICTURE via bloomberg.com: [https://www.bloomberg.com/news/articles/2016-03-10/what-happens-when-the-surveillance-state-becomes-an-affordable-gadget](https://www.bloomberg.com/news/articles/2016-03-10/what-happens-when-the-surveillance-state-becomes-an-affordable-gadget)
8\. IMSI Catchers and Mobile Security: [https://www.cis.upenn.edu/wp-content/uploads/2019/08/EAS499Honors-IMSICatchersandMobileSecurity-V18F.pdf](https://www.cis.upenn.edu/wp-content/uploads/2019/08/EAS499Honors-IMSICatchersandMobileSecurity-V18F.pdf)
9\. SS7 hack explained: what can you do about it? | The Guardian: [https://www.theguardian.com/technology/2016/apr/19/ss7-hack-explained-mobile-phone-vulnerability-snooping-texts-calls](https://www.theguardian.com/technology/2016/apr/19/ss7-hack-explained-mobile-phone-vulnerability-snooping-texts-calls)
10\. SS7 HACKING: How hackers interrupt your call and data | Daily Junkies: [https://dailyjunkies.com/ss7-hacking-how-hackers-interrupt-your-call-and-data/](https://dailyjunkies.com/ss7-hacking-how-hackers-interrupt-your-call-and-data/)
11\. Your home wi-fi isn't safe | Economic Times: [https://economictimes.indiatimes.com/magazines/panache/your-home-wi-fi-isnt-safe-hackers-know-router-trick-to-access-bank-accounts-card-details/articleshow/70571283.cms](https://economictimes.indiatimes.com/magazines/panache/your-home-wi-fi-isnt-safe-hackers-know-router-trick-to-access-bank-accounts-card-details/articleshow/70571283.cms?from=mdr)
12: Router security: How to setup Wi-Fi router securely | Norton:   [https://us.norton.com/internetsecurity-how-to-how-to-securely-set-up-your-home-wi-fi-router.html](https://us.norton.com/internetsecurity-how-to-how-to-securely-set-up-your-home-wi-fi-router.html)
13\. Router Security - Full List: [https://routersecurity.org/](https://routersecurity.org/#FullList) 
14\. Image 3: Photo from HOTLITTLEPOTATO via Wired.com: [https://www.wired.com/story/router-hacking-slingshot-spy-operation-compromised-more-than-100-targets/](https://www.wired.com/story/router-hacking-slingshot-spy-operation-compromised-more-than-100-targets/)
15\. How Israeli spyware tried to hack an Amnesty activist's phone | FastCompany: [https://www.fastcompany.com/90212318/how-israeli-spyware-tried-to-hack-an-amnesty-activists-phone](https://www.fastcompany.com/90212318/how-israeli-spyware-tried-to-hack-an-amnesty-activists-phone)
16\. Mobile Malware and APT Espionage: Prolific, Pervasive, and Cross-Platform | Cylance: [https://threatvector.cylance.com/en_us/home/mobile-malware-and-apt-espionage-prolific-pervasive-and-cross-platform.html](https://threatvector.cylance.com/en_us/home/mobile-malware-and-apt-espionage-prolific-pervasive-and-cross-platform.html)
17\. Attackers Exploit WhatsApp Flaw to Auto-Install Spyware | Bank of Security: [https://www.bankinfosecurity.com/attackers-exploit-whatsapp-flaw-to-auto-install-spyware-a-12480](https://www.bankinfosecurity.com/attackers-exploit-whatsapp-flaw-to-auto-install-spyware-a-12480)
18\. Zero-day vulnerability: What it is, and how it works | Norton: [https://us.norton.com/internetsecurity-emerging-threats-how-do-zero-day-vulnerabilities-work-30sectech.html](https://us.norton.com/internetsecurity-emerging-threats-how-do-zero-day-vulnerabilities-work-30sectech.html)
19\. Image 4: Photo from Kaspersky Blog: [https://www.kaspersky.com/blog/phishing-spam-hooks/24888/](https://www.kaspersky.com/blog/phishing-spam-hooks/24888/)
20\. Mobile Security 101 | Norton: [https://za.norton.com/internetsecurity-mobile-mobile-security-101.html](https://za.norton.com/internetsecurity-mobile-mobile-security-101.html)
21\. How to Protect Yourself From Cellphone Phishing Attacks | Digital Trends: [https://www.digitaltrends.com/mobile/how-to-protect-yourself-from-cellphone-phishing-attacks/](https://www.digitaltrends.com/mobile/how-to-protect-yourself-from-cellphone-phishing-attacks/)
22\. Mobile phishing attacks are moving to messaging and social media apps at an alarming rate | Wandera: [https://www.wandera.com/mobile-security/phishing/mobile-phishing-attacks/](https://www.wandera.com/mobile-security/phishing/mobile-phishing-attacks/)
23\. Phone surveillance in 2017: Are you being watched? | Digital Journal: [http://www.digitaljournal.com/tech-and-science/technology/phone-surveillance-in-2017-are-you-being-watched/article/486599](http://www.digitaljournal.com/tech-and-science/technology/phone-surveillance-in-2017-are-you-being-watched/article/486599)
24\. What is APT? | Kaspersky: [https://www.kaspersky.co.in/blog/apt/2050/](https://www.kaspersky.co.in/blog/apt/2050/)
25\. 5 smartphone spy apps that could be listening and watching you right now | Komando: [https://www.komando.com/tips/362160/5-smartphone-spy-apps-that-could-be-listening-and-watching-you-right-now](https://www.komando.com/tips/362160/5-smartphone-spy-apps-that-could-be-listening-and-watching-you-right-now)
26\. How to protect against phishing scams | Norton: [https://in.norton.com/internetsecurity-online-scams-how-to-protect-against-phishing-scams.html](https://in.norton.com/internetsecurity-online-scams-how-to-protect-against-phishing-scams.html)
27\. Mobile Threat Landscape Report: 2019 | CrowdStrike: [https://www.crowdstrike.com/resources/reports/mobile-threat-report-2019/](https://www.crowdstrike.com/resources/reports/mobile-threat-report-2019/)
28\. First‑of‑its‑kind spyware sneaks into Google Play | welivesecurity: [https://www.welivesecurity.com/2019/08/22/first-spyware-android-ahmyth-google-play/](https://www.welivesecurity.com/2019/08/22/first-spyware-android-ahmyth-google-play/)
29\. How To Sandbox Android Apps For Ultimate Data Privacy | Gtriks:   [https://www.gtricks.com/android/how-to-sandbox-android-apps-for-privacy/](https://www.gtricks.com/android/how-to-sandbox-android-apps-for-privacy/)
30\. Major Watering Hole Attack on iOS Shows Massive Challenge of Mobile Device Security | CPO Magazine: [https://www.cpomagazine.com/cyber-security/major-watering-hole-attack-on-ios-shows-massive-challenge-of-mobile-device-security/](https://www.cpomagazine.com/cyber-security/major-watering-hole-attack-on-ios-shows-massive-challenge-of-mobile-device-security/)
31\. Spyware - What Is It & How To Remove It | Malwarebytes: [https://www.malwarebytes.com/spyware/](https://www.malwarebytes.com/spyware/)
32\. Image 5: Photo from Getty Images via Wired.com: [https://www.wired.com/story/ccleaner-malware-supply-chain-software-security/](https://www.wired.com/story/ccleaner-malware-supply-chain-software-security/)
33\. Signs That Your Android Could be Infected With a Virus | Cybersponse: [https://cybersponse.com/6-signs-that-your-android-could-be-infected-with-a-virus/](https://cybersponse.com/6-signs-that-your-android-could-be-infected-with-a-virus/)
34\. Image 6: Photo from SEÑOR SALME via Wired.com: [https://www.wired.com/2016/10/inside-cyberattack-shocked-us-government/](https://www.wired.com/2016/10/inside-cyberattack-shocked-us-government/)
35\. JTAG Forensics | Binary Intelligence: [http://www.binaryintel.com/services/jtag-chip-off-forensics/jtag-forensics/](http://www.binaryintel.com/services/jtag-chip-off-forensics/jtag-forensics/) 
36\. Chip-Off Forensics | Binary Intelligence: [http://www.binaryintel.com/services/jtag-chip-off-forensics/chip-off_forensics/](http://www.binaryintel.com/services/jtag-chip-off-forensics/chip-off_forensics/)
37\. How to Encrypt Your Texts - Calls - Emails and Data | WIRED: [https://www.wired.com/story/encrypt-all-of-the-things/](https://www.wired.com/story/encrypt-all-of-the-things/)
38\. Foucault M. Technologies of the self: A seminar with Michel Foucault. Amherst: University of Massachusetts Press; 1988.
39\. How to Lock Down Your iPhone - David Koff | Medium: [https://medium.com/@TheTechTutor/how-to-lock-down-your-iphone-f81c7bb4f8af](https://medium.com/@TheTechTutor/how-to-lock-down-your-iphone-f81c7bb4f8af)
40\. Image 7: Photo from Leong Thian FU/Getty Images via Wired.com: [https://www.wired.com/story/google-location-tracking-turn-off/](https://www.wired.com/story/google-location-tracking-turn-off/)
41\. How Google Tracks Your Personal Information – Patrick Berlinquette | Medium: [https://medium.com/s/story/the-complete-unauthorized-checklist-of-how-google-tracks-you-3c3abc10781d](https://medium.com/s/story/the-complete-unauthorized-checklist-of-how-google-tracks-you-3c3abc10781d)
42\. How to Stop Apps From Tracking Your Location | The New York Times: [https://www.nytimes.com/2018/12/10/technology/prevent-location-data-sharing.html](https://www.nytimes.com/2018/12/10/technology/prevent-location-data-sharing.html)
43\. The ICSI Haystack Project Blog - Abbas Razaghpanah: [https://haystack.mobi/wordpress/](https://haystack.mobi/wordpress/)***
```