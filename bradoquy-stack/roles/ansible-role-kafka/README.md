ansible-role-kafka
=========

Instalação para RedHat

Dependencias
------------
ansible-role-java

Para executar esta Role você deve criar um arquivo de inventário, ou usar o host_example.yml deste repositório, com os grupos **zookeeper** e **kafka_broker** com cada host correspondente em seu grupo.

O Apache Kafka requer o cluster ZooKeeper. No entanto, essa função depende da função ZooKeeper e Java. 

variaveis
--------------

Esta Role tem muitas variáveis e está disponível no arquivo _main.yml_ no diretório _defaults_. Se você deseja alterar as propriedades do kafka broker, crie um arquivo de variáveis para o playbook e defina todos os valores-chave na configuração do seu broker.


Exemplo de Playbook
----------------
```yaml
    - hosts: kafkabroker
      become: true
      roles:
         - kafka
```

