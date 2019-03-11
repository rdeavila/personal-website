---
layout: post
title: 'OS X: Como adicionar um diretório ao $PATH'
date: 2014-06-12 09:23:24.000000000 -03:00
---
Ao instalar o [Postgres.app](http://postgresapp.com/) no Mac OSX 10.9 Mavericks, foi necessário adicionar o diretório com os binários do PostgreSQL ao `$PATH`, visto que todos os binários, bem como o diretório `data`, ficam dentro do app, em `/Applications`. Tentei adicionar o diretório ao `.bash_profile`, mas não sei porque motivo não funcionou. Por isso, foi pesquisar outros meios.

Descobri que o Mac OS X tem um diretório específico pra isso: `/etc/paths.d`. Dentro dele, o utilitário `path_helper` coloca as referências a todos os diretórios usados no `$PATH`.

Para adicionar o diretório `bin` do Postgres.app ao `/etc/paths.d`, faça o seguinte em um terminal:

{% highlight bash %}
sudo -s 'echo "/Applications/Postgres.app/Contents/Versions/9.3/bin" > /etc/paths.d/postgresql'
{% endhighlight %}

**Detalhe importante 1:** troque o diretório do Postgres.app pelo diretório de seu ambiente. Mesmo que você também instale o aplicativo no `/Applications`, acredito que a versão do PostgreSQL será diferente. Por isso, atenção com este detalhe.

**Detalhe importante 2:** os arquivos que ficam no diretório `/etc/pths.d` não podem ter linhas em branco no final. Se tiver, pode dar problema ao abrir um terminal.

Após isto, reinicie o terminal, e tente acessar o `psql`, o `pg_dump`, ou o `vacuumdb` a partir de qualquer outro local.

Fonte: [Mac OS X: Set / Change $PATH Variable](http://www.cyberciti.biz/faq/appleosx-bash-unix-change-set-path-environment-variable/)
