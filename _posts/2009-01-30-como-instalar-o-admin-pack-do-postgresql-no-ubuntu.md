---
layout: post
title: Como instalar o AdminPack do Postgresql no Ubuntu
date: 2009-01-30 12:14:00.000000000 -02:00
published: true
---
Você usa o PgAdmin III par administrar o seu servidor PostgreSQL? Se usa, já viu alguma vez um erro reclamando da falta da instrumentação do servidor (missing server instrumentation)?Se você usa o PostgreSQL 8.3 com Ubuntu 8.10, você pode fazer o seguinte:

1) Instale o pacote `postgresql-contrib`
2) Rode o seguinte comando em um terminal:

{% highlight bash %}
psql -U postgres -d postgres -h localhost < /usr/share/postgresql/8.3/contrib/adminpack.sql
{% endhighlight %}

Esse script cria um punhado de funções na base de dados de administração. Ao fazer isso, a mensagem não deve aparece mais.
