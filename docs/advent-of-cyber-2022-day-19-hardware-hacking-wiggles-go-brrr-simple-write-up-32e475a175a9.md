# Cyber 2022 的来临[第 19 天]硬件黑客| Wiggles go brrr-简单记录

> 原文：<https://infosecwriteups.com/advent-of-cyber-2022-day-19-hardware-hacking-wiggles-go-brrr-simple-write-up-32e475a175a9?source=collection_archive---------1----------------------->

## 任务 24-硬件黑客| Wiggles go brrr 网络 2022 的来临[第 19 天]-答案撰写和演练

![](img/5d4eccb3bf06763128c9415392b278df.png)

> *让我们进入 0 和 1 的世界。这就引出了一个问题，硬件是如何获取电能并产生信号的？在这项任务中，我们将重点关注数字通信。*
> 
> *对于硬件通信，我们使用一种叫做* ***逻辑分析仪*** *的设备来分析信号。该设备可以连接到用于两个设备之间通信的实际电线，这两个设备将捕获并解释正在发送的信号。*

**USART**

通用同步/异步接收器-发射器(USART)通信，或者更广为人知的串行通信，是一种使用两条线的协议。

一根线用于从器件 A 向器件 B 发送(TX)数据，另一根线用于从器件 B 接收(RX)器件 A 上的数据，本质上，我们将一个器件的发送端口连接到另一个器件的接收端口，反之亦然。

**SPI**

串行外设接口(SPI)通信协议主要用于微处理器与传感器或 SD 卡等小型外设之间的通信。

虽然 USART 通信将时钟内置于 TX 和 RX 线路中，但 SPI 使用单独的时钟线。将时钟(SCK)与数据(数据)线分开允许同步通信，这更快且更可靠。

**I2C**

内部集成电路(I2C)通信协议是为了解决 USART 和 SPI 通信协议的缺点而创建的。由于 USART 是异步的，并且时钟内置于发送和接收线路中，因此设备必须提前就通信配置达成一致。

此外，速度会降低，以确保通信保持可靠。

另一方面，虽然 SPI 速度更快、更可靠，但它需要更多的通信线路，而且每增加一个外设都需要多一条片选线路。

# 任务 24【第 19 天】**硬件黑客|** Wiggles go brrr

## 1.什么设备可以用来探测两台设备之间电线上传输的信号？

对于硬件通信，我们使用一种称为逻辑分析仪的设备来分析信号。

该设备可以连接到用于两个设备之间通信的实际电线，这两个设备将捕获并解释正在发送的信号。

```
Ans: logic analyser
```

## 2.USART 比 SPI 通讯快？(是，不是)

> *USART 通信将时钟内置于 TX 和 RX 线路中，但 SPI 使用单独的时钟线。*
> 
> *将时钟(SCK)与数据(data)线分开，可以实现同步通信，也就是* ***更快更可靠*** *。因此，代价是增加一根额外的电线，但我们获得了速度和可靠性的提升。*

```
Ans: Nay
```

## 3.USART 通信使用的电线比 SPI 少？(是，不是)

> *通用同步/异步接收器-发射器(USART)通信，或更广为人知的串行通信，是一种使用双线的协议。*
> 
> *一根线用于从设备 A 向设备 B 发送(TX)数据，另一根线用于从设备 B 接收(RX)设备 A 上的数据*

```
Ans: Yea
```

## 4.USART 的通讯速度比 I2C 快？(是，不是)

> *内部集成电路(I2C)通信协议旨在解决 USART 和 SPI 通信协议的缺点。*
> 
> *由于 USART 是异步的，并且时钟内置于发送和接收线路中，因此设备必须提前就通信配置达成一致。*
> 
> *此外，* ***速度降低*** *以确保通信保持可靠。*

```
Ans: Nay
```

## 5.I2C 使用比 SPI 更多的电线进行通信？(是，不是)

> *SPI 更快、更可靠，它需要更多的通信线，并且每增加一个外设都需要多一条片选线。*
> 
> I2C 试图解决这些问题。与 USART 类似，I2C 只利用 ***两条线*** *进行通信。I2C 使用串行数据(SDA)线和串行时钟(SCL)线进行通信。*

```
Ans: Nay
```

## 6.SPI 比 I2C 通信速度快？(是，不是)

SPI 比 I2C 更快更可靠

```
Ans: Yea
```

## 7.一对 I2C 线上最多可以连接多少台设备？

![](img/8c4f162942821a9cd2b591ec7d8c78e4.png)

使用外部时钟线，通信仍然比 USART 更快更可靠，虽然比 SPI 稍慢，但地址信号的使用意味着多达 **1008 个设备**可以连接到相同的两条线，并能够进行通信。

```
Ans: 1008
```

## 8.微处理器和 ESP32 芯片之间协商的新波特率是多少？

打开远程机器的拆分视图

![](img/25794aee2fbf14969cbbbf48152dee7b.png)![](img/5b62a2df5ba9932402ef4160930f2f35.png)

打开 Logic 2.4.2 应用程序并打开 Capture-Santa

![](img/7399511c7f4e5b2f66558f182a1e8159.png)![](img/43fab87b1730da6abfaa9a8de0550c63.png)![](img/316bb4511cb940a8ae308e56c8f8a9a2.png)![](img/9609244839ef216a6da833dc1bf56d1e.png)

点击分析仪，添加异步串行分析仪，并将输入通道设为**通道 1，波特率/比特率设为 4800**

![](img/760bfc1026a80a217c53fb2d1b18f260.png)![](img/903e850b06638855a9b91577ec2c6294.png)![](img/00fdd6f625989d5a8217b07632c753c8.png)

```
Ans: 9600
```

## 9.一旦新的波特率被接受，传输的标志是什么？

添加另一个异步串行分析仪，给定输入通道为**通道 0，波特率/比特率为 9600**

![](img/1f38ab88e9920714a27e9859be30cf02.png)![](img/03ce41a5c729ed690480fcb99bcb85df.png)![](img/d978ca9e18676d2428dffbc64529a307.png)

```
Ans: THM{Hacking.Hardware.Is.Fun}
```

感谢您的阅读！！

黑客快乐~

```
Author : Karthikeyan Nagaraj ~ Cyberw1ng
```

查询:

THM，TryHackMe，TryHackMe 2022 年网络时代的到来，TryHackMe 2022 年网络时代的到来第 19 天，道德黑客，写，走过，TryHackMe 2022 年网络时代的到来第 19 天答案

## 来自 Infosec 的报道:Infosec 每天都有很多内容，很难跟上。[加入我们的每周简讯](https://weekly.infosecwriteups.com/)以 5 篇文章、4 条线索、3 个视频、2 个 GitHub Repos 和工具以及 1 个工作提醒的形式免费获取所有最新的 Infosec 趋势！