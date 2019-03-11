---
layout: post
title: 'Git: Como comparar dois repositórios diferentes'
date: 2015-03-13 11:42:28.000000000 -03:00
---
Se você tem dois repositórios, em dois locais diferentes, e precisa saber se
existem diferenças entre eles, você pode rodar um `git diff` entre ambos, pra
ver as diferenças (se existirem, claro).

Levando em conta que você tem um `repositorio_a`, e quer comparar ele com um
`repositorio_b`, faça o seguinte no `repositorio_a`:

{% highlight bash %}
# Vá até o repositorio_a
cd /home/usuario/repositorio_a

# Adicione o repositorio_b como um remote
git remote add -f b /home/usuario/repositorio_b

# Veja as diferenças
git diff master remotes/b/master

# Quando estiver satisfeito, remova o remote
git remote rm b
{% endhighlight %}

Fonte: [Git: Getting the difference between two repositories](http://stackoverflow.com/a/1968538/2788008)
