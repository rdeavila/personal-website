---
layout: post
title: 'Ubuntu: Como redefinir o cache do APT-Cacher'
date: 2015-02-04 12:31:53.000000000 -02:00
---
Se [você usa o APT-Cacher](/2007/11/07/muitos_ubuntus_e_pouca_banda_use_o_apt_cacher_/),
mas está com problemas de espaço em disco, saibe que você pode redefinir por
completo os arquivos do cache, e começar do zero.

Para fazer isso, execute os comandos abaixo:

{% highlight bash %}
# Pare o serviço
sudo /etc/init.d/apt-cacher-ng stop

# Mova o cache antigo para um novo lugar. Desta forma, podemos removê-lo
# em background (dependendo do tamanho, a deleção pode demorar)
sudo mv /var/cache/apt-cacher-ng /var/cache/apt-cacher-ng.old
sudo rm -rf /var/cache/apt-cacher-ng.old &

# Crie a nova hierarquia de cache, e defina o dono correto.
sudo mkdir -p /var/cache/apt-cacher-ng/{headers,import,packages,private,temp}
sudo chown -R apt-cacher-ng:apt-cacher-ng /var/cache/apt-cacher-ng

# Inicie o serviço
sudo /etc/init.d/apt-cacher-ng start
{% endhighlight %}
