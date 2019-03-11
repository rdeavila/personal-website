---
layout: post
title: 'PostgreSQL: Lista de todas as tabelas, ordenada por número de registros'
date: 2014-04-29 21:59:29.000000000 -03:00
---
{% highlight sql %}
-- Usa as estatísticas do PostgreSQL para a contagem.
-- Para números mais precisos, execute
--    VACUUM ANALYZE
-- antes de iniciar.
SELECT
   relname,
   n_live_tup
FROM
   pg_stat_user_tables
ORDER BY
   n_live_tup DESC;
{% endhighlight %}
