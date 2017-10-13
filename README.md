vagrant-docker-compose-nginx-example
==

Deploy nginx container using Docker Compose as Vagrant provisioner, with CentOS7.

Created on following environments.

- Ubuntu 16.04.3 LTS (xenial)
- Vagrant 2.0.0
- VirtualBox 5.1.28
- CentOS/7
- Docker 17.09.0-ce
- Docker Compose 1.11.2

## Requirements

- vagrant-vbguest
- vagrant-docker-compose
- vagrant-hostsupdater

Install plguins

```
$ vagrant plugin install vagrant-vbguest
$ vagrant plugin install vagrant-docker-compose
$ vagrant plugin install vagrant-hostsupdater
```

## Start Virtual Machine

```
$ cd /path/to/repos
$ vagrant up
```

Once provisioning done successfully, you can confirm a working nginx application via browsers by accessing to [`http://localhost`](http://localhost).

## Licence

[MIT](https://github.com/orih/vagrant-docker-compose-example/blob/master/LICENCE)

## Author

[rubankumars](https://github.com/rubankumars)
