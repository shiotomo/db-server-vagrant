# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu"
  config.vm.hostname = 'carmy'
  config.vm.network "forwarded_port", guest: 5432, host:5432
  config.vm.network "forwarded_port", guest: 3306, host: 3306

  config.vm.network "private_network", ip: "192.168.33.22"

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get -y upgrade
    sudo apt-get install -y python-minimal
  SHELL

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook/site.yml"
    ansible.playbook = "playbook/database.yml"
    ansible.inventory_path = "settings/hosts"
    ansible.limit = "all"
  end

  config.vm.provider "virtualbox" do |vb|
    vb.customize [ "modifyvm", :id, "--uartmode1", "disconnected" ]
  end

  config.vm.synced_folder ".", "/vagrant", disabled: true
end
