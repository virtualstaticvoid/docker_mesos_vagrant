# Mesos + Marathon Example

Inspired by [mesosphere-docker](https://github.com/sekka1/mesosphere-docker/blob/master/README.md) this is a fully working setup for Vagrant.

## Requirements

* [Vagrant](https://www.vagrantup.com)
* Vagrant [trusty64](https://vagrantcloud.com/ubuntu/boxes/trusty64) - Ubuntu 14.04 64 bit

## Getting Started

### Get the sources

```bash
git clone git@bitbucket.org:virtualstaticvoid/docker_mesos_vagrant.git
cd docker_mesos_vagrant
git submodule init
git submodule update
```

### On the host, start the vagrant box

```bash
vagrant up
```

### Login to the vagrant, and run docker containers

```bash
vagrant ssh
cd /vagrant
./init
```

### On the host, open the mesos web console

[http://localhost:5050](http://localhost:5050)

### On the host, open the marathon web console

[http://localhost:8080](http://localhost:8080)
