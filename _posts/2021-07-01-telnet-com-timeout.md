---
layout: post
title: "Como executar telnet com timeout"
date: 2021-07-01 08:50:42.000000000 -03:00
published: true
---

Para executar o `telnet` com timeout de 3 segundos:

{% highlight bash %}
echo quit | timeout --signal=9 3 telnet [HOST] [PORTA]
{% endhighlight %}

Resposta:

{% highlight bash %}
$ echo quit | timeout --signal=9 3 telnet google.com 6969
Trying 172.217.28.14...
Killed
{% endhighlight %}
