---
title: Como usar SSH sem senha, com ssh-keygen
date: 2007-06-21 14:05:00.000000000 -03:00
published: true
---

Se você costuma logar por ssh em várias máquinas e gostaria de não precisar entrar a senha cada vez, siga o seguinte procedimento:

{% highlight bash %}
ssh-keygen
{% endhighlight %}

Quando for perguntado a você o local onde salvar o arquivo, escolha o lugar padrão. Pressione enter quando solicitado (não entre com passphrases). Se quiser usar uma senha, melhor. Mas daí não fica mais um SSH sem senha :D

Este programa cria 2 arquivos:

{% highlight bash %}
.ssh/id_rsa
.ssh/id_rsa.pub.
{% endhighlight %}

Transfira o `id_rsa.pub` para a máquina que você deseja conectar remotamente, usando o comando abaixo. Substitua login por seu nome de usuário no computador remoto, e maquinaremota pelo endereço IP do servidor remoto. Se preciso, altere o número da porta do servidor SSH, no parâmetro `-p`

{% highlight bash %}
ssh-copy-id -i .ssh/id_rsa.pub -p 22 login@maquinaremota
{% endhighlight %}

Caso o computador que você esteja usando não possua o comando `ssh-copy-id`, pode-se fazer a cópia direta do arquivo:

{% highlight bash %}
scp ~/.ssh/id_rsa.pub login@maquinaremota:.ssh/authorized_keys2
{% endhighlight %}
