---
layout: post
title: 'Ubuntu / OS X: Como remover as quebras de linha do Windows de um arquivo'
date: 2014-10-29 16:25:02.000000000 -02:00
---
Ao abrir um arquivo texto criado no Windows, as quebras de linha podem aparecer como caracteres estranhos, quando o arquivo é editado no Ubuntu ou no OS X.

![](/assets/quebras-de-linha-windows.png)

Para corrigir isto, basta passar o arquivo pelo comando `dos2unix`:

{% highlight bash %}
$ dos2unix original.csv
{% endhighlight %}

Este executável não vem instalado por padrão, nem no Ubuntu, nem no OS X. Para instalar:

* No Ubuntu:

{% highlight bash %}
$ sudo apt-get install -y dos2unix
{% endhighlight %}

* No OS X (você precisará instalar o [homebrew] antes):

{% highlight bash %}
$ brew install dos2unix
{% endhighlight %}

[homebrew]: http://brew.sh/index_pt-br.html
