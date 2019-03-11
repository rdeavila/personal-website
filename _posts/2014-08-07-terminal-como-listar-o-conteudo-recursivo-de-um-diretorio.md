---
layout: post
title: 'Terminal: Como listar o conteúdo recursivo de um diretório'
date: 2014-08-07 17:50:17.000000000 -03:00
---
Para listar recursivamente o conteúdo de um diretório, usando o `ls`, o comando é este:

{% highlight bash %}
ls -R /diretorio | awk '
/:$/&&f{s=$0;f=0}
/:$/&&!f{sub(/:$/,"");s=$0;f=1;next}
NF&&f{ print s"/"$0 }'
{% endhighlight %}

Além de mostrar o conteúdo de forma recursiva, este comando também mostra o caminho completo dos arquivos, e não apenas os nomes.

Este comando foi testado no Ubuntu e no OS X.

Fonte: [AskUbuntu.com](http://askubuntu.com/a/12880)
