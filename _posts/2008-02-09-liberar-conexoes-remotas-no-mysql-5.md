---
layout: post
title: Liberar conexões remotas no MySQL 5
date: 2008-02-09 20:52:00.000000000 -02:00
published: true
---
Veja o que fazer caso recebeu o erro `is not allowed to connect` ao conectar de um host remoto.

Esta é uma dica rápida: se depois de trocar o bind do mysql 5, você ainda não conseguir conectar remotamente em um server, faça o seguinte em um terminal:

{% highlight bash %}
% mysql -u root -p
mysql> use mysql;
mysql> grant all privileges on *.* to USERNAME@'%' identified by 'SENHA' with grant option;
mysql> insert into host values('HOSTNAME', '%', 'Y', 'Y', 'Y', 'Y', 'Y','Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y');
mysql> flush privileges;
mysql> exit
{% endhighlight %}

Nem preciso dizer que você deve fazer isto apenas em último caso, se precisar mesmo acessar este servidor remotamente.
