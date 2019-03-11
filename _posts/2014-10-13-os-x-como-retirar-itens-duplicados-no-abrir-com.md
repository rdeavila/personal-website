---
layout: post
title: 'OS X: Como retirar itens duplicados no "Abrir Com"'
date: 2014-10-13 16:09:51.000000000 -03:00
---
Se o seu menu "Abrir Com" tem várias entradas duplicadas, você pode rodar este comando no Terminal, para que a lista seja refeita, e os duplicados desapareçam.

{% highlight bash %}
/System/Library/Frameworks/CoreServices.framework/Frameworks/LaunchServices.framework/Support/lsregister -kill -r -domain local -domain system -domain user
{% endhighlight %}

Aguarde alguns instantes, porque este comando pode demorar um pouco até terminar.

Fonte: [Rebuild LaunchServices to Fix Duplicate Entries in OS X’s ‘Open With’ Menu](http://www.tekrevue.com/tip/rebuild-launchservices-fix-duplicate-entries-os-xs-open-menu/)
