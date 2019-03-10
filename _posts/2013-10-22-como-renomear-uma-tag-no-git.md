---
layout: post
title: Como renomear uma tag no Git
date: 2013-10-22 12:06:00.000000000 -02:00
---
Uma dica para renomear uma tag no Git:

Primeiro cria um alias da tag antiga com um nome novo

{% highlight bash %}
git tag nome_antigo nome_novo
{% endhighlight %}

Remove a tag antiga localmente

{% highlight bash %}
git tag -d nome_antigo
{% endhighlight %}

Depois, remove a tag no repositório remoto, com Checkout da fonte remota

{% highlight bash %}
git remote -v
{% endhighlight %}

O terceiro argumento é o seu repositório remoto, aquele que você acessa com `git remote`. Neste exemplo: `origin`

{% highlight bash %}
git push origin :refs/tags/nome_antigo
{% endhighlight %}

Finalmente, adicona a nova tag ao repositório remoto. Enquanto você não fizer isso, a nova tag não vai ser adicionada:

{% highlight bash %}
git push origin --tags
{% endhighlight %}

Repita este passo em todos os seus repositórios remotos.

Fonte: Resposta do usuário [kaiser](http://stackoverflow.com/users/376483/kaiser) no [StackOverflow](http://stackoverflow.com/a/16251698/2788008).
