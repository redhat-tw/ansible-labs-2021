# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ansible/tower"
  config.vm.box_version = "3.7.5"
  config.vm.network "private_network", ip: "172.16.33.10"
  config.vm.synced_folder "./", "/vagrant"
  config.vm.provider "virtualbox" do |vb|
    vb.name = "tower"
    vb.memory = 4096
    vb.cpus = 2
  end
end