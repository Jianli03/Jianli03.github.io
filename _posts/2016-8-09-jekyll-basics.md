---
layout: single
title: "Jekyll Basics"
---
 
 {% include base_path %}
 
这几天终于弄明白了怎么在Github的pages建立个人博客。 因为好高骛远，使用了mmistake的模版项目，fork下来一大堆东西，不知道怎么入手。
GitHub pages为了提供对HTML内容的支持，选择了Jekyll作为模板系统。
Jekyll是一个强大的静态模板系统，所以先搞清Jekyll怎么工作很有必要。

### 其实Jekyll本身的结构并不复杂， 如下：
* _config.yml
* _includes
* _layouts
* -----default.html
* -----post.html
* _posts
* -----2007-10-29-why-every-programmer-should-play-nethack.textile
* -----2009-04-26-barcamp-boston-4-roundup.textile
* _site
* -----index.html

### 简单介绍一下他们的作用：

##### _config.yml
配置文件，参考[这里](https://mmistakes.github.io/minimal-mistakes/docs/configuration/)进行设置，设置之后就不用关心了。

#####  _includes
存放一些小的可复用的模块，比如header footer 每个页面都会引入的，方便通过{ % include file.ext % }（去掉前两个{中或者{与%中的空格，下同）灵活的调用。这条命令会调用_includes/file.ext文件。

##### _layouts
这是模板文件存放的位置。模板通过YAML front matter来定义， 设置的话参考[这里](https://mmistakes.github.io/minimal-mistakes/dolayouts/)。

##### _posts
看名字就知道是你的博客正文存放的文件夹。命名规定，必须是YYYY-MM-DD-artical-title.MARKUP这样的形式，MARKUP是你所使用标记语言的文件后缀名，一般直接就是md, 也可以根据_config.yml中设定的链接规则灵活调整。 文章的日期和标记语言后缀与文章的标题的独立的。

##### _site
这个是Jekyll生成的最终的文档，不用去关心。有高人建议放到.gitignore文件中忽略它。

<a href="{{ site.baseurl }}/index.html">Go back</a>
