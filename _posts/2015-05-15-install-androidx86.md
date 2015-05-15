---
layout: post
title: androidx86的介绍与在vmware上的安装
---

在androidx86项目出现以前，pc上的android模拟器一直是蛋疼的存在。而androidx86有了之后，genymotion等一些厉害的模拟器开始出现了。

这次，我介绍下原生androidx86在vmware上的安装。

### 介绍

目前，功能最强大的pc平台的android模拟器是genymotion，搞安卓开发自然是必装。

但究其核心，和国内的许多杂七杂八的模拟器一样，本质都是android源码在x86平台上编译后的核心。

之前adt自带的模拟器慢的原因是：系统编译的target platform是arm平台，指令集自然与x86不同，在pc上运行需要再加一层转换。唉，我在电子的最后研究的就是arm平台的linux，当时为了搞懂`交叉编译`什么的真的费了好大劲。

androidx86项目的主页： [www.android-x86.org](http://www.android-x86.org/)

### 用vmware装原生androidx86的原因

* 有时候不做开发的话并不需要genymotion这样强大的东西，如只是想快速运行一些app
* genymotion等模拟器不能调整性能，而vmware可以调整cpu，内存，越大越爽。
* genymotion等模拟器套件增加了系统复杂度，出bug的几率也大大增加，

    genymotion是基于virtualbox，外面再套一层东西，国内的一些模拟器加的东西就不清楚安不安全了。而用vmware装的话只是一个vm而已，很绿色。

### 安装过程

**注意**：首先需要一个vpn，否则安装完第一次启动无法初始化(无法连接google服务)。

1. 在[官网](http://www.android-x86.org/)上下载iso
2. 新建虚拟机，选择advanced，选择3.x的linux内核
3. 磁盘类型选择IDE，cpu和内存越多越快，去掉打印机等一些无用硬件，cd/dvd载入下好的iso
4. 启动，选择installation

    首先创建分区：

    ![androidx86createpartition.PNG]({{ site.url }}/assets/androidx86createpartition.PNG)

    选择new：

    ![androidx86newpartition.PNG]({{ site.url }}/assets/androidx86newpartition.PNG)

    选择primary：

    ![androidx86primarypartition.PNG]({{ site.url }}/assets/androidx86primarypartition.PNG)

    设置为bootable：

    ![androidx86bootable.PNG]({{ site.url }}/assets/androidx86bootable.PNG)

	写入分区表：

    ![androidx86writetable.PNG]({{ site.url }}/assets/androidx86writetable.PNG)

	这样就有sda1可以安装了：

    ![androidx86sda1.PNG]({{ site.url }}/assets/androidx86sda1.PNG)

	选择ext3文件系统：

    ![androidx86ext3.PNG]({{ site.url }}/assets/androidx86ext3.PNG)

	安装grub：

    ![androidx86grub.PNG]({{ site.url }}/assets/androidx86grub.PNG)

    接下来就直接安装了，**第一次启动前连接vpn**，选择skip wifi：

    ![androidx86skipwifi.PNG]({{ site.url }}/assets/androidx86skipwifi.PNG)

	这个时候如果不能连接到google，就会出现这种情况，初始化失败：

    ![androidx86connnecting.PNG]({{ site.url }}/assets/androidx86connnecting.PNG)

    可以连接的话就能继续:

    ![androidx86gotgoogle.PNG]({{ site.url }}/assets/androidx86gotgoogle.PNG)

    完成后的图：

    ![androidx86finishinstall.PNG]({{ site.url }}/assets/androidx86finishinstall.PNG)

    **重要配置**，将sleep设置为never，否则休眠后vmware无法唤醒：

    ![androidx86sleep.PNG]({{ site.url }}/assets/androidx86sleep.PNG)

    勾选unknown source，去掉verify：

    ![androidx86security.PNG]({{ site.url }}/assets/androidx86security.PNG)

5. 将虚拟机做个snapshot，每次需要关机都选择暂停虚拟机，而不要在android中关机。

### 调试连接

android 虚拟机是可以调试连接的，在adt中设置虚拟机的ip和端口，刷新adb就能连接调试android程序了，不过开发的话还是直接用genymotion比较方便。

