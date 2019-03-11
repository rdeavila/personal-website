---
layout: post
title: 'GPG: Como importar chaves privadas via linha de comando'
date: 2014-05-06 11:03:09.000000000 -03:00
---
Este procedimento eu utilizei para importar minha própria chave privada, que eu tenho em backup, para um computador novo.

{% highlight bash %}
gpg --import arquivo.asc
gpg --allow-secret-key-import --import arquivo.asc
{% endhighlight %}

Para conferir se as chaves foram importadas:

{% highlight bash %}
gpg --list-keys | grep ^pub
pub   3185S/7DD21DBA 2014-05-06 [expires: 2015-05-05]  
#           ^^^^^^^^
{% endhighlight %}

Após fazer a importação, você precisa dizer ao gpg que confia nestas chaves. Para isto, você vai precisar do código heaxadecimal, apontado no item acima (no nosso caso, `7DD21DBA`). Com este código em mãos, execute:

{% highlight bash %}
gpg --edit-key 7DD21DBA
{% endhighlight %}

No prompt que se segue, digite `trust`, o nro. correspondente ao nível de confiança (no meu caso, `5`), e confirme digitando `sim`.

{% highlight bash %}
gpg> trust

Por favor decida quanto você confia neste usuário para
verificar corretamente as chaves de outros usuários
(olhando em passaportes, checando impressões digitais
de outras fontes...)

  1 = Eu não sei ou nem direi
  2 = Eu NÃO confio
  3 = Eu tenho pouca confiança
  4 = Eu confio totalmente
  5 = Eu confio ao extremo
  m = voltar ao menu principal

Sua decisão? 5
Você quer realmente definir esta chave à confiança final? sim
{% endhighlight %}

A partir deste momento, você disse que confia na chave importada.
