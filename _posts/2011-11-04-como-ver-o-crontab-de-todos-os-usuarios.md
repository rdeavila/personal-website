---
layout: post
title: Como ver o Crontab de todos os usuários
date: 2011-11-04 16:08:00.000000000 -02:00
published: true
---
O comando é bastante simples, e funciona tanto no Linux quanto no Mac OS X:

{% highlight bash %}
for user in $(cut -f1 -d: /etc/passwd); do echo $user; sudo crontab -u $user -l; done
{% endhighlight %}
