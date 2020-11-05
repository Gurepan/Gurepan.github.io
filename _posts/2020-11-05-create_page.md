---
layout:     post
title:      GitHub Pages搭建博客流程
subtitle:   GitHub Pages Blog
date:       2020-11-05
author:     Gure
header-img: img/2020-11-05-create_page/bg-art.jpg
catalog: true
tags:
    - 建站
---
随着自己年龄逐渐变大，要掌握的知识也逐渐变多，现在老是觉得自己的知识体系边得不够扎实了。很多自己觉得可以联系在一起的，并且可以继续深入的知识，也逐渐成为了一个个孤岛。最近查看了[费曼学习法](https://wiki.mbalib.com/wiki/%E8%B4%B9%E6%9B%BC%E5%AD%A6%E4%B9%A0%E6%B3%95)的相关资料，觉得应该试试从写点东西开始，来巩固和复习自己掌握的知识，提升自己的弱点：表达能力。于是搭建了这个基于`GitHub Pages`的博客，并把流程记录下来。

<!-- more -->

## 为什么选择GitHub Pages

- **Markdown** — 已融入到程序生涯中，具备优雅的写作体验。
- **免费** — 利用 GitHub Pages 的域名和免费无限空间，不用自己采购云主机。
- **Git工作流** — 非常熟悉的程序流程，Git Commit + Push 即可发布博文。
- **基于Jekyll** —无论是本地调试还是发布，简单的操作都可以获得令人满意的效果。
- **多种插件集成** —访客统计，评论功能，自定义社交链接等一系列功能都有对应的插件支持。

## 简介

#### GitHub Pages
[GitHub](https://github.com) 是通过`Git`进行版本控制的软件源代码托管服务，允许个人用户创建公开的代码仓库。GitHub 设计了 [GitHub Pages](https://pages.github.com) 功能允许用户为自己的项目提供网页展示，来替代默认的代码列表。GitHub Pages 可以被认为是用户编写的，托管在 GitHub 上的静态网页。

#### Jekyll
[Jekyll](https://jekyllrb.com) （发音/'dʒiːk əl/，“杰克尔”） 是一个简单的博客形态的静态站点生产机器。它有一个模版目录，其中包含原始文本格式的文档，通过一个转换器（如 Markdown）和我们的 Liquid 渲染器转化成一个完整的可发布的静态网站，你可以发布在任何你喜爱的服务器上,包括 GitHub Page 。

#### Disqus
[Disqus](https://disqus.com) 是一家第三方社会化评论系统，主要为网站提供评论托管服务。


## 本地环境搭建
我一般先习惯于在本地环境进行编写和调试，确认以后再上传到远程。

#### 安装 Ruby 和 DevKit
在官网下载，[点这里]( https://rubyinstaller.org/downloads/ )下载适合系统版本的 Ruby+Devkit 包。安装时候弹出的窗口选3（msys2 and mingw development toolchain）

![安装ruby](https://github.com/Gurepan/Gurepan.github.io/blob/master/img/2020-11-05-create_page/%E5%AE%89%E8%A3%85ruby.png?raw=true)

`gem -v` `ruby -v` 查看得到版本号就说明成功了。

如果是在墙内，需要切换安装源到https://gems.ruby-china.com/。墙外就不需要了。

`gem sources --add https://gems.ruby-china.com/ --remove https://rubygems.org/` 切换安装源

#### 安装bundler
`gem install bundler`  安装bundler

`bundle -v`  查看版本

`bundle config mirror.https://rubygems.org https://gems.ruby-china.com`  切换安装源

#### 安装Jekyll

[Jekyll 中文文档](http://jekyll.com.cn)，英语水平一般的福利。
`gem install jekyll` 所有`Jekyll`的依赖包都会被自动安装。
![安装Jekyll](https://github.com/Gurepan/Gurepan.github.io/blob/master/img/2020-11-05-create_page/%E5%AE%89%E8%A3%85jekyll.png?raw=true)

#### 搭建项目
使用 `Github Pages` + `Jekyll` 构建一个技术博客很简单，基本上步骤就是网上找一个自己喜欢的主题，`git clone`到本地 ，然后在删掉原博客中的内容，在上传自己的文章即可。在这里我也提供了一个自己的[模板](https://codeload.github.com/Gurepan/jekyll-blog/zip/main)，觉得合适的可以直接下载。

#### 预览博客
进入项目后`jekyll server`或者`jekyll s`  输入之后打开浏览器，不出意外输入localhost:4000即可看到博客内容。
![启动jekyll](https://github.com/Gurepan/Gurepan.github.io/blob/master/img/2020-11-05-create_page/%E5%90%AF%E5%8A%A8jekyll.png?raw=true)

这里以我自己的模板为例。
![预览博客](https://github.com/Gurepan/Gurepan.github.io/blob/master/img/2020-11-05-create_page/%E9%A2%84%E8%A7%88%E5%8D%9A%E5%AE%A2.png?raw=true)

## 搭建GitHub Pages服务

####  注册 GitHub 账号

要使用 GitHub Pages 服务，首先要注册一个 [GitHub](https://github.com) 账号，这个不必多说

#### 创建一个项目仓库

仓库名为`your GitHub name.github.io`，这个也不必多说

#### 提交本地项目

将本地项目提交到远程仓库上，，这个不必多说了吧？

## 细化配置

#### 注册 Disqus 帐号

为了给 Blog 加上评论系统，需要一个第三方的服务，可选择 [Disqus](https://disqus.com/)、[Duoshuo](http://duoshuo.com/)、[Gitalk](https://github.com/gitalk/gitalk)。我选择的是 Disqus。

注册好 `Disqus` 帐号后需要在账户下创建一个站点：

![](https://github.com/Gurepan/Gurepan.github.io/blob/master/img/2020-11-05-create_page/disqus.png?raw=true)

并配置好个人信息，记录好自己的`Shortname`。
在`_config.yml`中加入一行：
```yaml
disqus_username: 自己的Shortname
```
到此 `Disqus` 帐号及配置已基本准备完毕。

#### 增加访客记录
访客记录我用的是[不蒜子](http://busuanzi.ibruce.info/)网页计数器。用法也很简单，在`_includes\footer.html`中找到你满意的位置加上
```html
<script async src="//busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js"></script>
<span id="busuanzi_container_site_pv">本站总访问量<span id="busuanzi_value_site_pv"></span>次</span>
```

#### 注册 百度统计 帐号

如需要给自己的博客加上统计分析，则可以集成 [Baidu Analytics](http://tongji.baidu.com/web/welcome/login) 和 [Google Analytics](http://www.google.cn/analytics/)。这个我就懒得加了。


#### 配置 Blog

[Jekyll 网站的基本结构](https://www.jekyll.com.cn/docs/structure/)：

```
├── _config.yml
├── _drafts
|   ├── begin-with-the-crazy-ideas.textile
|   └── on-simplicity-in-technology.markdown
├── _includes
|   ├── footer.html
|   └── header.html
├── _layouts
|   ├── default.html
|   └── post.html
├── _posts
|   ├── 2007-10-29-why-every-programmer-should-play-nethack.textile
|   └── 2009-04-26-barcamp-boston-4-roundup.textile
├── _data
|   └── members.yml
├── _site
└── index.html
```

主要记住以下几点基本满足日常使用：
- `_config.yml`全局配置文件
- `_posts` 这里放的就是你的文章了。文件格式很重要，必须要符合：`YEAR-MONTH-DAY-title.md`

**_config.yml 配置**
```yaml
# 站点设置
title: 我的博客
SEOTitle: 我的博客 | My Blog
header-img: img/post-bg-desk.jpg
email: 暂无
description: "写一句你想写的话"
keyword: "我的博客"
url: "http://name.github.io"          # your host, for absolute URL
baseurl: ""      # for example, '/blog' if your blog hosted on 'host/blog'
github_repo: "https://github.com/name/name.github.io.git" # you code repository

# 侧边栏设置
sidebar: true                           # whether or not using Sidebar.
sidebar-about-description: "这里写自我介绍"
sidebar-avatar: /img/avatar.jpg # 个人头像路径

# 社交配置
RSS: false # 是否开启rss
zhihu_username:  # 知乎用户名
github_username:  # GitHub 用户名
jianshu_username:   # 简书用户名

# 评论设置
# Disqus（https://disqus.com/）
disqus_username: Shortname # 前文记录的Shortname
```

修改完成后提交到 GitHub 则已完成基本配置，博客已可访问。

## 动手写文章

发表文章一般用`markdown`格式写好放在`_posts`目录下。
一般文件头配置：

```markdown
---
layout: post
title: "标题"
subtitle: " 子标题"
date: 2020-11-05 00:00:00 # 写作日期
author: "作者名"
header-img: "你的图片路径（一般在img下）.jpg" # 文章头部背景图地址
catalog: true # 是否开启目录
tags: # 标签
    - 笔记
---
```
