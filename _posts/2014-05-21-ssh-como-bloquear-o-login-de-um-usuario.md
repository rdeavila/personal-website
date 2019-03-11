---
layout: post
title: 'SSH: Como bloquear o login de um usuário'
date: 2014-05-21 16:28:14.000000000 -03:00
---
O OpenSSH tem duas diretivas para bloquear o acesso de um (ou mais) usuários. Estas diretivas precisam ser colocadas no arquivo `/etc/ssh/sshd_config`.

Por usuário:

{% highlight apacheconf %}
DenyUsers usuario1 usuario2 usuario3
{% endhighlight %}

Por grupo:

{% highlight apacheconf %}
DenyGroups grupo1 grupo2 grupo3
{% endhighlight %}

Salve o arquivo, e reinicie o sshd

{% highlight bash %}
sudo service ssh restart
{% endhighlight %}
