---
layout: post
title: 'SQL Server: Como saber o uptime do servidor'
date: 2015-02-11 01:12:53.000000000 -02:00
tags: sqlserver sql uptime server
---
Se você precisa saber a quanto tempo o SQL Server está rodando, a query abaixo
vai te dar esta informação.

{% highlight sql %}
SET
NOCOUNT
   ON  DECLARE @crdate DATETIME,
   @hr VARCHAR(50),
   @min VARCHAR(5)  SELECT
      @crdate=crdate
FROM
   sysdatabases
WHERE
   NAME='tempdb'  SELECT
      @hr=(DATEDIFF ( mi,
      @crdate,
      GETDATE()))/60  IF ((DATEDIFF ( mi,
      @crdate,
      GETDATE()))/60)=0  SELECT
         @min=(DATEDIFF ( mi,
         @crdate,
         GETDATE()))  
         ELSE  SELECT
            @min=(DATEDIFF ( mi,
            @crdate,
            GETDATE()))-((DATEDIFF( mi,
            @crdate,
            GETDATE()))/60)*60  PRINT 'O SQL Server "' + CONVERT(VARCHAR(20),
            SERVERPROPERTY('SERVERNAME'))+'" esta online a '+@hr+' horas e '+@min+' minutos.'
{% endhighlight %}
