---
layout: post
title: 【译文】Jekyll的YAML前置数据
description: 这是Jekyll官方Wiki上关于YAML前置数据的说明，希望对大家有所帮助。
keywords: Jekyll,YAML Front Matter,Wiki
category: 翻译
tags: Jekyll,YAML,Wiki,翻译
---

> 原文地址:[https://github.com/mojombo/jekyll/wiki/YAML-Front-Matter](https://github.com/mojombo/jekyll/wiki/YAML-Front-Matter)

所有包含[YAML](http://yaml.org/)前置数据块的文件都会被**Jekyll**当做特殊文件来处理。这些前置数据必须存在于文件的首部，他们的格式是这样的：

{% highlight yaml %}
---
layout: post
title: Blogging Like a Hacker
---
{% endhighlight %}

在三条虚线之间，你可以设置一些预定义的变量（可以查看下面的参考说明）或者是你自己定义的变量。

注意：这很**重要**（尤其是对Windows用户）

当你使用`UTF-8`编码来编辑你的文件时，请确保没有`BOM`的头部字符在你的文件中，否则整个都会奔溃。

# 预定义的全局变量 #

|-------------------------+------------------------------------------------------------------------------------------------------------------|
|    **变量** 						|																**描述**																																			     |
|:------------------------|:-----------------------------------------------------------------------------------------------------------------|
|			`layout`						|这个变量是用来设置选用的模板文件。使用模板文件的文件名，但不包括扩展名，模板文件必须存在于 `_layout`目录中。      |
|			`permalink`    	    |如果你需要你的Url地址和默认的/年份/月份/日期/标题.html不同，那你就需要设置这个选项，它将会当做最终的URL地址。     |
|			`published` 	      |当站点生成时，如果你不希望这篇文章显示出来，那就应该把这个变量设置为false																			   |
|	`category`/`categories` |除了你可以把文章放在归档文件夹中，你还可以为文章设置一个或多个类别。当网站生成时，这些文章将会表现得和真的属于这些分类一样。这些类别可以通过[YAML列表](http://en.wikipedia.org/wiki/YAML#Lists)来设置，或者也可以通过一个用空格分隔的字符串来设置。															     |
| 		`tags`							|类似于分类，一个文章可以拥有一个或多个标签。同样和分类类似，标签也可以通过YAML列表或一个用空格分隔的字符串来设置。|
|-------------------------+------------------------------------------------------------------------------------------------------------------|

# 自定义数据 #

在转换过程中，所有在前置数据中的非预定义变量都会被一起提交给**Liquid**模板引擎。举例来说，如果你设置了变量:title，你可以在你的布局模板文件中使用这个变量来设置页面的标题：

{% highlight html %}
<title> { { page.title } } </title>
{% endhighlight %}

#为文章预定义的前置数据#

下面是文章可用的前置数据变量：

|-------------+----------------------------------------------------------------------|
|   **变量**  |        **描述**                                                      |
|:------------|:---------------------------------------------------------------------|
|     `date`  |这个日期变量将会覆盖文件名中的日期，这个变量能够用来确保文章的正确排序|
|-------------+----------------------------------------------------------------------|
