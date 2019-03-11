---
layout: post
title: 'Ubuntu: como corrigir o erro “Setting locale failed”'
date: 2014-05-08 09:24:10.000000000 -03:00
---
Quando você executa comandos como `a2dismod` ou `a2dissite`, você pode acabar se deparando com o erro `Setting locale failed`, do Perl. Para resolver este problema, são 3 comandos simples:

{% highlight bash %}
locale-gen pt_BR.UTF-8
locale-gen en_US.UTF-8
dpkg-reconfigure locales
{% endhighlight %}
