---
layout: post
title: 'Git: Como assinar um commit com GPG'
date: 2014-05-06 11:01:25.000000000 -03:00
---
Para listar as chaves atuais:

{% highlight bash %}
$ gpg --list-secret-keys | grep ^sec
sec   3185S/7DD21DBA 2014-05-06 [expires: 2015-05-05]
#           ^^^^^^^^
{% endhighlight %}

O valor hexadecimal depois da barra é o que precisamos.

Adicione este valor à config. padrão do Git:

{% highlight bash %}
$ git config --global user.signingkey 7DD21DBA
{% endhighlight %}

Substitua `7DD21DBA` pelo valor hexadecimal do comando anterior.

Para fazer com que esta chave seja usada em apenas um repositório, execute este comando sem o `--global`.

Na hora defazer o commit, adicione a opção `-S`:

{% highlight bash %}
$ git commit -S -m 'Teste de Commit assinado.'
{% endhighlight %}

Para confirmar:

{% highlight bash %}
$ git log --show-signature
{% endhighlight %}
