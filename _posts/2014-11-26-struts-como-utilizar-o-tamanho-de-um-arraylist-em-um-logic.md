---
layout: post
title: 'Struts: Como utilizar o tamanho de um ArrayList em um logic'
date: 2014-11-26 11:38:15.000000000 -02:00
---
Como utilizar o `size()` de um `ArrayList` em um bloco `logic`, como, por exemplo, um `<logic:greaterThan/>`?

Basta utilizar um `bean:size`...

{% highlight xml linenos %}
<bean:size id="tamanho" name="meuArrayList"/>
<logic:greaterThan name="tamanho" value="0">
  <!-- Minha lógica -->
</logic:greaterThan>
{% endhighlight %}

Fonte: [Struts logic tags if ArrayList size](http://www.theserverside.com/news/thread.tss?thread_id=32090)
