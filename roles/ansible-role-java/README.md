# Ansible Role: Java

Installs Java for RedHat/CentOS and Debian/Ubuntu linux servers.

## Requirements

None.

## Variáveis ​​das Roles

As variáveis ​​disponíveis estão listadas abaixo, juntamente com os valores default:

    # Os defaults fornecidos por esta Role são específicos para cada distribuição.
    java_packages:
      - java-1.8.0-openjdk

Defina o kit de versão/desenvolvimento do Java a ser instalado, juntamente com quaisquer outros pacotes Java necessários. Algumas outras opções estão incluídas nos arquivos específicos da distribuição na pasta 'defaults' desta função.

    java_home: ""

Se definido, a função definirá a variável de ambiente global `JAVA_HOME` para esse valor.

## Dependências

Nenhum.

## Exemplo de Playbook (usando o pacote default)

    - hosts: servers
      roles:
        - role: ansible-role-java
          become: yes

## exemplo (instale o OpenJDK 8)

Para RHEL/CentOS:

     - hosts: server
      roles:
        - role: ansible-role-java
          when: "ansible_os_family == 'RedHat'"
          java_packages:
            - java-1.8.0-openjdk

Para Ubuntu < 16.04:

    - hosts: server
      tasks:
        - name: installing repo for Java 8 in Ubuntu
  	      apt_repository: repo='ppa:openjdk-r/ppa'
    
    - hosts: server
      roles:
        - role: geerlingguy.java
          when: "ansible_os_family == 'Debian'"
          java_packages:
            - openjdk-8-jdk


