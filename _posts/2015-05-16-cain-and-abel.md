---
layout: post
title: 用cain&abel嗅探局域网数据
---

在 学校机房，电子图书馆 之类的局域网环境通常是嗅探数据的好地方(*不要做坏事*)。

嗅探数据和arp工具比较多，kali里面带的就有不少，如果要全部抓下来事后分析直接用`wireshark`之类的，`tcpdump`更好些，因为是命令行的。

但是如果是简单的玩玩，cain&abel还是比较方便的。这个软件比较老，但真的比较实用，也包含密码破解之类的其他功能，当然比较鸡肋了，其他功能还是用专业的软件比较好，比如密码破解首推`hashcat`。但是局域网嗅探还是非常方便的。

1. 第一步要做的是关闭windows防火墙
2. 找到网关的ip，因为是arp的目标啊
3. 配置http的密码字段，这个看需求了，比如要截取别人登陆学籍系统的用户名密码，就要先自己试试用浏览器开发者工具看看提交的字段名是什么，然后添加到cain&abel中(因为它是边嗅探边分析的) 

    ![cainhttpfields.PNG]({{ site.url }}/assets/cainhttpfields.PNG)

    ![cainhttpconfig.PNG]({{ site.url }}/assets/cainhttpconfig.PNG)

4. 在arp routing中添加 你的`目标机器ip`和`网关ip`

    ![cainnewrouting.PNG]({{ site.url }}/assets/cainnewrouting.PNG)

5. 开启arp按钮和嗅探按钮，等着收鱼就好了

    ![cainresult.PNG]({{ site.url }}/assets/cainresult.PNG)