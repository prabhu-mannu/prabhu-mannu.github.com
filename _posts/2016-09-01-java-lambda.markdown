---
layout: post
title:  "JAVA 8 lambda: print list"
date:   2016-09-01 +0800
categories:
- Java 8
- Lambda
- ArrayList
tags:
- Java 8
- Lambda
- ArrayList
---

{% highlight java %}
public class Test {
    public static void main(String[]args){

        List<String> list=new ArrayList<>();
        list.add("Item1");
        list.add("Item2");
        list.add("Item3");
        list.add("Item4");
        //Simple online to sout the list works the same for Objects by using toString
        list.forEach(System.out::println);
    }
}
{% endhighlight %}
