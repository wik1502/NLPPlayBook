# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "server_db" do |node|
    node.vm.box = "centos/7"
    node.vm.network "private_network", ip:"192.168.33.10"
    node.vm.synced_folder ".", "/vagrant"
  end

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.inventory_path = "inventory"
    ansible.limit = "server_db"
  end

  config.vm.provider "virtualbox" do |v|
    v.gui = false
  end

end
