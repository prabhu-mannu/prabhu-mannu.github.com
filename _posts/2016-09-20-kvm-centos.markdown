---
layout: post
title:  "How to setup kvm on redhat 7 "
date:   2016-09-20 +0800
categories:
- linux
- kvm setup
tags:
- linux
- centos
- redhat
- kvm setup
---

{% highlight shell %}
[prabhu@localhost ~]$ sudo yum groupinfo  "Virtualization Host"
Failed to set locale, defaulting to C
Loaded plugins: product-id, search-disabled-repos, subscription-manager

Environment Group: Virtualization Host
 Environment-Id: virtualization-host-environment
 Description: Minimal virtualization host.
 Mandatory Groups:
   +base
   +core
   +virtualization-hypervisor
   +virtualization-tools
 Optional Groups:
   +debugging
   +network-file-system-client
   +remote-system-management
   +virtualization-platform
[prabhu@localhost ~]$ yum groupinstall "Virtualization Host" -y
{% endhighlight %}
