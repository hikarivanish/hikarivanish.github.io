---
layout: post
title: 拆解y485/y485p等联想笔记本
---

笔记本用了一段时间后，感觉散热越来捉急，有几次热的cpu当机了。记得有几次u盘上跑kali，想直接跑出密码来，结果总是一下子机子就挂了，当时没弄清楚原因，以为是U盘上跑不稳定的缘故，后来才知道是机子热的。我的笔记本是联想y485，联想的笔记本清灰比较麻烦，需要拆的比较深。

### 拆底面

首先**拿掉电池**，这个在加内存或加ssd时特别容易忘记。手摸大金属**释放静电**。

![y485-battery.jpg]({{ site.url }}/assets/y485-battery.jpg)

拆掉几颗螺丝就能看见硬盘了，无线网卡旁就是mSata接口，可以加ssd

![y485-d.jpg]({{ site.url }}/assets/y485-d.jpg)

内存也比较容易拿下来，

![y485-mem.jpg]({{ site.url }}/assets/y485-mem.jpg)
![y485-d-mem.jpg]({{ site.url }}/assets/y485-d-mem.jpg)

硬盘可以用黑带拿下来，

![y485-hd.jpg]({{ site.url }}/assets/y485-hd.jpg)
![y485-hd-2.jpg]({{ site.url }}/assets/y485-hd-2.jpg)

光驱可以直接拖出来，

![y485-cdrom.jpg]({{ site.url }}/assets/y485-cdrom.jpg)

拆键盘面之前，要把底面所有的螺丝全去掉。

### 拆键盘面

键盘这一步非常难拆，最好有专业的工具，一般买拆机工具会送的黄色塑料翘棒。
千万小心**键盘下有排线**，不能直接拿，否则排线会坏。要从上边开始翘(暗扣比较多)。

![y485-keybord-1.jpg]({{ site.url }}/assets/y485-keybord-1.jpg)

打开排线扣，才能把键盘拿下来，然后打开面板和主板之间的排线扣，把面板拆下，

![y485-tiaoxian.jpg]({{ site.url }}/assets/y485-tiaoxian.jpg)
![y485-c-front.jpg]({{ site.url }}/assets/y485-c-front.jpg)
![y485-c-naked.jpg]({{ site.url }}/assets/y485-c-naked.jpg)

然后就可以把风扇弄开，清灰了。
可以参考这里专业人员推出的[专业的视频](http://v.youku.com/v_show/id_XNTM5MjM5NTQ4.html)



