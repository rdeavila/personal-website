---
layout: post
title: 'Ubuntu: Como remover o Canonical Landscape'
date: 2015-02-13 12:31:53.000000000 -02:00
---
O [Landscape](https://landscape.canonical.com/), da Canonical, é um serviço que facilita o gerenciamento de múltiplos
servidores ao mesmo tempo, fornecendo uma interface web facilitada para monitoramento
e atualização. Mas, como a informação de remoção está [bem no final do FAQ](https://help.landscape.canonical.com/FAQ#How_do_I_remove_a_computer_from_Landscape.3F),
vou descrever como fazer a desinstalação:

1. Acesso o Landscape, e remova todos os servidores de sua conta.
2. Acesse cada um dos servidores, e remova os serviços do Landscape:

{% highlight bash %}
sudo apt-get remove --purge landscape-client landscape-client-ui landscape-client-ui-install landscape-common
{% endhighlight %}

Fonte: [How do I remove a computer from Landscape?](https://help.landscape.canonical.com/FAQ#How_do_I_remove_a_computer_from_Landscape.3F)
