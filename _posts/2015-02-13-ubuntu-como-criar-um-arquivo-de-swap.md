---
layout: post
title: 'Ubuntu: Como criar um arquivo de swap'
date: 2015-02-13 12:31:53.000000000 -02:00
---
Se você tem um servidor com pouca memória, como um [VPS de 512Mb da DigitalOcean](https://www.digitalocean.com/?refcode=978a22be9bab)
(que, por padrão, é criado sem arquivo de troca), você pode criar um arquivo
de swap. Assim, você não precisa reparticionar seu disco.

Os comandos são estes:

{% highlight bash %}
# Este comando cria um arquivo de swap de 4Gb.
sudo fallocate -l 4G /swapfile

# Define as permissões
sudo chmod 600 /swapfile

# Formata o arquivo
sudo mkswap /swapfile

# Habilita o swap para este arquivo
sudo swapon /swapfile

# Define configurações do Ubuntu, para melhor utilização
# do swap
sudo sysctl vm.swappiness=10
sudo sysctl vm.vfs_cache_pressure=50
{% endhighlight %}

Feito isto, o seu arquivo de swap está habilitado e funcionando.

Agora, para fazer com que estas alterações se tornem permanentes, você precisa
alterar os seguintes arquivos:

* Adicionar ao `/etc/fstab`

{% highlight text %}
    /swapfile   none    swap    sw    0   0
{% endhighlight %}

* Adicionar ao `/etc/sysctl.conf`

{% highlight text %}
    vm.swappiness = 10
    vm.vfs_cache_pressure = 50
{% endhighlight %}
