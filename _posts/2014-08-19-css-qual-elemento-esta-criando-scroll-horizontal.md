---
layout: post
title: 'CSS: Qual elemento está criando scroll horizontal?'
date: 2014-08-19 17:19:20.000000000 -03:00
---
Se, ao criar uma página, você percebeu que ela ficou com uma incômoda barra de rolagem horizontal, você pode executar o seguinte código no console do seu navegador, para descobrir quem é o culpado:

{% highlight javascript %}
var docWidth = document.documentElement.offsetWidth;

[].forEach.call(
  document.querySelectorAll('*'),
  function(el) {
    if (el.offsetWidth > docWidth) {
      console.log(el);
    }
  }
);
{% endhighlight %}

Os culpados irão aparecer no Console...

![](/assets/scroll-horizontal.png)

Fonte: [Finding/Fixing Unintended Body Overflow](http://css-tricks.com/findingfixing-unintended-body-overflow/)
