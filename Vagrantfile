# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "trusty64"

  config.vm.provider :virtualbox do |vbox, override|
    vbox.customize ['modifyvm', :id, '--memory', 1024]
  end

  # zookeeper
  config.vm.network :forwarded_port, :guest => 2181, :host => 2181

  # mesos
  config.vm.network :forwarded_port, :guest => 5050, :host => 5050

  # marathon
  config.vm.network :forwarded_port, :guest => 8080, :host => 8080

  # chronos
  config.vm.network :forwarded_port, :guest => 4400, :host => 4400

  # slave ports for applications
  (31000..31010).each do |port|
    config.vm.network :forwarded_port, :guest => port, :host => port
  end

  config.vm.provision :shell do |s|
    s.inline = <<-BASH
      sudo apt-get update;
      sudo apt-get install -y htop;
    BASH
  end

  config.vm.provision "docker",
                      :images => [
                        'debian:jessie',
                        'ubuntu:14.04',
                        'garland/zookeeper:latest',
                        'garland/mesosphere-docker-base-image',
                        'garland/mesosphere-docker-mesos-master',
                        'garland/mesosphere-docker-marathon'
                      ]

end
