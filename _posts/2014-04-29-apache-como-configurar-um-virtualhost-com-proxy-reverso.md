---
layout: post
title: 'Apache: Como configurar um VirtualHost com proxy reverso'
date: 2014-04-29 14:35:02.000000000 -03:00
---
#### Instala biblioteca do Apache

{% highlight bash %}
sudo apt-get install libapache2-mod-proxy-html
{% endhighlight %}

#### Habilita os módulos no Apache

{% highlight bash %}
sudo a2enmod proxy proxy_http proxy_connect proxy_html xml2enc
{% endhighlight %}

#### Reinicia o Apache

{% highlight bash %}
sudo service apache2 restart
{% endhighlight %}

#### Cria o arquivo com novo site

{% highlight bash %}
sudo nano /etc/apache2/sites-available/site-proxy.conf
{% endhighlight %}

{% highlight apacheconf %}
<VirtualHost *:80>

    # Altere o email do administrador.
    ServerAdmin hostmaster@example.com
    ProxyRequests off
    DocumentRoot /var/www
    ProxyPreserveHost On

    # Altere a URL que vai ser usada
    # para acessar o site
    ServerName example.com

    # Caso mais de uma URL for usada,
    # adicione as outras aqui, uma em
    # cada linha.
    ServerAlias www.example.com

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

    # Alguns possíveis valores: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel error

    <Location />
        # Configure aqui a URL do site que se quer acessar.
        ProxyPass http://internal.example.com:8444/
        ProxyPassReverse http://internal.example.com:8444/
        Order allow,deny
        Allow from all
    </Location>
</VirtualHost>
{% endhighlight %}

#### Adiciona o site ao Apache

{% highlight bash %}
sudo a2ensite site-proxy
{% endhighlight %}

#### Reinicia (de novo) o Apache

{% highlight bash %}
sudo service apache2 restart
{% endhighlight %}
