# 使用 gau-Expose 工具分析 Gau 结果

> 原文：<https://infosecwriteups.com/analyze-your-gau-result-with-gau-expose-tool-124edf7682b7?source=collection_archive---------1----------------------->

![](img/34418dfb63f25c7ac06d559ba0f4c39c.png)

# 愿你平安

你好黑客们。我希望你一切都好。我是塔米姆·哈桑，来自孟加拉国🇧🇩.的安全研究员和臭虫赏金猎人

今天我们学习如何使用 **Gau-Expose** 工具分析 gau URLs 结果。制作这个工具的想法来自于 [Sm9l](https://medium.com/@Sm9l/the-most-underrated-tool-in-bug-bounty-and-the-filthiest-one-liner-possible-cab14ef7faeb) 。所以谢谢你伙计。

![](img/1c3a02560fa550056b1b508d9621f936.png)

> **那么什么是 Gau**

它从 AlienVault 的开放威胁交换、Wayback Machine 和 Common Crawl 中获取已知的 URL。

> 让我们言归正传

那么 [**Gau Expose**](https://github.com/tamimhasan404/Gau-Expose) 工具是做什么的呢？

**答**:这让你在分析 **gau** 结果的时候工作变得简单了一点，同时也收集了其他信息，比如

**[]收集子域**

它收集来自 gau 网址的子域，用这个，你可能会发现一些不同的域，正常的子域枚举工具找不到。

**[]收集面板素材**

如登录、注册等。这很有帮助，因为您可能会找到一个容易被绕过旧面板，或者找到任何可以使用默认凭证轻松登录的面板。或者启用了任何具有注册选项的管理/员工面板。

**【聚集第三方资产】**

比如:格拉夫纳、吉拉、詹金斯等

如果您发现任何漏洞，您可以访问该 url(如果存在)，然后尝试根据其版本找到漏洞。

**【聚集机器人】txt**

我在这个工具中添加了这个东西，因为有时 robots.txt 会向您显示一些泄露敏感信息的路径。这些类型的路径可能不在你的单词表中，但是它们存在于 domains **robots.txt** 文件中。所以要手动检查。

**[]收集电子邮件/用户名**

它收集电子邮件和用户名，如果他们存在于 gau 的结果。这种结果可能会帮助您登录到任何特殊的登录面板，就像您找到任何特殊的登录作者邮件/用户名，然后您可以尝试暴力破解。

**【收集敏感文件】**

它收集一些敏感文件，如 bak，zip，xls 等。所以你必须手动检查，因为很多时候它 greps 不必要的东西。

**[]收集错误**

正如我们所知，有时错误暴露了有用的信息，这可能有助于我们在进一步的攻击，或有助于与其他一些漏洞链。虽然几率很低，但碰碰运气也无妨。

**[]为目录暴力收集路径**

这非常有用，因为您从 gau 中收集的这些路径是特定于目标的，因此将这些单词列表与通用单词列表相结合对于目标基本目录暴力破解来说是非常好的。

**注意:**为了快速获得结果，你可以使用 [gauplus](https://github.com/bp0lr/gauplus) 工具而不是 gau。

**++** 现在开始之前你要做的

1.  安装 gauplus 和 uro 工具

*   ***高斯:***

```
go install github.com/bp0lr/gauplus@latest
```

*   如果这种方法不起作用，请手动安装 gauplus

```
git clone [https://github.com/bp0lr/gauplus.git](https://github.com/bp0lr/gauplus.git)cd gauplusgo buildmv gauplus /usr/local/bin/
```

*   **Uro**

```
pip3 install uro
```

**++** 在目标实时域上运行 gauplus 工具

cat live-domains . txt | gau plus-t 30 > gau-URLs . txt

**++** 现在只需运行[**Gau-Expose**](https://github.com/tamimhasan404/Gau-Expose)**工具**

```
bash gau-expose.sh
```

**然后把你的 gau-urls.txt 路径就这样。**

**今天就到这里吧，伙计们。如果我犯了任何错误，请原谅我，如果你有任何建议/问题，让我知道。祝您愉快:)**

****可以关注我的**[**Youtube**](https://www.youtube.com/c/HackoMedia404)**|**[**Github**](https://github.com/tamimhasan404)**|**[**Twitter**](https://twitter.com/tamimhasan404)**|**[**Linkedin**](https://www.linkedin.com/in/tamimhasan404/)|[**脸书**](https://www.facebook.com/tamimhasan404)**