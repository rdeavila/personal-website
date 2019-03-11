---
layout: post
title: 'PostgreSQL: restaurando backup dentro de um .tar.bz2'
date: 2014-02-27 12:48:00.000000000 -03:00
---
Primeiro, verifica o nome e o caminho do arquivo `.out`, dentro do `.tar.bz2`

```bash
tar --list --file=backup.tar.bz2
```

Vamos supor que o arquivo `backup.tar.bz2` tem os seguintes arquivos:

```bash
script.sh
README.txt
backup/saida.out
backup/log_backup.txt
```

Cria a base de dados no PostgreSQL

```bash
createdb minha-base
```

Depois, utiliza o caminho correto do arquivo out (caminho dentro do `.tar.bz2`) no comando de descompactação para o stdout. Ao mesmo tempo, passa o stdout para o psql

```bash
tar Ojxvf backup.tar.bz2 backup/saida.out | psql minha-base
```
