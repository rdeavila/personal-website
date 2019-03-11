---
layout: post
title: 'Ubuntu: como montar um arquivo ISO?'
date: 2014-08-08 16:01:51.000000000 -03:00
---
Se você tem um arquivo .iso, e quer montá-lo como se fosse uma unidade de DVD/CD, você pode fazer o seguinte:

1. Crie um diretório, que servirá como ponto de montagem:

{% highlight bash %}
sudo mkdir /media/iso
{% endhighlight %}

1. Monte a ISO neste diretório:

{% highlight bash %}
sudo mount -o loop SEU_ARQUIVO.ISO /media/iso
{% endhighlight %}

Eu sei que existem ferramentas no Gnome que podem fazer isso pra você. Mas esta solução é perfeita, caso esteja usando um servidor.

Ah, claro. Para desmontar, execute:

{% highlight bash %}
sudo umount /mnt/iso
{% endhighlight %}

Fonte: [AskUbuntu](http://askubuntu.com/a/193632)
