---
layout: post
title: Como executar o JBoss em portas diferentes
date: 2013-10-25 12:56:00.000000000 -02:00
---
Edit: para fazer o mesmo no JBoss 6, o arquivo a usar é este:

{% highlight bash %}
$JBOSS_HOME/server/default/conf/bindingservice.beans/META-INF/bindings-jboss-beans.xml
{% endhighlight %}

Dentro deste arquivo, altere a única referência a `8080` pela porta que você
quer usar.

---

Dentro do diretório `examples` do jboss tem um arquivo chamado `sample-bindings.xml`. Exemplo: `jboss-4.2.3.GA/docs/examples/binding-manager/sample-bindings.xml`. Você terá que carregar este arquivo na inicialização do JBoss, pois é ele que define quais são as portas utilizadas pelo container. Para isso, você habilita o MBean que está dentro do arquivo `jboss-service.xml` de cada um das instancias (minimal, default, all), é só descomentar o trecho abaixo:

{% highlight xml %}
<mbean
 code="org.jboss.services.binding.ServiceBindingManager"
 name="jboss.system:service=ServiceBindingManager">
  <attribute name="ServerName">
    ports-default
  </attribute>
  <attribute name="StoreURL">
    ../sample-bindings.xml
  </attribute>
  <attribute name="StoreFactoryClassName">
    org.jboss.services.binding.XMLServicesStoreFactory
  </attribute>
</mbean>
{% endhighlight %}

No arquivo `sample-bindings.xml`, já existem 3 conjuntos diferentes de portas (`<attribute name="ServerName">ports-xxx</attribute>`) pré-configurados (`ports-default`, `ports-01`, `ports-02`), basta configurar o arquivo `jboss-service` dentro da pasta `conf` de cada instância (`minimal`, `default`, `all`) apontando para um `ServerName` diferente, ou seja, `ports-default`, `ports-01` ou `ports-02` sendo que todas as instâncias vão se carregar neste mesmo arquivo, `sample-bindings.xml` somente utilizando um conjunto de portas diferentes, carregando portas diferentes pra cada instância.

Depois, é só rodar `run.bat` com o nome da instância (`minimal`, `default` ou `all`).

{% highlight bash %}
run.bat -c default
{% endhighlight %}

Fonte: Post do usuário [rogeriofr](http://javafree.uol.com.br/viewprofile.jbb?u=6286) no [JavaFree](http://javafree.uol.com.br/topic-848360-Duas-instancias-do-JBoss-com-ejb-na-mesma-maquina.html#ixzz2LwU27mXm).
