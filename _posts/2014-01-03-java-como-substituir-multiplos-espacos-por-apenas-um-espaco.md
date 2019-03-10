---
layout: post
title: 'Java: Como substituir múltiplos espaços por apenas um espaço'
date: 2014-01-03 10:02:00.000000000 -02:00
---

{% highlight java %}
"espaços   mútiplos  ".trim().replaceAll(" +", " ");
{% endhighlight %}

Para testar este código, [utilize o CodingGround].

[utilize o CodingGround]: http://www.tutorialspoint.com/compile_java_online.php
