---
layout: post
title: 'OS X: Como executar várias cópias de um programa'
date: 2014-06-27 12:00:32.000000000 -03:00
---
Já comentei por aqui [como fazer isso no Ubuntu com Unity](http://www.avila.net.br/2011/10/21/como_executar_varias_copias_de_um_programa_via_lancador_do_unity/). Mas agora tive o mesmo problema, no OS X.

Para executar o mesmo programa mais de uma vez, precisamos recorrer ao Terminal. Desse jeito:

{% highlight bash %}
open -n -a "Nome da Aplicação"
{% endhighlight %}

Este comando fala para o sistema abrir (`open`) uma nova instância (`-n`) da aplicação (`-a`) que está escrita entre aspas.

Existem vários motivos para que o OS X não permita de forma fácil a execução de várias instâncias de um programa ao mesmo tempo. Por exemplo, alguns programas usam a mesma base central de dados; usar mais de uma instância pode levar a inconsistências.

Mas em casos como o do Eclipse (que é o programa que eu preciso rodar), isso não é um problema. Até porque o Eclipse mesmo se encarrega de não executar caso você tente abrir duas vezes o mesmo workspace.
