---
layout: post
title: 使用Github搭建个人博客
category: 操作配置
tags: [环境搭建]
description: 使用Github的page功能和jekyll搭建个人博客
---

[GitHub](https://github.com)，是全球最大的社交编程及代码托管网站，GitHub可以托管各种git库，并提供一个web界面，但与其它像SourceForge或Google Code这样的服务不同，GitHub的独特卖点在于从另外一个项目进行分支的简易性。这里着重写如何使用Github的page功能搭建个人博客。

<!-- more -->

###目录
{:.no_toc}

* 目录
{:toc}

###1.github博客概述

为什么我选择github写博客呢？最开始在CSDN、新浪等博客平台写过博客，也在印象笔记中做过笔记，但是都只是满足了我一部分的需求。对于理工科而已，良好的数学编辑环境、支持博客分类、博客搜索等功能也必不可少，这样也方便自己以后查找和回顾。这一切，在github page中都可以实现。甚至包括添加社交评论、分享等功能，也可以使用百度统计来查看博客的访问情况等功能。另外，github本身的版本控制也非常方便我进行编辑博客、与他人一起合作编辑等等。

但是，毕竟自己搭建博客是一个相对需要一点技术的事情，尤其是使用Markdown进行博客写作，也与传统的Word写作方式不一样，都需要付出时间来学习。然而，学会之后，确实很有帮助！

[GitHub](https://github.com)，是全球最大的社交编程及代码托管网站，一个拥有无数多开发者的社区。其中不乏Linux发明者[Torvalds](https://github.com/torvalds)这样的顶级黑客，以及Rails创始人[DHH](https://github.com/dhh)这样的年轻极客。上面也很多人开源项目，包括Python的机器学习库sklearn，深度学习库theano、pylearn2、BootStrap、Node.js、CoffeScript等等！

[Jekyll](http://jekyllcn.com/) 是一个简单的博客形态的静态站点生产机器。它有一个模版目录，其中包含原始文本格式的文档，通过 Markdown （或者 Textile） 以及 Liquid 转化成一个完整的可发布的静态网站，你可以发布在任何你喜爱的服务器上。Jekyll 也可以运行在 GitHub Page 上，也就是说，你可以使用 GitHub 的服务来搭建你的项目页面、博客或者网站，而且是完全免费的。

注意：本文只是介绍在github上搭建blog，不考虑本地博客环境。此外，本文列出了许多可以参考的文档，感兴趣深入的同学可以深入了解！

###2.搭建博客

一般的教程是在本地搭建好jekyll环境，之后一步一步的使用github搭建博客。但是，这里我没有在本地搭建环境。所以，如果想在本地搭建环境的，需要去其他地方找资料了。
步骤流程参考[Github Page](https://pages.github.com/)，这里只是简单的介绍下！

####2.1新建项目

首先需要大家建立一个去建立一个github账号。注册成功之后，我们新建一个项目，注意**项目名称**！，如下图：

<img src="/images/application/github_blog.jpg" height="80%" width="80%">

之后可以设置该项目的属性，在项目的右侧的Settings，可以设置允许有wiki等，注意GitHub Pages不要选择**automatic page generator!**。

####2.2Git下载

在项目建立完之后，我们下载Github。我自己电脑上装的是通用版的[Git](http://www.git-scm.com/download/win),无法下载的童鞋，可以去网上搜索下载。也可以下载Github自己的[客户端](https://windows.github.com/)。
根据[Github Page](https://pages.github.com/)所说，你需要根据自己下载的东西进行操作。比如你选择了Github的客户端，你可以按照上面说的**Clone the repository**,一步一步的操作。
我个人是用的是**a terminal**，之后Clone 操作（选择一个自己喜欢的文件夹下进行clone操作）。我个人博客clone如下：
"git clone https://github.com/chrispher/chrispher.github.com.git"。
之后，我们会在本地的看到与自己项目名称一致的文件夹。

####2.3设置主题

我们可以去Jekyll自己收集的一些[主题](https://github.com/jekyll/jekyll/wiki/Sites)，这里罗列了许多主题，大家可以去点击看看页面的效果，如果喜欢，就去对应的source链接里，能够查看到该主题的所有代码！
我这里比较推荐大家使用博客主题Jekyll Light, 由[pexcn](https://github.com/pexcn/Jekyll-Light)设计，我在该版本上增加了**站内搜索**、**多种社交关注**、**标签页**、**页面标签链接**、**留言板**、**支付宝捐赠**、重设**百度统计**功能、删除了豆瓣阅读和其他一些细节上的修改。。

看中自己喜欢的主题之后，可以去主题项目下下载他的项目。比如到到我的[博客项目](https://github.com/chrispher/chrispher.github.com), 页面右侧有**Download ZIP**。下载到本地之后，解压之后可以看到各种乱七八糟的文件夹。大家可以把.git（默认文件是隐藏的，需要打开显示隐藏文件夹选项！）文件夹以外的所有东西拷贝到自己的项目下。

大家如果想关注本博客，可以在我的[博客项目](https://github.com/chrispher/chrispher.github.com)右上角，点击**Watch Star Fork**。其中Fork是把我的博客复制到自己的项目空间去。

这里简单的介绍主要文件夹的意思和内容：

- _config.yml:保存了站点的配置信息, 详细配置在这里, 中文翻译看这里.
- _includes:该目录存放可以与_layouts和_posts混合,匹配并重用的文件. 这里可以使页面的页脚、评论功能、百度统计等功能.
- _layout:该目录存放用来插入帖子的网页布局模板, 注意是模板, 具体数据在_posts中.
- _posts:发表的博文的内容, 其下文件的命名格式为: YEAR-MONTH-DAY-title.md(使用markdown语法写的文件), 另外还支持textile和html文件.
- res:这里存放了博客使用的各种字体、js、css等东西。不同的人存放的地点也可以不一致。也可以使用默认的字体（默认字体对中文支持不太好）
- _site:这里是Jekyll用以存放最终生成站点的根路径位置, 编译好的html文件都放在这里, 最好把这个目录加到 .gitignore 列表中.
- index.html:博客的首页
- CNAME 是你申请的域名，如果你没有申请域名并绑定，那么你需要删除这个文件！

对于其他的一些东西，大家慢慢摸索，用的多了就会懂了，也可以多去看看[Jekyll](http://jekyllcn.com/)官网。开始，最重要的是搭建起来，其他的慢慢调整！

####2.4设置博客

一般所需要做的核心设置在_config.yml 中，用文本打开：

    blog:
        name: chrispher guan       # 博客名称
        description: Data Science  # 博客描述
        title: Data Science        # 网页标题
        url: http://chrispher.github.com  # 博客地址，即你的项目名称
        duoshuo: chrispher2012            # 多说ID
        tongji: 3F27793c8b949a643c724f32bcf5058791 # 百度统计ID
    author:
        name: chrispher guan       # 作者名称
        email: chrispher2012@gmail.com # 邮箱地址
        weibo: 2917650677  # weibo ID
        github: chrispher  # github ID
        linkedin: chrispher-guan/5a/a68/6b8 # linkedIn ID
        gplus: 110552447039675960964  # G+ ID 
        logo: http://chrispher.github.com/images/op_we_are_brothers.png # logo地址

如果没有对应的账号，可以直接不填！如果填我的账号信息，那么你的博客就相当于我的一个子博客了，哈哈！

####2.5修改与提交

如果你都修改好了之后，你可以上传你的项目了。同样，如果你使用Github客户端，同步一下就可以了。我个人是terminal，需要使用以下几个命令。
以下是示范，井号后面是注释说明，不需要输入！可以参考一些简单[教程](http://rogerdudler.github.io/git-guide/index.zh.html)

    git add --all  # 添加所有文件
    git commit -a -m 'first commit' # 'first commit'表示你为这次提交写的备注，方便自己回顾和查看
    git push # 上传所有文件，之后输入自己的用户名和密码即可

之后，10min左右，你的博客就好建好了，在网址栏输入**chrispher.github.com**即可访问博客（注意用户名！）

其他的一些常用Git命令，建议大家去学习一些Git的基本操作[教程](http://git-scm.com/book/zh/v1)！当然，你可以不在乎乱七八糟的东西，专注于几个常用命令即可（除了上面提到的命令外，git pull表示把）。

###3.写作与格式

这里简单的介绍下如何利用markdown进行文章的写作。大家可以随意选择一个文本编辑器，这里我推荐使用Sublime Text2，关于sublime的一些常用设置可以参考我的博客[My sublime text2 setting](http://www.datakit.cn/blog/2014/08/12/My%20sublime%20setting.html)。

我们可以在"_posts"里随便的建立文件夹（一般按照自己的类别或者兴趣建立文件夹），也可以不建立。Jekyll支持多种格式的文本解析，这里指介绍markdown！新建文本文件，只有文件命名的规范是**2014-8-12-My sublime setting.md**, 即**日期-文章标题.md**，注意markdown文件以md或markdown结尾。

在文章开头是关于文章主题的设置，如下(井号后面是注释说明):

    ---                   # 默认文章主题设置起始标识符
    layout: post          # 使用post模板，在_layouts里多个模板可以用
    title: My sublime text2 setting #文章标题
    comments: true        # 增加评论功能
    category: Application # 设置文章的类别
    tags: [sublime, setting] # 设置文章的tag，方便自己以后搜索用
    ---          # 默认结束标识符

windows下sublime text2的一些设置和调整 #正文


Makrdown的简单语法,可以参考[Markdown 语法说明简体中文版](http://wowubuntu.com/markdown/)

###4.写作的一些技巧

这里额外讲一下几个我在博客里比较常用的语法；

####4.1添加目录
更具基本的语法我们知道中括号[] 后面跟着小括号() 表示对中括号内容做了超链接，而链接地址是小括号内容。目录就是根据这个思路去做的。即如下：

`### 目录`  
`- [1.github博客概述]（#1.github博客概述）`

之后在每个需要添加的目录地方，增加
`### 1.github博客概述`

这里是使用了html的一些语法，注意内容的一致性。另外，网上也也其他的不是有html语法的目录创建方式。但是，有些Jekyll不支持，比如直接使用TOC。也有自动侧边栏生成，可以自行搜索"Markdown自动生成侧边栏目录"等内容。

另外，如果你使用的是`markdown: kramdown`，那么你可以在开头加入下面几行，实现自动的目录。

    ###目录
    {:.no_toc}

    * 目录
    {:toc}


####4.2插入图片

官方的语法是 `![Alt text](image_path "Optional title")` ，这里是一个惊叹号!，接着一个方括号，里面放上图片的替代文字
接着一个普通括号，里面放上图片的网址，最后还可以用引号包住并加上 选择性的 'title' 文字。这种方式不能自动的适应屏幕，所以我个人比较喜欢适应html的格式，即` <img src="img_path" height="100%" width="100%">` 这里的100%是指相对屏幕的大小。

####4.3文章简介

在博客的首页，通常只显示了文章的一部分内容，这是怎么实现的呢？一般而言，我们写作时，会在开头写一下整篇文章的概述，之后在增加一行`＜！－－ more --＞`，那么一般显示的时候就只显示`＜！－－ more --＞`之前的文本，只有点击阅读进入这篇文章才能看到全部内容。当然，这里也是跟html语法相关的，在index.html里的
＞ {{ post.content ｜ split:＇＜！－－ more --＞'｜ first }}
这里不细说其他html语法，毕竟我不是做web的，只是了解一点点对自己有价值的部分。

####4.4代码高亮

代码高亮语法是：在代码开始的地方标注 `｛％ highlight python ％｝` ，在代码结束的地方标注 `｛％ endhighlight ％｝`，那么中间的代码就是使用了Python的代码高亮风格！

**注意：有些时候我们用的字符和markdown或者系统的字符重合，导致编译错误，我们可以用全角来替换，本文写作技巧中，部分符号用了全角替换！**

另外需要注意，不同的markdown解析器，使用的语法也有一些差距。有些markdown的编辑器比如本文用的kramdown，可以使用波浪号来表示代码块等等。具体的语法扩展可以参考官网。