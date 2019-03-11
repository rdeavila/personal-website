---
layout: post
title: 'Terminal: como listar apenas uma coluna de um arquivo'
date: 2014-05-14 15:46:30.000000000 -03:00
---
O comando abaixo separa as linhas de um log usando `:` como divisor, e mostra apenas a quarta coluna:

{% highlight bash %}
cat arquivo.log | cut -d":" -f4
{% endhighlight %}

Se quiser retirar os repetidos, é só passar a saída pelo `awk`:

{% highlight bash %}
cat arquivo.log | cut -d":" -f4 | awk '!a[$0]++'
{% endhighlight %}
