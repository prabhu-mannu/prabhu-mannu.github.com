---
layout: post
title:  "How to install oracle Java/JDK 1.8 on Redhat 7.2"
date:   2016-08-23 +0800
categories:
- linux
- java
- jdk 1.8
tags:
- linux
- redhat 
- oracle java
- jdk 1.8
---

To install java from oracle need to enable the repo via `subscription-manager`

{% highlight shell %}
subscription-manager repos --enable=rhel-7-server-thirdparty-oracle-java-rpms
{% endhighlight %}

Now to install oracle **Java jdk 1.8.0** 

{% highlight shell %}
yum install java-1.8.0-oracle java-1.8.0-devel -y
{% endhighlight %}