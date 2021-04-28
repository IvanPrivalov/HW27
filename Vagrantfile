# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "centos/7"
  
  config.vm.provider "virtualbox" do |v|
    v.memory = 512
    v.cpus = 1
  end

  config.vm.define "master" do |server|
    server.vm.network "private_network", ip: "192.168.11.10"
    server.vm.hostname = "master"
  end

  config.vm.define "slave" do |client|
    client.vm.network "private_network", ip: "192.168.11.20"
    client.vm.hostname = "slave"
  end

  config.vm.provision "mysql_replication", type:'ansible' do |ansible|
    ansible.inventory_path = './inventories/all.yml'
    ansible.playbook = './mysql_repl.yml'
  end
end
