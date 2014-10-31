---
layout: post
title: jekyll中文问题的解决方法
---
## jekyll中文问题的解决方法

花了4个晚上终于把jekyll的中文问题解决了，其中放弃了一次想改投octopress，但octopress的模板真是太少了，关键还没有好看的。想着再研究一天的态度，解决还搞出来了。
> 
1. jekyll 1.4.3
2. ruby 2.1.1
3. jekyll模板 [scribble](http://scribble.muan.co)

在我安装的时候始终出现的问题就是这个信息

```
invalid byte sequence in UTF-8
```

在网上找了2个晚上，基本上发现的修改方法都是说修改convertible.rb这个文件，因为liquid这个gem默认是使用ascii进行的本地文件读取。
但从[stackoverflow](https://github.com/jekyll/jekyll/pull/999)上面也找了一些内容，表明已经可以在新的版本上是解决这个问题的。

### 发现问题
在stackoverflow上查找的时候，看到一些系统编码和编辑器编码可能也会产生这个问题。我是使用vim进行开发的，查看一下我的vimrc就傻了，用的是gbk而不是utf-8。

另外一个原因，我的目的是把它放在github的page上面，而github page上面的jekyll环境我是不能修改的，所以这个方案对于我来说基本不可行了

把它修改成utf-8就直接搞定了这个问题。

```
settings fileencodings=ucs-bom,utf-8,cp936
set fileencoding=utf-8
```
