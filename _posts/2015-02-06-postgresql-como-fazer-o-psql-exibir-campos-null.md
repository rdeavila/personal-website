---
layout: post
title: 'PostgreSQL: Como fazer o psql exibir campos null'
date: 2015-02-06 15:31:53.000000000 -02:00
---
Normalmente, o comando `psql` apenas deixa em branco os campos nulos de um registro, quando se faz uma query. Para forçar o `psql` a mostrar os nulos, use o comando `\pset`:

{% highlight bash %}
rodrigo@servidor:~$ psql base_teste
psql (9.1.11)
Type "help" for help.

base_teste=# SELECT NULL;
 ?column?
----------

(1 row)

base_teste=# \pset null '(null)'
Null display is "(null)".
base_teste=# SELECT NULL;
 ?column?
----------
 (null)
(1 row)

base_teste=# \q
rodrigo@servidor:~$
{% endhighlight %}

Neste exemplo, vemos como o PostgreSQL mostra um nulo antes e depois de definir a opção com o `\pset`. Note que o texto escolhido, para representar um valor nulo, foi `(null)`. Mas poderia ser qualquer outro texto.

Esta opção de saída fica disponível apenas na execução atual do `psql`.

Fonte: [Output Format Options](http://momjian.us/main/writings/pgsql/aw_pgsql_book/node142.html#Example_of_pset)
