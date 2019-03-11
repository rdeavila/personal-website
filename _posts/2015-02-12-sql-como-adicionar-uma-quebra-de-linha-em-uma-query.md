---
layout: post
title: 'SQL: Como adicionar uma quebra de linha em uma query'
date: 2015-02-12 12:31:53.000000000 -02:00
---
Veja abaixo dois exemplos. Um para PostgreSQL e outro para SQL Server.

{% highlight sql %}
-- Exemplo para PostgreSQL
SELECT 'Primeira Linha' || Chr(13) ||'Segunda Linha';

-- Exemplo para SQL Server
SELECT 'Primeira Linha' + CHAR(13)+CHAR(10) + 'Segunda Linha';
{% endhighlight %}

`CHAR(13)` é o equivalente ao `CR`. Para seguir o estilo `CRLF` do DOS/Windows,
é necessário o `CHAR(13)+CHAR(10)`.

**Update 26/06/2015:** Alguns leitores informaram que a solução apresentada para
SQL Server não funciona. Na verdade ela funciona sim. Faltou eu explicar melhor
o problema que existe quando visualizamos o resultado da query.

Quando executamos a query, ela adiciona as quebras de linha, seja do windows,
seja do Unix. Mas, visualizar estas quebras depende da ferramenta que usamos para
executá-la. Veja os exemplos abaixo:

#### SQL Server

Ao executar as queries no Management Studio, temos duas forma de visualizar os
resultados: em modo grid, e em modo texto.

Quando visualizamos em modo grid, o Management Studio não mostra as quebras de
linha:

![](/content/images/2015/02/sqlserver-result-to-grid.png)

Mas, quando visualizamos em modo texto, ele faz a quebra, como deve ser:

![](/content/images/2015/02/sqlserver-result-to-text.png)


#### PostgreSQL

Ao visualizar usando o `psql`, ele mostra o `\r`, que é a representação do
caractere de quebra de linha:

![](/content/images/2015/02/pgsql-terminal.png)

Já quando visualizamos pelo PgAdmin, ele faz a quebra, como deve ser:

![](/content/images/2015/02/pgsql-pgadmin.png)


#### Mas, e o meu aplicativo?

Se você utiliza esta dica em um aplicativo desenvolvido por você, você precisará
tratar o resultado da query, e mostrar os caracteres de quebra de linha da forma
como quiser. Por exemplo, se estiver desenvolvendo um app web, você pode, na
camada de visualização, substituir as quebras de linha por `<br/>`.

Obrigado aos leitores [Leonardo Cintra](https://disqus.com/by/leonardonascimentocintra/)
e [robson_cks](https://disqus.com/by/robson_cks/) pelo alerta!
