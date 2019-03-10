---
layout: post
title: Como gerar código hexadecimal para cores HTML
date: 2009-04-02 11:55:00.000000000 -03:00
published: true
---
Esses dias eu precisei de um gerador randômico de cores HTML. Como as cores em HTML são geradas a partir de um código hexadecimal, foi fácil fazer um gerador.

{% highlight java %}
Random rand = new Random();

// Caracteres possíveis dentro de uma
// cor HTML representada em hexadecimal.
String chars = "0123456789ABCDEF";

StringBuilder cor = new StringBuilder("#");
cor.append(chars.charAt(rand.nextInt(16)))
   .append(chars.charAt(rand.nextInt(16)))
   .append(chars.charAt(rand.nextInt(16)))
   .append(chars.charAt(rand.nextInt(16)))
   .append(chars.charAt(rand.nextInt(16)))
   .append(chars.charAt(rand.nextInt(16)));

return cor.toString();
{% endhighlight %}
