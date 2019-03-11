---
layout: post
title: 'Ubuntu Server: como identificar uma nova placa de rede'
date: 2014-05-07 22:19:36.000000000 -03:00
---
Se você usa o Ubuntu Server em uma máquina virtual, como Parallels ou Virtualbox, já precisou alguma vez trocar a placa de rede da VM, por algum motivo?

E quando faz isso, o Ubuntu reconheceu e configurou a placa sozinho?

No meu caso, não. O que fiz pra resolver o problema é isso:

* Verifiquei se o driver estava carregado. No meu caso, era pra instalar uma Realtek RTL8029AS, do Parallels.

{% highlight bash %}
lsmod |grep ne
modprobe -v ne
modprobe -v ne2k-pci
{% endhighlight %}

* Como o driver estava listado, verifiquei se a placa de rede tinha sido reconhecida:

{% highlight bash %}
lspci -v | grep -A12 "Ethernet"
{% endhighlight %}

* Mas, mesmo aparecendo, o DHCP da rede não entregou um endereço IP para esta placa. Para corrigir isso, apaguei o conteúdo do arquivo `70-persistent-net.rules`, e reiniciei o servidor.

{% highlight bash %}
echo "" > /etc/udev/rules.d/70-persistent-net.rules
shutdown -r now
{% endhighlight %}

Após isto, a placa de rede recebeu um novo endereço, normalmente.
