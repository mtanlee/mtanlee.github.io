---
layout: post
title: rdo-quick-start
date: 2015-04-21  01:38:49
category: "openstack"
---

本篇文章对于小白比较有用，能够快速的体验一下openstack。

###1.更新packages
{% highlight java %}
sudo yum update -y
{% endhighlight %}
###2.安装RDO源
{% highlight java %}
sudo yum install -y https://rdo.fedorapeople.org/rdo-release.rpm
{% endhighlight %}
###***两种安装模式***

###3.1.安装all-in-one
{% highlight java %}
sudo packstack --allinone
{% endhighlight %}

###3.2.根据需求修改配置文件

{% highlight java %}
sudo packstack --gen-answer-file /root/answers.txt
sudo vim answers.txt ;可将单节点改为多节点
[general]

...

CONFIG_CONTROLLER_HOST=$ip_controller;控制节点ip地址

CONFIG_COMPUTE_HOSTS=$ip_compute     ;计算节点ip地址

CONFIG_NETWORK_HOSTS=$ip_network     ;网络节点ip地址

...

sudo packstack --answer-file /root/answers.txt
{% endhighlight %}
