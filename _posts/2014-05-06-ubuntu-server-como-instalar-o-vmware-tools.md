---
layout: post
title: 'Ubuntu Server: como instalar o Vmware Tools'
date: 2014-05-06 16:21:19.000000000 -03:00
---
Se você instalou o Ubuntu Server em uma máquian virtual criada com Vmware vSphere, você pode instalar estes pacotes, para usar o Vmware Tools no servidor. Estes pacotes vão fornecer ao servidor um melhor desempenho de rede, além de mostrar informações do servidor no vSphere Client (como, por exemplo, reiniciar o servidor via client).

Os pacotes são estes:

{% highlight bash %}
sudo apt-get install --no-install-recommends open-vm-dkms
sudo apt-get install open-vm-tools
{% endhighlight %}

Não sei se este passo é realmente necessário, mas...

{% highlight bash %}
sudo shutdown -r now
{% endhighlight %}

Caso troque o kernel, as ferramentas precisam ser removidas e reinstaladas:

{% highlight bash %}
# Remove os pacotes
sudo apt-get remove open-vm-tools
sudo apt-get remove open-vm-dkms
sudo shutdown -r now

# reinstala os pacotes.
sudo apt-get install --no-install-recommends open-vm-dkms
sudo apt-get install open-vm-tools
sudo shutdown -r now
{% endhighlight %}
