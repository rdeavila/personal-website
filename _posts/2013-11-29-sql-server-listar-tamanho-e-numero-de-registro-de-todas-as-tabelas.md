---
layout: post
title: 'SQL Server: listar tamanho e número de registro de todas as tabelas'
date: 2013-11-29 12:16:00.000000000 -02:00
---
Lista as tabelas de um banco de dados SQL Server, junto com o nro. de registros, e tamanho de cada tabela.

{% highlight sql %}
SELECT
    t.NAME AS Entidade,
    p.rows AS Registros,
    SUM(a.total_pages) * 8 AS EspacoTotalKB,
    SUM(a.used_pages) * 8 AS EspacoUsadoKB,
    (SUM(a.total_pages) - SUM(a.used_pages)) * 8 AS EspacoNaoUsadoKB
FROM
    sys.tables t
INNER JOIN
    sys.indexes i ON t.OBJECT_ID = i.object_id
INNER JOIN
    sys.partitions p ON i.object_id = p.OBJECT_ID AND i.index_id = p.index_id
INNER JOIN
    sys.allocation_units a ON p.partition_id = a.container_id
LEFT OUTER JOIN
    sys.schemas s ON t.schema_id = s.schema_id
WHERE
    t.NAME NOT LIKE 'dt%'
    AND t.is_ms_shipped = 0
    AND i.OBJECT_ID > 255
GROUP BY
    t.Name, s.Name, p.Rows
ORDER BY
    Registros DESC
{% endhighlight %}

Fonte: post do usuário [marc_s](http://stackoverflow.com/users/13302/marc-s) no [StackOverflow](http://stackoverflow.com/questions/7892334/get-size-of-all-tables-in-database)
