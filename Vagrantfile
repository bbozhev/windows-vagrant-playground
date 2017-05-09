# -*- mode: ruby -*-
# vi: set ft=ruby :
# Issues with Landrush and vagrant 1.9.0 so for now disabling landrush
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "geerlingguy/centos7"
  config.ssh.insert_key = false
  config.vm.synced_folder ".", "/var/www/html/", type: "virtualbox"
  config.vm.provider :virtualbox do |v|
    v.name = "websrv.dev"
    v.memory = 1024
    v.cpus = 2
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--ioapic", "on"]
  end

  config.vm.hostname = "websrv.dev"
  config.vm.network "private_network", ip: "10.0.1.1", auto_config: "true"
  config.vm.define :websrv do |websrv|
  end

end
