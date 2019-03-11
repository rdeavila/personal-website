---
layout: post
title: 'Git: estatísitcas simples, bash-style'
date: 2014-05-06 11:15:20.000000000 -03:00
---
Interessado em algumas estatísticas para seu projeto? Quem fez quantos commits? Em que dia da semana foram feitos mais commits, e em que hora do dia?

Bom, aqui temos algumas destas estatísticas. Todas elas em uma linha de bash script.

O ranking de commits, por autor, por número de commits.

{% highlight bash %}
git shortlog  -ns
{% endhighlight %}

Os commits de um projeto, por dia da semana.

{% highlight bash %}
for i in Mon Tue Wed Thu Fri Sat Sun; do
    echo $( echo " $i: "; git shortlog  -n --format='%ad %s'| grep "$i " | wc -l);
done
{% endhighlight %}

Os commits de um projeto, por dia da semana, a partir de uma determinada data. Interessante para ver a diferença quando o grupo de desenvolvedores muda, por exemplo. Se quiser contar os commits de antes de uma data, troque `--since` por `--until`.

{% highlight bash %}
for i in Mon Tue Wed Thu Fri Sat Sun; do
    echo $( echo " $i: "; git shortlog  -n --format='%ad %s' --since='2011-06-31'| grep "$i " | wc -l);
done
{% endhighlight %}

Os commits de um projeto, por hora do dia.

{% highlight bash %}
for i in `seq -w 0 23`; do
    echo $( echo " $i:"; git shortlog  -n --format='%ad %s' | grep " $i:" | wc -l);
done
{% endhighlight %}

Os commits de um projeto, por hora do dia, a partir de uma determinada data.Aqi também dá pra trocar `--since` por `--until`.

{% highlight bash %}
for i in `seq -w 0 23`; do
    echo $( echo " $i:"; git shortlog  -n --format='%ad %s' --until='2011-06-31' | grep " $i:" | wc -l);
done
{% endhighlight %}

Fonte: [Jazzy Coding]

[Jazzy Coding]: https://phreaknerd.wordpress.com/2012/03/27/git-statistic-bash-one-liners/
