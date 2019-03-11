---
layout: post
title: 'Ubuntu: como enviar arquivos para o Google Drive usando o terminal'
date: 2014-04-29 15:34:42.000000000 -03:00
---
O GDrive é um utilitário para fazer o upload e o download de arquivos para o seu Google Drive. Esta ferramenta não faz nenhum tipo de sincronização. Apenas permite que você faça um único upload/download, via linha de comandou, ou usando um script automatizado.

Para download, [acesse esta página]. Ali estão os arquivos para Linux, OSX, freebsd, e Windows.

Para instalar: copie o executável que você baixou em algum lugar acessível. No linux, por exemplo, em `/usr/bin`

Antes de usar pela primeira vez, será necessário executá-lo sem opções, para que se faça a autorização junto à sua conta. Siga as instruções no terminal para fazer isso.

#### Listar arquivos

{% highlight bash %}
$ drive list
Id                             Title                     Size     Created
0B3X9GlR6EmbnenBYSFI4MzN0d2M   drive-freebsd-amd64       5 MB     2013-01-01 21:57:01
0B3X9GlR6EmbnOVRQN0t6RkxVQk0   drive-windows-amd64.exe   5 MB     2013-01-01 21:56:41
0B3X9GlR6Embnc1BtVVU1ZHp2UjQ   drive-linux-arm           4 MB     2013-01-01 21:57:23
0B3X9GlR6EmbnU0ZnbGV4dlk1T00   drive-linux-amd64         5 MB     2013-01-01 21:55:06
0B3X9GlR6EmbncTk1TXlMdjd1ODQ   drive-darwin-amd64        5 MB     2013-01-01 21:53:34
{% endhighlight %}

### Upload de um arquivo

{% highlight bash %}
$ drive upload --file drive-linux-amd64
Id: 0B3X9GlR6EmbnU0ZnbGV4dlk1T00
Title: drive-linux-amd64
Size: 5 MB
Created: 2013-01-01 21:55:06
Modified: 2013-01-01 21:55:06
Owner: Petter Rasmussen
Md5sum: 334ad48f6e64646071f302275ce19a94
Shared: False
Uploaded 'drive-linux-amd64' at 510 KB/s, total 5 MB
{% endhighlight %}

### Download de um arquivo

{% highlight bash %}
$ drive download --id 0B3X9GlR6EmbnenBYSFI4MzN0d2M
Downloaded 'drive-freebsd-amd64' at 2 MB/s, total 5 MB
{% endhighlight %}

### Compartilhar um arquivo

{% highlight bash %}
$ drive share --id 0B3X9GlR6EmbnOVRQN0t6RkxVQk0
File 'drive-windows-amd64.exe' is now readable by everyone @ https://drive.google.com/uc?id=0B3X9GlR6EmbnOVRQN0t6RkxVQk0
{% endhighlight %}

#### Direcionar o conteúdo de um arquivo diretamente para o drive

{% highlight bash %}
$ echo "Hello World" | drive upload --stdin --title hello.txt
Id: 0B3X9GlR6EmbnVHlHZWZCZVJ4eGs
Title: hello.txt
Size: 12 B
Created: 2013-01-01 22:05:44
Modified: 2013-01-01 22:05:43
Owner: Petter Rasmussen
Md5sum: e59ff97941044f85df5297e1c302d260
Shared: False
Uploaded 'hello.txt' at 6 B/s, total 12 B
{% endhighlight %}

#### Exibir o conteúdo de um arquivo no stdout

{% highlight bash %}
$ drive download --stdout --id 0B3X9GlR6EmbnVHlHZWZCZVJ4eGs
Hello World
{% endhighlight %}

#### Obter informações de um arquivo

{% highlight bash %}
$ drive info --id 0B3X9GlR6EmbnVHlHZWZCZVJ4eGs
Title: hello.txt
Size: 12 B
Created: 2013-01-01 22:05:44
Modified: 2013-01-01 22:05:43
Owner: Petter Rasmussen
Md5sum: e59ff97941044f85df5297e1c302d260
Shared: False
{% endhighlight %}

#### Obter a URL de download de um arquivo

{% highlight bash %}
$ drive url --id 0B3X9GlR6EmbnVHlHZWZCZVJ4eGs
https://drive.google.com/uc?id=0B3X9GlR6EmbnVHlHZWZCZVJ4eGs
{% endhighlight %}

[acesse esta página]: https://github.com/prasmussen/gdrive/blob/master/README.md#downloads
