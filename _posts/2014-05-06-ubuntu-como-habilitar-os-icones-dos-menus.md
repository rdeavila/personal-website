---
layout: post
title: 'Ubuntu: como habilitar os ícones dos menus'
date: 2014-05-06 17:02:32.000000000 -03:00
---
Por padrão os ícones de menu ficam desabilitados no Ubuntu, desde a versão 12.10. Mas, se você quiser habilitar estes ícones, você pode fazê-lo usando o `dconf-tools`. Uma vez instalado, você vai encontrar as opções de interface em `org.gnome.desktop.interface`. As configurações específicas de ícones em menus ficam em `menus-have-icons` e `buttons-have-icons`.

Ambos podem ser alterados pelo terminal, com os comandos abaixo:

{% highlight bash %}
gsettings set org.gnome.desktop.interface menus-have-icons true
gsettings set org.gnome.desktop.interface buttons-have-icons true
{% endhighlight %}

Após habilitados, os ícones voltam a aparecer nos menus, desse jeito:

![](/content/images/2014/May/EspaC-o-de-Trabalho-1_001-1.png)

Fonte: [GMJ Designs]

[GMJ Designs]: http://www.gmjjavadesigns.com/content/ubuntu-1210-how-turn-menu-icons
