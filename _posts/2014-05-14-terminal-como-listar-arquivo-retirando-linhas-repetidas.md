---
layout: post
title: 'Terminal: como listar arquivo retirando linhas repetidas'
date: 2014-05-14 15:49:15.000000000 -03:00
---
Para listar o conteúdo de um arquivo, retirando as linhas repetidas, basta passar a saída do comando pelo `awk`:

{% highlight bash %}
cat arquivo.log | awk '!a[$0]++'
{% endhighlight %}

Se quiser, ainda dá para [listar apenas uma coluna do arquivo](/2014/05/14/terminal-como-listar-apenas-uma-coluna-de-um-arquivo).
