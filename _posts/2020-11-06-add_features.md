---
layout:     post
title:      为博客增加新功能
date:       2020-11-06
author:     Gure
catalog: true
header-img: img/2020-11-06-add_features/post-bg-debug.png
---

现在趁吃夜宵的功夫，为我的博客增加了两个新功能：

- 首页推荐文章
- 首页文章标签

效果见图：PS:我知道格式很丑了，等我学会css会改的！！

![功能](https://github.com/Gurepan/Gurepan.github.io/blob/master/img/2020-11-06-add_features/%E5%8A%9F%E8%83%BD.png?raw=true)

下面来说说这个流程：

## 增加首页文章标签

不得不说ruby真是一门对人类友好的语言，像我这种完全不懂的人看个大概也可以依葫芦画瓢写点新功能，配合上`Jekyll`的模板引擎，让我有一种像是在写`thymeleaf`或者是`vue`的感觉。它的语法就是下面这种：

![标签](https://github.com/Gurepan/Gurepan.github.io/blob/master/img/2020-11-06-add_features/%E6%A0%87%E7%AD%BE.png?raw=true)

这一段也是我增加功能写的代码，在`index.html`这个文件里新增这段即可。里面提及的`post`的指的是我们平时写的，读者看的文章实体。而`post.tags`这个也很明显，就是我们写博文时候在文章头备注里加上的熟悉了。也就是说，以后要是有什么新属性也可以加到文章头备注里，在用ruby代码的时候使用`post.新属性`就可以获取到了。同时，这段话的意思也很明白，就是一个判断，如果`post.tags`存在而且不为空，就会把`if`和`endif`里面的内容渲染出来。这里面还有一个`for`循环做循环渲染`a`标签，这个应该都看得懂这里就不解释了。



增加首页文章标签就这样就完成了，简单吧？



## 新增首页推荐文章功能

首页推荐文章功能的新增其实也一样简单，主要是修改`_layouts/page.html`文件：

![推荐](https://github.com/Gurepan/Gurepan.github.io/blob/master/img/2020-11-06-add_features/%E6%8E%A8%E8%8D%90.png?raw=true)

这段话其他地方都很好理解，主要是这里新增了一个对象叫`site`。这个对象我的理解是可以把它看成是`_config.yml `文件和整个站点其他所有对象的集合。所以要开启这个功能，需要在`_config.yml `文件里面新增加一行

```yaml
recommend-recommend: true                #是否使用推荐文章
```

同时，在这段话里面还做了一个所有文章的循环判断（还好是静态渲染+个人博客文章少），判断文章里面只有`recommend`属性存在而且为`true`时候才会渲染出来：

```ruby
if post.recommend == true
```

因此，使用的时候，需要在想要推荐的文章的文章头里加上`recommend: true `这个属性。

这样，首页推荐文章功能也就实现了。

## 源码

为了方便大家吐槽，我把对这次源码的改动也贴上来[点这里](https://github.com/Gurepan/Gurepan.github.io/commit/c91269f9f37e3c88a5e20c3c196a5af1095b667f)，欢迎大家提issue。 ^_^

