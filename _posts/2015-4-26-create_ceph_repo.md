---
layout: post
title: CREATE_CEPH_REPO 
date: 2015-04-26 01:05:19 
category: storage 
---
#centos 7创建ceph本地源

###安装工具包
{% highlight java %}
sudo yum install yum-utils createrepo yum-plugin-priorities
{% endhighlight %}
###修改yum.conf配置
{% highlight java %}
sudo sed -i "s/keepcache=0/keepcache=1/g" /etc/yum.conf
{% endhighlight %}
###更新源，导入ceph源并安装相关依赖包
{% highlight java %}
sudo rpm --import 'https://ceph.com/git/?p=ceph.git;a=blob_plain;f=keys/release.asc'
sudo rpm -Uvh http://mirrors.yun-idc.com/epel/7/x86_64/e/epel-release-7-5.noarch.rpm
sudo yum install snappy leveldb gdisk python-argparse gperftools-libs -y
sudo rpm -Uvh http://ceph.com/rpm-dumpling/el7/noarch/ceph-release-1-0.el7.centos.noarch.rpm
sudo yum install ceph-deploy -y
sudo yum install ceph -y
sudo yum install btrfs-progs
{% endhighlight %}
###centos 7默认没有开启ceph_fs内核，需要更改内核
{% highlight java %}
sudo rpm --import https://www.elrepo.org/RPM-GPG-KEY-elrepo.org
sudo rpm -Uvh http://www.elrepo.org/elrepo-release-7.0-2.el7.elrepo.noarch.rpm
sudo yum install -y yum-plugin-fastestmirror
sudo yum --enablerepo=elrepo-kernel install kernel-ml kernel-ml-devel
sudo grub2-set-default 0
sudo init 6
{% endhighlight %}
###copy packages
{% highlight java %}
sudo mkdir -p /root/ceph
sudo find /var/cache/yum/x86_64/7/* -name  “*rpm” | xargs -I{} cp {} /root/ceph.repo
{% endhighlight %}
###创建包依赖关系
{% highlight java %}
sudo createrepo /root/ceph/
{% endhighlight %}
###创建本地源
{% highlight java %}
sudo vim /etc/yum.repo/ceph.repo
[ceph_mtanlee]
name=ceph_mtanlee
baseurl=file:///root/ceph
enabled=1
gpgcheck=0
sudo yum repolist
{% endhighlight %}
###原创转载请注明出处:<a herf='http://mtanlee.com'>www.mtanlee.com</a>
