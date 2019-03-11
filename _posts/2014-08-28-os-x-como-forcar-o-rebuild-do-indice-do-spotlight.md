---
layout: post
title: 'OS X: Como forçar o rebuild do índice do Spotlight'
date: 2014-08-28 16:27:58.000000000 -03:00
---
Após fazer mudanças nas configurações do Spotlight, pode demorar um pouco até que elas sejam aplicadas. Isto acontece porque, após as mudanças, o Spotlight precisa refazer o seu índice.

Se ele não começou a reindexar os seus discos após uma mudança na configuração, você pode forçar o OS X com o seguinte comando:

{% highlight bash %}
sudo mdutil -E /
{% endhighlight %}

De acordo com a man-page, a opção `-E` faz o seguinte:

{% highlight text %}
     -E  This flag will cause each local
         store for the volumes indicated to
         be erased.  The stores will be
         rebuilt if appropriate.
{% endhighlight %}
