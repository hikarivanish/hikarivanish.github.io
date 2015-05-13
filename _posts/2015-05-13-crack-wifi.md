---
layout: post
title: wifi破解的流程总结
---


### 概述

目前破解无线路由器的方法比较固定。
先分目标打开wps和未打开两种情况

- 若打开了wps，则用reaver试PIN码，时间3-10小时不等看运气，
但一旦试出PIN码则一劳永逸，不怕对方改wifi密码
- 若未打开，则嗅探握手包(可打断连接促进握手)，用字典破解。

国内的奶瓶之类的系统也基本上以Aircrack-ng为核心的，不推荐。

第一步都是将网卡设置为监听模式：

    airmon-ng start wlan0

查看无线的信息，打开一个新终端：

    airodump-ng mon0

### reaver

直接输入：

    reaver -i mon0 -b MAC -a -S -vv

等待结果即可。
reaver会将中间结果保存session，不怕被打断。

### Aircrack-ng

直接输入：

    airodump-ng --ivs -c 频道 --bssid target's MAC -w 握手包文件 mon0

抓到后ctrl-c即可。**不要**用Aircrack-ng来跑包，效率太低,而要用hashcat。

### hashcat

真神器，目前世界上最快的 password cracker，基于GPU。

拿到握手包后，需要转成hashcat可以处理的文件：

[convert a WPA / WPA2 pcap capture file to a oclHashcat capture file](https://hashcat.net/cap2hccap/)

破解方式有很多mode，如字典，Brute-Force等等，根据电脑性能跑的速度也差很大。
具体的方式需参考 [hashcat wiki](http://hashcat.net/wiki/)

    oclHashcat [options]... hash|hashfile|hccapfile [dictionary|mask|directory]

其中破握手包的话为`--hash-type=2500`。

---
网上也有跑包的业务，不过貌似tb上很难搜到了。国外有付费用云服务器跑包的平台，就是比较贵。