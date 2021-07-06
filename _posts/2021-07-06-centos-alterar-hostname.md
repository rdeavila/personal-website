---
layout: post
title: "CentOS: Como alterar o hostname"
date: 2021-07-06 12:50:42.000000000 -03:00
published: true
---

Para alterar o hostname de um servidor:

{% highlight bash %}
# Altera o nome do host, persistindo após o restart
sudo hostnamectl set-hostname [HOST]
# Altera o nome do host, antes do restart
sudo hostnamectl --transient set-hostname [HOST]
# Altera o nome do host no arquivo de hosts
sudo vim /etc/hosts
{% endhighlight %}
