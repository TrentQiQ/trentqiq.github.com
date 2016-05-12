---
layout:     post
title:      "Welcome to QiQ Blog"
subtitle:   "一些博客建立过程中的细节"
date:       2016-05-06
author:     "QiQ"
header-img: "img/jekyll.jpg"
tags:
    - 生活
---
## 前言

一直想鼓捣一个自己的独立博客，趁着最近几天的空闲终于可以好好搞搞了。。。
博客主要采用Github+Jekyll的方法实现。需要一些git基础以及前端技术。

## 使用GitHub Pages的一些参考

[一步步在GitHub上创建博客主页-最新版](http://www.pchou.info/ssgithubPage/2014-07-04-build-github-blog-page-08.html)

[通过GitHub Pages建立个人站点（详细步骤）](http://www.cnblogs.com/purediy/archive/2013/03/07/2948892.html)

[jekyll模版](http://jekyllthemes.org/)


创建过程中没什么坑，主要就是一些git操作，熟练就好。如果不是专业前端可以选择一个jekyll模版，在模版的基础上做修改生成自己的博客样式。


## 搭建windows下jekyll本地环境碰到的问题


* 安装路径问题
* gem源问题

**解决方案**

> 1. 安装步骤参考这个[jekyll安装](http://www.pchou.info/web-build/2013/01/05/build-github-blog-page-04.html),安装路径确保没有中文，空格之类的字符，最好安装在如C盘或D盘根目录
>
> 2. [gem源替换](http://www.haorooms.com/post/gem_not_use)国内由于众所周知的原因，访问国外源较慢，所以需要替换国内源，在前两个参考中都选择了淘宝的源作为替换，但是可能由于本人的网络是教育网，淘宝的源也不好用，后来发现了一个山东理工大学的源，测试可用。http://ruby.sdutlinux.org/
>
> 3. [Markdown入门](http://sspai.com/25137) 由于之前没接触过markdown的语法，所以搜索了一篇markdown的一些基础命令介绍。windows下用的一个叫MarkdownPad2的软件，可以实现实时预览，效果不错。

*本地环境搭建好后，便可以在本地进行页面效果的测试，测试完成后再将修改后的文件通过git统一提交到github。毕竟修改一点然后提交查看效果不满意再重新修改提交的过程也是挺麻烦，在本地测试完一次性提交也能减少麻烦。*
