---
layout: posts
title: 在ubuntu上安装jdk
---

也许有人会问这有什么难的，但是据我多次在桌面版ubuntu上安装的经验来看，直接下载再修改环境变量不是一个很好的办法，有时候会和openjdk混淆，有时候只有root才能用jdk。所以，简单的事简单办，ubuntu官方给出的oracle jdk 安装方法：

```bash
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
``` 
