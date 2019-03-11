---
layout: post
title: 'Como testar as configurações do nginx'
date: 2015-05-12 09:46:42.000000000 -03:00
---
Ao alterar as configurações do nginx, você pode testar a sintaxe do `nginx.conf` antes
de reiniciar o servidor. No Ubuntu 14.04, você pode executar o seguinte comando antes
do restart:

{% highlight bash %}
sudo nginx -t -c /etc/nginx/nginx.conf
{% endhighlight %}

Caso o arquivo de configuração do seu servidor esteja em um local diferente, basta informar
o local correto no comando acima.

Se a sintaxe do arquivo estiver correta, você receberá uma mensagem parecida com esta:

{% highlight bash %}
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
{% endhighlight %}

Fonte: [Checking nginx config file syntax](https://wincent.com/wiki/Checking_nginx_config_file_syntax)
