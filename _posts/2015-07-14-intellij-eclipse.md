---
layout: post
title: intellij IDEA和eclipse几个重要不同(要注意的点)
---

公司用eclipse用的比较多，而我个人比较喜欢intellij,在使用intellij开发公司里的项目时，遇到了一些比较罕见的坑，由此得出了几个注意的点，当然前方一定还有很大的坑。

##### 注意点1：使用纯净的maven/gradle项目

也就是说，不要把.idea .setting等ide的配置文件放入git中，不然后患无穷。如果已经有.setting之类的文件，用idea导入的时候，注意不要当成idea工程导入，因为其实这个.setting是eclipse生成的。一定要以maven或gradle形式导入。

##### 注意点2：项目根目录与resource目录

eclipse的锅。

公司里用springboot开发。我们都知道标准的springBoot工程中application.properties文件是放在resource下的，打包后会在classpath下。公司里也不知道是谁起的头，把application.properties放在了项目根目录下，神奇的是在eclipse中居然可以正常运行。

而一到idea下就会出问题，因为spring在classpath下找不到application.properties，通常会报找不到驱动类(class not found)错误。这才是符合逻辑的。当时这个问题让我很困惑，为什么同一个项目eclipse没问题，idea就不能运行。

##### 注意点3：<scope\>provided</scope\>

还是eclipse的锅。

有时在pom.xml中有provided的依赖，比如servlet，编译jsp会用到，但是运行时tomcat已经提供了。公司里有些项目不知为什么把一些应该打包进去的依赖也设置为provided。神奇的是，在eclipse中同样可以运行。

而在idea中就会出现编译没有问题，运行时就会找不到jar包。

-----
暂时就这些，再遇到坑再回来添加。