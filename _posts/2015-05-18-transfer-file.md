---
layout: post
title: 与服务器传输文件的常用方法
---

经常需要往VPS上传输文件，比较方便的方法有这些：

### sftp

不需要安装ftp服务器，直接利用ssh就可以传了，这里推荐filezilla，有个问题要注意，下载filezilla的安装包时，要选择`Show additional download options`，否则会下载sourceforge的壳。

![filezilladown.PNG]({{ site.url }}/assets/filezilladown.PNG)

直接在host中输入

    sftp://ip

filezilla就会自动用sftp协议。

![filezilla.PNG]({{ site.url }}/assets/filezilla.PNG)

### netcat

有些时候条件很苛刻，比如渗透时要往肉鸡上传文件，这个时候就需要netcat。通常也是先用netcat得到反弹shell。

接收端：

    nc -l [port] >　file

发送端：

    nc [ip] [port] < file

需要注意：

* 先运行listen的一端
* 有些版本的netcat需要在端口前加`-p`，也就是要改成：

        nc -l -p [port] > file

### netcat && ncat

[ncat](https://nmap.org/ncat/)是渗透扫描利器nmap的一部分，官方描述为

    ncat was written for the Nmap Project as a much-improved reimplementation of the venerable Netcat.

不过其实和netcat也差不多。

```
root@kiwi:~# nc -h
[v1.10-40]
connect to somewhere:   nc [-options] hostname port[s] [ports] ...
listen for inbound:     nc -l -p port [-options] [hostname] [port]
options:
        -c shell commands       as `-e'; use /bin/sh to exec [dangerous!!]
        -e filename             program to exec after connect [dangerous!!]
        -b                      allow broadcasts
        -g gateway              source-routing hop point[s], up to 8
        -G num                  source-routing pointer: 4, 8, 12, ...
        -h                      this cruft
        -i secs                 delay interval for lines sent, ports scanned
        -k                      set keepalive option on socket
        -l                      listen mode, for inbound connects
        -n                      numeric-only IP addresses, no DNS
        -o file                 hex dump of traffic
        -p port                 local port number
        -r                      randomize local and remote ports
        -q secs                 quit after EOF on stdin and delay of secs
        -s addr                 local source address
        -T tos                  set Type Of Service
        -t                      answer TELNET negotiation
        -u                      UDP mode
        -v                      verbose [use twice to be more verbose]
        -w secs                 timeout for connects and final net reads
        -z                      zero-I/O mode [used for scanning]

```
