---
layout: post
title: wamp的初始配置及注意点
---

### 选择wamp的原因

其实就是为了开发时有个数据库，但是sqlserver和oracle显然是太大了。

也可以直接安装mysql和navicat for mysql，但是习惯了phpmyadmin，而且有个本地的web服务器好些，开发前端时也可以用到。

其他win+mysql+apache/nginx+php的安装管理合集也有很多，国内也有这类软件，不过还是选国外流行的比较靠谱，更新也好。

### 安装和初始配置

1. 安装vccredit_x64 和.net frameword 4.0 
2. 安装wamp
3. 编辑phpmyadmin 改成cookie

    就是改成这样：
        
        /* Authentication type */
        $cfg['Servers'][$i]['verbose'] = 'mysql wampserver';
        $cfg['Servers'][$i]['auth_type'] = 'cookie';
        //$cfg['Servers'][$i]['auth_type'] = 'config';
4. 打开phpmyadmin ChangePassword
5. 删除any用户  否则其他用户无法登陆

### 要注意的地方

- 必须先安装vccredit_x64 和.net frameword 4.0，否则wamp安装失败，只能卸载重装
- sqlserver 的repoter service会占用80端口，使得apache服务不能启动，stop即可
