# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/8"
  config.vm.box_version = "1905.1"
  config.ssh.insert_key = false

  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--audio", "none"]
    vb.memory = 256
  end

  config.vm.define "application_servers" do |app_server_1|
    app_server_1.vm.hostname = "centos.httpd.test"
    app_server_1.vm.network :private_network, ip: "192.168.55.5"
    config.vm.network :forwarded_port, host: 80, guest: 80 
  end

  config.vm.provision "ansible" do |ansible|
    ansible.host_key_checking = false
    ansible.playbook = "playbook.yml"
    ansible.inventory_path = "inventory.ini"
  end
end
