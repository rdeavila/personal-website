---
layout: post
title: 'SQL Server: Como listar e encerrar as queries que estão sendo executadas'
date: 2013-11-25 12:32:00.000000000 -02:00
---
A query a seguir lista todas as queries que estão em execução no seu servidor SQL Server.

{% highlight sql %}
SELECT      sqltext.TEXT,
            req.session_id,
            req.status,
            req.command,
            req.cpu_time,
            req.total_elapsed_time
FROM        sys.dm_exec_requests req
CROSS APPLY sys.dm_exec_sql_text(sql_handle) 
AS          sqltext
{% endhighlight %}

Uma das colunas acima é a `session_id`. Se você acha que uma delas está rodando a mais tempo que o necessário, basta usar a query abaixo para encerrar a conexão responsável por esta query, e terminar sua execução:

{% highlight sql %}
KILL [session_id]
{% endhighlight %}

Fonte: Pinal Dave ([http://blog.SQLAuthority.com](http://blog.sqlauthority.com/2009/01/07/sql-server-find-currently-running-query-t-sql/))
