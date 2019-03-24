---
layout: post
title: 'Ubuntu: Como fazer o Déjà Dup guardar backups por menos de seis meses'
date: 2014-04-29 13:38:43.000000000 -03:00
---
Você precisa modificar a configuração no Dconf, no caminho `/org/gnome/deja-dup/`, schema `org.gnome.DejaDup`, chave `delete-after`. Ali docê coloca o número de dias que você quer manter os arquivos de backup na localização configurada.

Por exemplo, se você quer guardar seus backups por 2 meses (ou 60 dias), execute este comando no Terminal:

{% highlight bash %}
gsettings set org.gnome.DejaDup delete-after 60
{% endhighlight %}

Você também pode fazer isso usando o `dconf-editor`:

![](/assets/1NOxS.png)

O utilitário Déjà Dup vai fazer a alteração instantaneamente, adicionando este número de dias como uma opção:

![](/assets/YpdDf.png)

Detalhe importante: o Déjà Dup, internamente, tenta manter pelos menos dois backups completos no local de armazenamento. Por isso, se você definir um valor menor que 6 meses na chave `delete-after`, você também precisará colocar a metade deste valor na chave `full-backup-period`.

Fonte e imagens: [AskUbuntu]

[AskUbuntu]: http://askubuntu.com/a/246708
