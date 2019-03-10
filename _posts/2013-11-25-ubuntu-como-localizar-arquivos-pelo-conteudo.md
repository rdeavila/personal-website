---
layout: post
title: 'Ubuntu: como localizar arquivos pelo conteúdo'
date: 2013-11-25 12:42:00.000000000 -02:00
---
Esta dica funciona tanto no Ubuntu quanto no OS X.

{% highlight bash %}
grep -lr "texto a encontrar" *.txt
{% endhighlight %}

Uma breve explicação, em Português, da linha acima:

* lista arquivos que contenham um padrão
* de forma recursiva
* Em todos os arquivos com nome `*.txt`

Fonte: [Quickly find any text string in any set of files](http://hints.macworld.com/article.php?story=20001105214242629)
