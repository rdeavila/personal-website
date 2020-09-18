---
layout: post
title: "Como ler o tempo de resposta de um site usando cUrl"
date: 2020-09-18 08:50:42.000000000 -03:00
published: true
---

Essa é simples.

{% highlight bash %}
curl -o /dev/null -s -w %{time_total}\\n https://rodrigoavila.dev
{% endhighlight %}

Resposta (em segundos):

{% highlight bash %}
0,536215
{% endhighlight %}

Se desejar, ainda dá pra obter outros tipos de tempo da requisição.

{% highlight bash %}
curl -o /dev/null -s -w {time_connect}:%{time_starttransfer}:%{time_total}\\n https://rodrigoavila.dev
{% endhighlight %}

Resposta (em segundos):

{% highlight bash %}
# Conexão : início da transferência : total
0,035299:0,151648:0,157692
{% endhighlight %}
