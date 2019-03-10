---
layout: post
title: Como instalar o Oracle Java 7 no Ubuntu, via PPA
date: 2013-10-23 13:23:00.000000000 -02:00
---
As instruções são simples. Basta adicionar o PPA, e instalar. O pacote `oracle-java7-set-default` define as variáveis de ambiente, e coloca o java 7 como padrão.

Este pacote fornece o Oracle Java JDK 7 (que inclui Java JDK, JRE e o plugin Java para navegadores).

Não é possível instalar apenas o Oracle JRE - o PPA fornece apenas o pacote completo.

Use os comandos abaixo para adicionar o PPA e instalar a última versão do Oracle Java 7 no Ubuntu. Suporta Ubuntu 10.04 a 14.04.

{% highlight bash %}
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer oracle-java7-set-default
{% endhighlight %}

Fonte: [INSTALL ORACLE JAVA 7 IN UBUNTU VIA PPA REPOSITORY](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)
