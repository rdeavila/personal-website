---
layout: post
title: 'Curl: Como continuar (resume) um download já iniciado'
date: 2013-12-06 22:40:00.000000000 -02:00
---

{% highlight bash %}
curl -C - -o arquivo_ja_salvo 'www.example.com/caminho/do/arquivo_ja_salvo'
{% endhighlight %}
