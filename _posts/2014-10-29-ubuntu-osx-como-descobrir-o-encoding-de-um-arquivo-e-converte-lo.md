---
layout: post
title: 'Ubuntu / OSX: Como descobrir o encoding de um arquivo, e convertê-lo.'
date: 2014-10-29 16:19:04.000000000 -02:00
---
Para descobrir o encoding de um arquivo:

{% highlight bash %}
$ file -I original.csv
original.csv: text/plain; charset=iso-8859-1
{% endhighlight %}

No exemplo, o arquivo tem o encoding `ISO-8859-1`. Agora, se eu quiser converter este arquivo para `UTF-8`, por exemplo, o comando é o seguinte:

{% highlight bash %}
$ iconv -f iso-8859-1 -t utf-8 < original.csv > copia.csv
{% endhighlight %}

Depois, se necessário, [dá pra retirar os caracteres de fim de linha do windows].

Fonte: [uso do comando file], e [uso do comando iconv].

[uso do comando file]: http://superuser.com/a/152001
[uso do comando iconv]: http://superuser.com/a/151980
[dá pra retirar os caracteres de fim de linha do windows]: /2014/10/29/ubuntu-os-x-como-remover-as-quebras-de-linha-do-windows-de-um-arquivo
