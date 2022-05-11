<h1 align="center">Welcome to Bradoquy Ansible Kafka 👋</h1>
<p>
  <img alt="Version" src="https://img.shields.io/badge/version-1.0.0-blue.svg?cacheSeconds=2592000" />
  <img src="https://img.shields.io/badge/node-%3E%3D9.3.0-blue.svg" />
  <a href="https://github.com/oliveiha/bradoquy-ansible-kafka#readme" target="_blank">
    <img alt="Documentation" src="https://img.shields.io/badge/documentation-yes-brightgreen.svg" />
  </a>
  <a href="https://github.com/kefranabg/readme-md-generator/graphs/commit-activity" target="_blank">
    <img alt="Maintenance" src="https://img.shields.io/badge/Maintained%3F-yes-green.svg" />
  </a>
  <a href="https://github.com/oliveiha/bradoquy-ansible-kafka/blob/main/LICENSE" target="_blank">
    <img alt="License: MIT" src="https://img.shields.io/github/license/oliveiha/Bradoquy Ansible Kafka" />
  </a>
  <a href="https://twitter.com/hdoliveiha" target="_blank">
    <img alt="Twitter: hdoliveiha" src="https://img.shields.io/twitter/follow/hdoliveiha.svg?style=social" />
  </a>
</p>

> Ansible Playbooks and roles for build a cluster kafka

### 🏠 [Homepage](https://github.com/oliveiha/bradoquy-ansible-kafka)

### ✨ [Demo](https://github.com/oliveiha/bradoquy-ansible-kafka)

## Prerequisites for Nodes

* install git
* install python3
* nstall setuptools_rust python module
* install --upgrade pip 
* install ansible via pip3
* disable selinux
* stop and disable firewalld

## Install

```sh
#!/bin/bash
echo "Install git"
yum install git

echo "Install python"
yum install python3

echo "Install module rust"
pip3 install setuptools_rust

echo "Upgrade pip"
pip3 install --upgrade pip

echo "Install git"
pip3 install ansible

echo "Stop FirewallD"
systemctl stop firewalld

echo "Disable FirewallD"
systemctl disable firewalld

echo "Disable Selinux"
sed -i --follow-symlinks 's/SELINUX=enforcing/SELINUX=disabled/g' /etc/sysconfig/selinux

echo "Disable Selinux"
setenforce 0
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

👤 **Tiago Oliveira**

* Website: www.bradoquy.com.br
* Twitter: [@hdoliveiha](https://twitter.com/hdoliveiha)
* Github: [@oliveiha](https://github.com/oliveiha)
* LinkedIn: [@tiago-oliveira-6b671710a](https://linkedin.com/in/tiago-oliveira-6b671710a)

## 🤝 Contributing

Contributions, issues and feature requests are welcome!<br />Feel free to check [issues page](https://github.com/oliveiha/bradoquy-ansible-kafka/issues). You can also take a look at the [contributing guide](https://github.com/oliveiha/bradoquy-ansible-kafka/blob/main/CONTRIBUTING.md).

## Show your support

Give a ⭐️ if this project helped you!

## 📝 License

Copyright © 2022 [Tiago Oliveira](https://github.com/oliveiha).<br />
This project is [MIT](https://github.com/oliveiha/bradoquy-ansible-kafka/blob/main/LICENSE) licensed.

***
_This README was generated with ❤️ by [readme-md-generator](https://github.com/kefranabg/readme-md-generator)_