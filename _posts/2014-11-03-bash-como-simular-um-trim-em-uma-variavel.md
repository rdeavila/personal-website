---
layout: post
title: 'Bash: como simular um trim() em uma variável'
date: 2014-11-03 15:28:50.000000000 -02:00
---
Em Java, trim() retira os espaços no início e no fim de uma String. Como fazer o mesmo, em uma String que está dentro de uma variável, usando Bash Script?

{% highlight bash %}
echo " teste teste teste " | sed -e 's/^ *//' -e 's/ *$//'
{% endhighlight %}

Fonte: Resposta do usuário [MattyV](http://stackoverflow.com/users/389877) no [StackOverflow](http://stackoverflow.com/a/3232433).
