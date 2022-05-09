<h1 align="center">Welcome to aggrandize-kafka-cluster-registry 👋</h1>
<p>
  <img alt="Version" src="https://img.shields.io/badge/version-1.0.0-blue.svg?cacheSeconds=2592000" />
  <img src="https://img.shields.io/badge/npm-%3E%3D5.5.0-blue.svg" />
  <img src="https://img.shields.io/badge/node-%3E%3D9.3.0-blue.svg" />
  <a href="https://github.com/kefranabg/readme-md-generator#readme" target="_blank">
    <img alt="Documentation" src="https://img.shields.io/badge/documentation-yes-brightgreen.svg" />
  </a>
  <a href="https://github.com/kefranabg/readme-md-generator/graphs/commit-activity" target="_blank">
    <img alt="Maintenance" src="https://img.shields.io/badge/Maintained%3F-yes-green.svg" />
  </a>
  <a href="https://github.com/kefranabg/readme-md-generator/blob/master/LICENSE" target="_blank">
    <img alt="License: MIT" src="https://img.shields.io/github/license/oliveiha/aggrandize-kafka-cluster-registry" />
  </a>
  <a href="https://twitter.com/hdoliveiha" target="_blank">
    <img alt="Twitter: hdoliveiha" src="https://img.shields.io/twitter/follow/hdoliveiha.svg?style=social" />
  </a>
</p>

> kafka cluster with [ZooKeeper, Kafka, Schema Registry, REST Proxy, Confluent Control Center, Kafka Connect (distributed mode), KSQL Server ,Replicator]

### 🏠 [Homepage](https://github.com/oliveiha/readme-md-generator#readme)

## Prerequisites

- npm >=5.5.0
- node >=9.3.0

## Install

```sh
npm install
```

## Usage

```sh
npm run start
```

## Run tests

```sh
npm run test
```

## Author

👤 **Tiago Oliveira (tiago.oliveira@aggrandize.com.br)**

* Website: www.bradoquy.com.br
* Twitter: [@hdoliveiha](https://twitter.com/hdoliveiha)
* Github: [@oliveiha](https://github.com/oliveiha)
* LinkedIn: [@tiago-oliveira-6b671710a](https://linkedin.com/in/tiago-oliveira-6b671710a)

## 🤝 Contributing

Contributions, issues and feature requests are welcome!<br />Feel free to check [issues page](https://github.com/oliveiha/readme-md-generator/issues). You can also take a look at the [contributing guide](https://github.com/oliveiha/readme-md-generator/blob/master/CONTRIBUTING.md).

## Show your support

Give a ⭐️ if this project helped you!

## 📝 License

Copyright © 2022 [Tiago Oliveira (tiago.oliveira@aggrandize.com.br)](https://github.com/oliveiha).<br />
This project is [MIT](https://github.com/oliveiha/readme-md-generator/blob/master/LICENSE) licensed.

***
_This README was generated with ❤️ by [readme-md-generator](https://github.com/kefranabg/readme-md-generator)_


# Doc
[Confluence Doc](https://docs.confluent.io/platform/current/quickstart/ce-docker-quickstart.html#step-2-create-ak-topics)


# Install
1. Run the following command to download the CP Ansible Playbook:
```bash
ansible-galaxy collection install git+https://github.com/confluentinc/cp-ansible.git
```

2. Copy the following into a file called ansible.cfg that can be saved in the current directory
```
[defaults]
hash_behaviour=merge
```

3. Copy the following into a file called hosts.yml that can be saved in the current directory

```yaml
all:
  vars:
    ansible_connection: ssh
    ansible_user: ec2-user
    ansible_become: true
    ansible_ssh_private_key_file: /root/.ssh/
    ansible_ssh_common_args: -o StrictHostKeyChecking=no

zookeeper:
  hosts:
    ec21:

kafka_broker:
  hosts:
    ec22:
    ec23:
    ec24:

schema_registry:
  hosts:
    ec25:

ksql:
  hosts:
    ec25:

kafka_connect:
  hosts:
    ec25:
      vars:
        kafka_connect_confluent_hub_plugins:
          - confluentinc/kafka-connect-datagen:0.4.0

control_center:
  hosts:
    ec26:
```

#### Config distribution
```
################################################################################
# Egress access for all 6 machines
################################################################################
Allow
port: any
protocol: any
to ip/ipBlock: 0.0.0.0/0
################################################################################
# SSH access for all 6 machines
################################################################################
Allow
port: 22
protocol: TCP
from ip/ipBlock: your workstation
################################################################################
# 1
################################################################################
# For Zookeeper
Allow
port: 2181
protocol: TCP
from ip/ipBlock: 2, 3, 4
################################################################################
# 2, 3, 4
################################################################################
# For inter broker communication
Allow
port: 9091
protocol: TCP
from ip/ipBlock: 2, 3, 4
# For Kafka AdminClient API, custom applications, etc
Allow
port: 9092
protocol: TCP
from ip/ipBlock: 0.0.0.0/0
// Alternatively for more restrictive use, only allow ingress from 5, 6, and your workstation
# OPTIONAL: For MDS & Embedded Kafka Rest
Allow
port: 8090
protocol: TCP
to ip/ipBlock: 0.0.0.0/0
// Alternatively for more restrictive use, only allow ingress from 6 and your workstation
# OPTIONAL: For Standalone REST Proxy
Allow
port: 8082
protocol: TCP
to ip/ipBlock: 0.0.0.0/0
// Alternatively for more restrictive use, only allow ingress from 6 and your workstation
################################################################################
# 5
################################################################################
# For Kafka Connect
Allow
port: 8083
protocol: TCP
from ip/ipBlock: 0.0.0.0/0
// Alternatively for more restrictive use, only allow ingress from 6 and your workstation
# For KSQL
Allow
port: 8088
protocol: TCP
from ip/ipBlock: 0.0.0.0/0
// Alternatively for more restrictive use, only allow ingress from 6 and your workstation
# For Schema Registry
Allow
port: 8081
protocol: TCP
from ip/ipBlock: 0.0.0.0/0
// Alternatively for more restrictive use, only allow ingress from 6 and your workstation
################################################################################
# 6
################################################################################
# For browser access to Confluent Control Center
Allow
port: 9021
protocol: TCP
from ip/ipBlock: 0.0.0.0/0
// Alternatively for more restrictive use, only allow ingress from your workstation
# For Metadata Service and Embedded Kafka REST
Allow
port: 8090
protocol: TCP
to ip/ipBlock: 0.0.0.0/0
// Alternatively for more restrictive use, only allow ingress from 6 and your workstation
```

4. Run the following command: 
```bash
ansible-playbook -i hosts.yml confluent.platform.all
```

The playbook should take about 15 minutes to complete. The results of each intermediate step will be noted in terminal output. If successful, the final output will be similar to below in which failed=0 for all 6 machines.

```bash
PLAY RECAP
******************************************************************************************************************************************************
ec21    : ok=30	changed=15	unreachable=0	failed=0	skipped=27	rescued=0	ignored=0
ec22    : ok=38	changed=25	unreachable=0	failed=0	skipped=30	rescued=0	ignored=0
ec23    : ok=38	changed=10	unreachable=0	failed=0	skipped=29	rescued=0	ignored=0
ec24    : ok=38	changed=12	unreachable=0	failed=0	skipped=29	rescued=0	ignored=0
ec25    : ok=81	changed=57	unreachable=0	failed=0	skipped=88	rescued=0	ignored=0
ec26    : ok=81	changed=57	unreachable=0	failed=0	skipped=88	rescued=0	ignored=0
```



