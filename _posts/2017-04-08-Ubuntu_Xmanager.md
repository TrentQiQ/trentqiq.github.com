---
layout:     post
title:      "Ubuntu + Xmanager 实现远程图形化界面"
subtitle:   "测试环境为Ubuntu14.04.5_x64"
date:       2017-04-08
author:     "QiQ"
header-img: "img/BingWallpaper-2017-04-08.jpg"
tags:
    - Ubuntu
    - Xmanager
---

*Ubuntu14.04自带图形化桌面环境为Unity，桌面显示管理器为lightdm。实际测试中发现能用Xmanager连接到Ubuntu看到登录界面，输入密码登录后就会闪退，登录不到桌面，并且在登录界面看不到鼠标。*  
因此考虑换个桌面环境，采用**Ubuntu+lightdm+Mate+Xmanager的方式实现远程图形化界面**

---
1. 关闭防火墙或是打开177端口（二选一）  
    `sudo ufw disable`  
    `sudo ufw allow 177`
2. 启用XDMCP登陆  
`sudo vi /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf`  
确保有如下两行  
`[XDMCPServer]`  
`enabled=true`
3. 安装Mate桌面  
`$ sudo apt-add-repository ppa:ubuntu-mate-dev/ppa`  
`$ sudo apt-add-repository ppa:ubuntu-mate-dev/trusty-mate`  
`$ sudo apt-get update`  
[mate官方WIKI](http://wiki.mate-desktop.org/download)针对Ubuntu 14.04给出了三种安装方式  
`$ sudo apt-get install mate-desktop-environment-core   #安装一个最小化的mate桌面`  
`$ sudo apt-get install mate-desktop-environment        #安装一个完整的mate桌面`  
`$ sudo apt-get install mate-desktop-environment-extras #安装一个完整的mate桌面(包含推荐的软件包)`
4. 修改默认登录桌面（可选）  
`sudo vi /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf`  
`[SeatDefaults]`  
`user-session=ubuntu    #修改默认登录桌面`  
在`/usr/share/xsessions`路径下可以看到当前拥有的桌面环境  
*当用户在图形化界面登录过一次之后，下次登录时系统会默认使用上次登录界面时选择的桌面环境*

参考：
> [xmanager远程Ubuntu1604LTS](http://blog.csdn.net/junbujianwpl/article/details/52792878)  
> [配置Xmanager连接Ubuntu 14.04远程桌面](http://blog.csdn.net/jwq2011/article/details/54970540)  
> [ubuntu自定义登录xsession和桌面环境](https://www.zhukun.net/archives/7783)
