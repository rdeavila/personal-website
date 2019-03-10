---
layout: post
title: Como usar HTTPS (SSL) no JBoss 4.2.3.GA
date: 2009-11-09 15:34:00.000000000 -02:00
published: true
---
Se você (ainda) usa o JBoss 4.2.3.GA como servidor de aplicações, e deseja criptografar os dados trocados entre o servidor e o cliente via https, você pode usar a solução a seguir para criar um certificado SSL, e ativar o serviço no JBoss.

**Uma palavra de cautela**: Um certificado SSL tem dois objetivos: _criptografar dados_, e _garantir procedência_. Apenas o primeiro item é coberto por este tutorial, pois aqui você vai ver como criar um certificado auto-assinado. Se você sabe o que isto significa, e conhece bem os riscos que isto pode ocasionar, vá em frente. A configuração a seguir é um ótimo campo-de-testes. Mas se não sabe, procure estudar mais um pouco, e entender bem os riscos. Depois, volte aqui e aproveite.

**Uma alternativa**: Se quiser, pode deixar o JBoss como está, e colocar um Apache na frente, [como um proxy reverso](/2014/04/29/apache-como-configurar-um-virtualhost-com-proxy-reverso/).

## Passo 1: decida por qual URL você vai acessar o seu servidor

Este passo é importante, pois este endereço vai ser gravado no certificado, e se você acessar o servidor por outro endereço, o navegador irá reclamar. Caso esteja fazendo apenas um teste em seu próprio computador, localhost é o suficiente.

## Passo 2: crie um certificado auto-assinado

Como vimos acima, é um risco de segurança usar certificados auto-assinados. Mas para ambientes de teste e desenvolvimento, eles são mais do que suficientes. O local do arquivo vai depender de qual profile do JBoss você usa. No caso, vamos exemplificar com o 'default' mesmo.

- Vá até o diretório de configuração do profile

{% highlight bash %}
cd /opt/jboss-4.2.3.GA/server/default/conf
{% endhighlight %}

- Crie o arquivo keystore.jks usando a ferramenta keytool:

{% highlight bash %}
keytool -genkey -alias jboss -validity 1825 -keyalg RSA -keystore keystore.jks
{% endhighlight %}

Uma breve explicação do que estamos fazendo:

* `-alias jboss`: apelido que damos a este certificado, dentro do keystore.

* `-validity 1825`: número de dias em que este certificado será válido. Neste caso, 5 anos.

Ao digitar este comando, o keytool vai começar a perguntar um punhado de informações, que serão usadas para compor o certificado. Vamos mostrar aqui como ficariam estas informações, para o setor de TI da `Empresa de Exemplo`:

{% highlight bash %}
Enter keystore password: 
Re-enter new password: 
What is your first and last name?
  [Unknown]:  www.example.com
What is the name of your organizational unit?
  [Unknown]:  Setor de TI
What is the name of your organization?
  [Unknown]:  Empresa de Exemplo
What is the name of your City or Locality?
  [Unknown]:  Brochier
What is the name of your State or Province?
  [Unknown]:  Rio Grande do Sul
What is the two-letter country code for this unit?
  [Unknown]:  BR
Is CN=www.example.com, OU=Setor de TI, O=Empresa de Exemplo, L=Brochier, ST=Rio Grande do Sul, C=BR correct?
  [no]: 

Enter key password for <jboss>
 (RETURN if same as keystore password):  
Re-enter new password:
{% endhighlight %}

Alguns itens aqui são de extrema importância:

* `keystore password`: deve ser uma senha de pelo menos seis caracteres. Use a mesma senha, tanto no início quanto no final da lista acima.
* `first and last name`: Apesar de parecer que ele quer o seu nome e sobrenome, digite ali a URL do servidor, escolhida no passo 1.

Ao terminar, o arquivo `keystore.jks` deve estar criado.

## Passo 3: Edite o arquivo de configuração

Quem serve os JSPs e servlets no JBoss é o Tomcat. Vá até o diretório de configuração dele, e edite o arquivo server.xml:

{% highlight bash %}
nano /opt/jboss-4.2.3.GA/server/default/deploy/jboss-web.deployer/server.xml
{% endhighlight %}

Neste arquivo, você verá uma seção chamada `Connectors`. Entre os diversos Connectors, vai haver um, comentado, que aponta para a porta `8443`. Deixe-o comentado. Abaixo dele, use a seguinte configuração:

{% highlight xml %}
<connector protocol="HTTP/1.1" 
           sslenabled="true"
           port="8443" 
           address="${jboss.bind.address}"
           scheme="https" 
           secure="true" 
           clientAuth="false"
           keystoreFile="/opt/jboss-4.2.3.GA/server/default/conf/keystore.jks"
           keystorePass="umasenha" 
           sslProtocol="TLS"
           keyAlias="jboss">
</connector>
{% endhighlight %}

Alguns itens importantes:

* `port="8443"`: a porta a ser usada. Normalmente a porta para https é a `443`. Mas esta porta só pode ser usada por processos iniciados com o usuário root em sistemas unix/linux.
* `keystorePass="umasenha"`: digite aqui a senha escolhida por você durante a geração do arquivo `keystore.jks`.

Salve e feche o arquivo. A princípio, isto basta. Vá adiante.

## Passo 4: Reinicie e teste

Após baixar e levantar o JBoss, acesse o servidor pela URL escolhida, na porta `8443`. No exemplo acima:

{% highlight text %}
https://www.example.com:8443
{% endhighlight %}

E é só.
