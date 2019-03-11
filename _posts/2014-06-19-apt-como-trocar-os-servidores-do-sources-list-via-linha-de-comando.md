---
layout: post
title: 'APT: Como trocar os servidores do sources.list via Linha de Comando'
date: 2014-06-19 00:24:35.000000000 -03:00
---
Se o seu `sources.list` está configurado com os servidores americanos `us.archive.ubuntu.com`, você pode trocar todas as linhas, de uma vez só, para `br.archive.ubuntu.com`.

O comando para fazer isto é esse:

{% highlight bash %}
sudo sed -i 's/us.archive.ubuntu.com/br.archive.ubuntu.com/g' /etc/apt/sources.list
{% endhighlight %}

[Uma breve explicação](http://explainshell.com/explain?cmd=sudo+sed+-i+%27s%2Fus.archive.ubuntu.com%2Fbr.archive.ubuntu.com%2Fg%27+%2Fetc%2Fapt%2Fsources.list):

- `sudo` = Como vamos mudar o `sources.list`, precisamos ter poderes de root pra isso.
- `sed` = é o Stream EDitor
- `-i` = de `in-place` (ou seja: salva as alterações no arquivo original.)
- A String de alteração:
 - `s` = o comando para efetuar a substituição
 - `us.archive.ubuntu.com` = a expressão regular que descreve o servidor que está configurado no arquivo, e que precisa ser substituído (ou diretamente o nome do servidor)
 - `br.archive.ubuntu.com` = o servidor que deve substituir o anterior
 - `g` = de `global` (ou seja: substitui todas as ocorrências, e não apenas a primeira)
- `/etc/apt/sources.list` = O arquivo `sources.list` que terá seus servidores alterados.

Não esqueça de executar `sudo apt-get update` depois da alteração.

Fonte: http://askubuntu.com/a/20416
