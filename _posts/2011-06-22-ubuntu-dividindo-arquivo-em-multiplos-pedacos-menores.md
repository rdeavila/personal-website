---
layout: post
title: 'Ubuntu: Dividindo arquivo em múltiplos pedaços menores'
date: 2011-06-22 18:25:00.000000000 -03:00
---
Para dividir um arquivo em vários pedaços menores, use:

{% highlight bash %}
split --verbose --bytes=<TAMANHO> -d <ARQUIVO> <PREFIXO>
{% endhighlight %}

onde:

* `--verbose` mostra na tela cada vez que ele começa um novo arquivo.
* `--bytes=<TAMANHO>` é o tamanho de cada pedaço, em bytes, ou um inteiro seguido de K, M, G, T, P, E, Z, Y
* `-d` Informa que é pra usar um sufixo numérico no fim do arquivo.
* `<ARQUIVO>` Obviamente, o arquivo a ser dividido.
* `<PREFIXO>` Como deve ficar o nome dos pedaços.

Uma imagem ISO poderia ser dividida em pedaços de 1Gb cada, desta forma:

{% highlight bash %}
split --verbose --bytes=1G -d imagem.iso img
{% endhighlight %}

A resposta do comando seria a seguinte:

{% highlight bash %}
criando arquivo "img00"
criando arquivo "img01"
criando arquivo "img02"
criando arquivo "img03"
criando arquivo "img04"
{% endhighlight %}

Para juntar estes arquivos novamente, use:

{% highlight bash %}
cat img00 img01 img02 img03 img04 > imagem.iso
{% endhighlight %}
