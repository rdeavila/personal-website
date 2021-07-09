---
layout: post
title: "Como encontrar o docker-compose-yml de um container"
date: 2021-07-09 12:50:42.000000000 -03:00
published: true
---

Se você precisa saber qual arquivo `docker-compose.yml` foi usado para
iniciar um container, use o `docker inspect`. Ele provê o local do arquivo
dentro de uma etiqueta.

{% highlight bash %}
[rodrigo@localhost ~]$ docker inspect 7e7c50e4caff | grep com.docker.compose
                "com.docker.compose.config-hash": "b71ebe6f0cc3a4fad024ddf27906c1e83467d25542d939c2fd123736325a23f1",
                "com.docker.compose.container-number": "1",
                "com.docker.compose.oneoff": "False",
                "com.docker.compose.project": "testfile",
                "com.docker.compose.project.config_files": "/opt/testfile/docker-compose.yml",
                "com.docker.compose.project.working_dir": "/opt/testfile",
                "com.docker.compose.service": "haproxy",
                "com.docker.compose.version": "1.25.5"
{% endhighlight %}
