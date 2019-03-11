---
layout: post
title: 'Ubuntu: Como limitar o acesso com SFTP Jail'
date: 2015-02-05 13:06:42.000000000 -02:00
---
Se você já configurou um servidor FTP para permitir acesso dos usuários apenas ao seu diretório `home`, saiba que dá pra fazer o mesmo com SFTP. E ainda impedir que o usuário acesse o servidor por SSH.

## Configure o OpenSSH

Edite o arquivo `/etc/ssh/sshd_config`, e altere ou adicione a seguinte configuração:

{% highlight bash %}
Subsystem sftp internal-sftp
{% endhighlight %}

Depois, no mesmo arquivo, adicione o seguinte no fim do arquivo:

{% highlight bash linenos %}
Match group filetransfer
    ChrootDirectory %h
    X11Forwarding no
    AllowTcpForwarding no
    ForceCommand internal-sftp
{% endhighlight %}

Reinicie o OpenSSH.

{% highlight bash %}
service ssh restart
{% endhighlight %}

## Modifique as contas dos usuários

Primeiro, crie um grupo no sistema, que será usado por todos os usuários que podem acessar o servidor __apenas__ por SFTP.

{% highlight bash %}
addgroup --system filetransfer
{% endhighlight %}

Modifique as contas dos usuários, para restringir o acesso deles apenas ao SFTP. Estes comandos precisam ser feitos para cada conta de usuário que for criada.

{% highlight bash %}
usermod -G filetransfer usuario
chown root:root /home/usuario
chmod 755 /home/usuario
{% endhighlight %}

As contas de usuários que podem acessar o servidor via SSH não devem ser alteradas, nem ser adicionados ao grupo `filetransfer`.

Feito isto, será necessário criar um diretório, dentro do `home` de cada usuário. Este diretório será o local onde o usuário poderá colocar seus arquivos normalmente.

{% highlight bash %}
cd /home/usuario
mkdir public_html
chown usuario:filetransfer *
{% endhighlight %}

Com estas configurações, os usuários conseguirão acessar o servidor por SFTP e adicionar/remover arquivos no diretório `public_html`, mas eles não conseguirão adicionar arquivos em outros lugares, nem acessar o servidor por SSH.

Fonte: [Limiting Access with SFTP Jails on Debian and Ubuntu](https://www.linode.com/docs/tools-reference/tools/limiting-access-with-sftp-jails-on-debian-and-ubuntu)
