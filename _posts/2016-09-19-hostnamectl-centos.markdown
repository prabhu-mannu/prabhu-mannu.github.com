---
layout: post
title:  "How to hostname on redhat 7 "
date:   2016-09-19 +0800
categories:
- linux
- system administration
tags:
- linux
- centos
- redhat
- hostname
- hostnamectl
---

To change the hostname of the redhat 7 or centos 7 system

hostnamectl command can be used

status flag gives the full details of the hostname

{% highlight shell %}
[prabhu@localhost ~]$ hostnamectl status
   Static hostname: localhost.localdomain
         Icon name: computer-laptop
           Chassis: laptop
        Machine ID: eae60944bb9d4ace827fac49d8b6994f
           Boot ID: d80f021a3e2949399a09af0ae523fd5e
  Operating System: Red Hat Enterprise Linux
       CPE OS Name: cpe:/o:redhat:enterprise_linux:7.3:GA:server
            Kernel: Linux 3.10.0-327.36.2.el7.x86_64
      Architecture: x86-64
{% endhighlight %}

**set-hostname** flag sets the hostname 
**--static** flag indicates the static hostname
**--pretty** flag indicates the description of the host

{% highlight shell %}
[prabhu@localhost ~]$ sudo hostnamectl set-hostname "untrinilium.scriptbyte.local" --static
[prabhu@localhost ~]$ sudo hostnamectl set-hostname "my personal workstation" --pretty
{% endhighlight %}
