---
layout: post
title: 'Ubuntu: como substituir o OpenJDK pelo Java Hotspot da Oracle no 11.10'
date: 2011-11-09 14:08:00.000000000 -02:00
---
Apesar de se comentar aos quatro cantos que o OpenJDK está no mesmo nível do Hotspot, já encontrei várias situações em que precisei mesmo do `sun-java6` original. Principalmente quando falo de EJBs e JBoss. Mas, como a maioria vence, vamos então à procura de alternativas.

Escrito por Eduardo Rodrigues da Luz, no [site BitMasters](http://www.bitmasters.com.br/2011/10/instalando-o-oraclesun-java-no-ubuntu-11-10-oneiric-ocelot/), vem a dica que me salvou quando reinstalei minha estação de trabalho e decidi usar o Oneiric 64bits. Abaixo, segue como fazer a instalação.

>A Canonical decidiu que não irá trazer para os repositórios o Oracle Java no Ubuntu Oneiric Ocelot, o OpenJDK atende muito bem o Java porém existem alguns desenvolvedores e até usuário que preferem instalar a versão da Oracle, nesse tutorial o objetivo é instalar a Maquina Virtual Java da Oracle sem mais complicações, então mãos-a-obra.
> Primeiro vamos adicionar o ppa:

{% highlight bash %}
sudo add-apt-repository ppa:ferramroberto/java
sudo apt-get update
{% endhighlight %}

> Para instalar o Oracle/Sun Java JRE:

{% highlight bash %}
sudo apt-get install sun-java6-jre sun-java6-plugin
{% endhighlight %}
 
> Para instalar o Oracle/Sun Java JDK:

{% highlight bash %}
sudo apt-get install sun-java6-jdk
{% endhighlight %}

> Agora vamos definir o o Oracle Java como Padrão:

{% highlight bash %}
sudo update-alternatives --config java
sudo update-alternatives --config javac
{% endhighlight %}
 
> Quando executar o update-alternatives escolha na lista a opção referente ao JRE/JDK da Oracle. Para testar o java foi configurado corretamente basta executar:

{% highlight bash %}
$ javac -version
javac 1.6.0_26
{% endhighlight %}
 
{% highlight bash %}
$ java -version
java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) 64-Bit Server VM (build 20.1-b02, mixed mode)
{% endhighlight %}

>Pronto, agora estamos com o Java da Oracle/Sun configurados.

Fontes:
[http://ubuntuguide.net/install-sun-java-6-jrejdk-from-ppa-in-ubuntu-11-04](http://ubuntuguide.net/install-sun-java-6-jrejdk-from-ppa-in-ubuntu-11-04)
[https://launchpad.net/~ferramroberto/+archive/java](https://launchpad.net/%7Eferramroberto/+archive/java)
http://www.bitmasters.com.br/2011/10/instalando-o-oraclesun-java-no-ubuntu-11-10-oneiric-ocelot/
