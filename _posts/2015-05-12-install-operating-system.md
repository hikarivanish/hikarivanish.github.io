---
layout: post
title: 浅浅的谈U盘启动和系统安装
---

### U盘启动

国内有很多所谓的U盘启动制作工具，如laomaotao之类的，
但是国内的这类工具都会向电脑**嵌入流氓程序**，
只要用这个启动，它先检测硬盘中是否有windows，如果有则先降低user control setting的提示level，
再在启动文件夹中加入恶意脚本，等你启动windows时联网给你装上360之类的很多软件。

如果用此类工具安装windows，则是在安装过程中嵌入脚本，下场还是一样。

所以只能用国外的工具，或者直接将安装镜像写入U盘


### U盘写入

- UltraISO

        这个是最稳定的，可以用绿色版，我用过许多镜像，只有这个软件都可以正确引导，
        且支持uefi
- RUFUS

        这个比较新，官网上说写入速度是同类软件中最快的，
        但我用了有些镜像不能引导，貌似它只用linux的引导头，
        而UltraISO有linux引导头和winPe的引导
- unetbootin

        老牌的upan启动工具，但貌似对windows的支持捉急啊
- win32diskimager

        这个就是直接写入，貌似不加引导头，我试了，只有kali和fedora成功引导

### 启动工具合集

主要是用来修复系统，备份系统，分区，引导安装系统之类的。通常人们把这些工具放在一个winPe里面。
例如norton ghost，PartitionMagic。

- [Boot_USB_Sergei_Strelec](http://www.sergeistrelec.ru/forum/20)
  这个比较新，工具也齐全，目前用的就是这个。
- [hiren's bootcd](http://www.hirensbootcd.org/)
  这个在国外名气很大，相当于国内的[老毛桃](http://laomaotao.net/)
  ![hirensbootcd.png]({{ site.url }}/assets/hirensbootcd.png)

### 系统安装

国内直接用ghost安装的很多(因为方便)，几年前创始人被抓的番茄花园之类的。**这些都不好**。
其实网上提供的ghost就是破解后的windows和驱动程序打包而成，当然不忘送你许多垃圾软件。
所以msdn上提供的安装镜像和正版才是最干净的。
但是破解和pro版却是一个问题，所以我一般使用[海盗湾](http://thepiratebay.se)上比较流行的镜像安装，当然已经破解了

目前win8.1是最好的系统选择，不管是新机器还是几年前的旧机器。
原因很多，如省了很多补丁，自带安全软件(windows defender,原MSE[Microsoft Security Essentials])，
安全机制和输入法管理等等都有很大的提升。注意`win8`和`win8.1`是完全不同的系统，不只是update而已。
