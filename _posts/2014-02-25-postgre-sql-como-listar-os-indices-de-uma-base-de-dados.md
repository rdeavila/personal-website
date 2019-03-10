---
layout: post
title: 'PostgreSQL: Como listar os índices de uma base de dados'
date: 2014-02-25 17:08:00.000000000 -03:00
---
Gera queries do tipo CREATE INDEX para todos os índices de um banco de dados.

{% highlight sql %}
select
   'CREATE INDEX '|| index_name || ' ON ' || table_name || ' ( ' || colunas || ' );'  
from
   (select
      table_name,
      index_name,
      array_to_string ( ARRAY (  select
         a.attname as column_name  
      from
         pg_class t,
         pg_class i,
         pg_index ix,
         pg_attribute a  
      where
         t.oid = ix.indrelid  
         and i.oid = ix.indexrelid  
         and a.attrelid = t.oid  
         and a.attnum = ANY(ix.indkey)  
         and t.relkind = 'r'  
         and i.relname not like 'fk_%'  
         and i.relname not like 'pk_%'  
         and i.relname not like '%_pkey'  
         and t.relname = base.table_name  
         and i.relname = base.index_name  
      order by
         t.relname,
         i.relname,
         a.attname ),
      ', ') AS colunas  
   from
      (select
         distinct t.relname as table_name,
         i.relname as index_name  
      from
         pg_class t,
         pg_class i,
         pg_index ix,
         pg_attribute a  
      where
         t.oid = ix.indrelid  
         and i.oid = ix.indexrelid  
         and a.attrelid = t.oid  
         and a.attnum = ANY(
            ix.indkey  
         )  
         and t.relkind = 'r'  
         and i.relname not like 'fk_%'  
         and i.relname not like 'pk_%'  
         and i.relname not like '%_pkey'  
      order by
         t.relname,
         i.relname ) as base) as base2;
{% endhighlight %}
