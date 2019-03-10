---
layout: post
title: 'Mac OS X: Como redimensionar um sparseimage'
date: 2010-08-18 17:21:00.000000000 -03:00
---
De acordo com a Wikipédia, "Um Sparse image é um tipo arquivo de imagem de disco que pode ser criadono Mac OS X usando o Utilitário de Disco. Sparse images encriptados são usados pelo File Vault para manter seguro o diretório home do usuário."

Na hora de criar a imagem, o tamanho máximo é solicitado. Se você subestimou o tamanho da imagem, e agora precisa de mais espaço, a dica é redimensionar. Como?

1) **Desmonte a imagem**, caso você a esteja usando.
2) Abra um terminal, vá até o diretório onde está a imagem, e digite:

{% highlight bash %}
hdiutil resize -size 50g nomedoarquivo.sparseimage
{% endhighlight %}

Isso, claro, se você quiser que a imagem fique com 50Gb. Para outros tamanhos, é só mudar o parâmetro.

Uma dica parecida serve quando você deletou arquivos de dentro de um sparseimage, e agora quer compactá-lo. O comando é:

{% highlight bash %}
hdiutil compact nomedoarquivo.sparseimage
{% endhighlight %}

Mais informações sobre como funciona o comando hdiutil, você encontra no manpage.

Fonte: [Artigo na Wikipedia](http://en.wikipedia.org/wiki/Sparse_image)
