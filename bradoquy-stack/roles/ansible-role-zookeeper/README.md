ansible-role-zookeeper
=========


instalação do ZooKeeper

Variáveis 
--------------

Esta Role possui algumas variáveis "default" no arquivo _main.yml_ que está disponível no diretório defaults.

Dependências
------------

Esta Role depende de outra Role para instalação "ansible-role-java". 


Exemplo de Playbook
----------------

O grupo de hosts para instalação do ZooKeeper, em seu inventário, deve seguir exatamente o exemplo do playbook abaixo:

```yaml
 - hosts: zookeeper
      become: true
      roles:
         - ansible-role-zookeeper
```

