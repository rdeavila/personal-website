---
layout: post
title: 'SSH: Como executar "tail -f" em uma máquina remota'
date: 2014-02-10 16:38:00.000000000 -02:00
---

Substitua `user` pelo nome de usuário, `host` pelo nome ou endereço IP do servidor remoto, e `/var/log/messages` pelo arquivo que você quer exibir.

```bash
ssh user@host "tail -f /var/log/messages"
```

Fonte: [ianneubert.com](http://www.ianneubert.com/wp/2010/07/14/use-ssh-to-get-tail-of-log-file/)
