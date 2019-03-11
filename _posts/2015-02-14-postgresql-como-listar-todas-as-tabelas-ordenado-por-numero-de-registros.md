---
layout: post
title: 'PostgreSQL: Como listar todas as tabelas, ordenado por número de registros'
date: 2015-02-14 14:29:12.000000000 -02:00
---
Para que a query abaixo funcione, é preciso rodar um `VACUUM ANALYZE` antes. Isso
acontece porque a query utiliza as estatísticas do PostgreSQL para a contagem.

{% highlight sql %}
SELECT
   relname,
   n_live_tup
FROM
   pg_stat_user_tables
ORDER BY
   n_live_tup DESC;
{% endhighlight %}
