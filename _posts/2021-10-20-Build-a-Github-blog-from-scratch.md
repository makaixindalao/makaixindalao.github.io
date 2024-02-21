<!--
 * @Copyright (C), 2020-2023, hkzy Co., Ltd.: 
 * @FileName     : 
 * @Author       : mkx
 * @Description  : 
 * @Others       : 
 * @Function List: 
 * @LastEditTime : 2024-02-21 11:44:43
-->
---
layout: post
title: 从零开始GitHub博客搭建
description: 从零开始GitHub博客搭建，小白推荐。
categories:
  - Jekyll
tags:
  - Jekyll
---

毕业一年多啦，终于有时间自己弄一个博客，如今博客基本是开发者的标配之一了，在博客中分享自己的学习经验，能够帮助自己梳理学到的内容，促进技术成长。

这篇文章记录了我从零开始，在GitHub上建立自己的博客的过程，也是查了很多资料，遇到了很多问题。

## GitHub

### 选择GitHub的三大优势：
1.免费：白嫖的最香。

2.开源：GitHub作为国内外最热门的开源平台之一，参与的人非常多，能找到很多的技术支持和开源代码。

3.便捷：托管在GitHub上，不需要花时间去打理，使用MarkDown语法，容易上手。

#### GitHub注册与环境配置

![1](/images/posts/github/t1.jpg)

直接百度GitHub，然后根据引导提示注册GitHub。注册号以后登录 ![](/images/posts/github/Github-start-a-project.png)

然后选择创建仓库

![](/images/posts/github/creat-a-new-reository.png)

Repository name 这一栏中填写特定格式内容：你的GitHub名.github.io（很重要，这个也是以后你的GitHub博客网址）。例如，我的GitHub名叫makaixindalao，所以此处应该填写makaixindalao.github.io。输入完成后，点击Create repository。



接下来是环境配置，我比较懒，直接转载CSDN上的一篇[很详细的文章（GitHub环境搭建）](https://blog.csdn.net/gavincook/article/details/11992827?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522163477958916780366572063%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=163477958916780366572063&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-1-11992827.first_rank_v2_pc_rank_v29&utm_term=github%E7%8E%AF%E5%A2%83%E9%85%8D%E7%BD%AE&spm=1018.2226.3001.4187)，这里不再赘述。不过我推荐使用[GitHub Desktop](https://desktop.github.com/)，相对于GitHub的命令行，图形化界面更容易入门。

## Jekyll

#### 为什么要用jekyll

jekyll是一个简单的免费的Blog生成工具，类似WordPress。但是和WordPress又有很大的不同，原因是jekyll只是一个生成静态网页的工具，不需要数据库支持。但是可以配合第三方服务,例如Disqus。最关键的是jekyll可以免费部署在Github上，而且可以绑定自己的域名。

#### Jekyll安装
Jekyll是一个编译工具，安装好Jekyll后，你可以用过Jekyll创建网站模板，然后通过访问 http://localhost:4000/ 或 http://127.0.0.1:4000 从本地访问刚刚创建的网站。通过修改本地文件，可以实时通过本地预览修改效果，修改好后再上传到GitHub上，更加便捷和高效。

安装步骤如下：

1、下载安装[Ruby installer](https://rubyinstaller.org/);

2、下载[RubyGems](https://rubygems.org/pages/download)，通过cmd访问下载文件位置，例如我放在E:\Software\rubygems-2.7.4，那么通过CMD访问这个目录，cd E:\Software\rubygems-2.7.4，然后执行Rubygems安装命令：gem install jekyll，安装成功后，使用jekyll命令创建一个博客模板:

    cd d
    jekyll new blog
    cd blog
    jekyll server

接下来在浏览器访问 http://localhost:4000/ 或 http://127.0.0.1:4000 ，即可进入刚刚创建的网站。

#### Jekyll主题选择

这里提供[Jekyll主题官网](http://jekyllthemes.org/)，可以在里面选择合适的主题。

![chose-themes](/../images/posts/github/chose-themes.png)

例如选择Simplex主题，点击Homepage可以链接到该blog Github页面，点击download可以下载该博客源码，点击demo可以预览该博客效果。

点击download，将该源码下载下来，命令行进入该目录，再执行jekyll server，执行成功可以在控制台看到运行路径：

![cmd1](/../images/posts/github/cmd1.png)

#### Jekyll目录结构

![catalog](/../images/posts/github/catalog.png)

这里提供一个讲的很好的[说明文档](http://jmcglone.com/guides/github-pages/)，有基础的道友们可以去看看。

#### Jekyll部分语法

[官网传送门](http://jekyllcn.com/docs/home/)，可以在官网更详细了解Jekyll语法。我就偷懒不写啦，官网写的很详细。

## 总结

一个博客模板总算是搭建完成了，后面可能会写一篇关于修改博客模板的blog。
