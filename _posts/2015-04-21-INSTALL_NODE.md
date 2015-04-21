---
layout: post
title: INSTALL_NODEJS 
date: 2015-04-21 19:53:33 
category: jekyll 
---
之前找了挺多的资料关于安装node.js多不怎么给力，发现github上的源下载速度挺快的，在此介绍centos下安装node.js

###设置传输源
{% highlight java %}
 sudo curl -sL https://rpm.nodesource.com/setup | bash -
{% endhighlight %}
###安装node
{% highlight java %}
 sudo yum install -y node.js
{% endhighlight %}
###检测是否安装成功
{% highlight java %}
 sudo node -v
{% endhighlight %}
###参考资料：<a herf='https://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager#debian-and-ubuntu-based-linux-distributions'>INSTALL_NODEJS</a>
