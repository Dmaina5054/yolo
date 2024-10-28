# -*- mode: ruby -*-
# vi: set ft=ruby :

#using version 2
Vagrant.configure("2") do |config|

  config.vm.define "backendserver" do |host1|
    host1.vm.box = "geerlingguy/ubuntu2004"
    host1.vm.network "private_network", ip: "192.168.56.10"  # IP for backendserver
  end

  config.vm.define "frontendserver" do |host2|
    host2.vm.box = "geerlingguy/ubuntu2004"
    host2.vm.network "private_network", ip: "192.168.56.11"  # IP for frontendserver
  end

  config.vm.define "mongodbserver" do |host2|
    host2.vm.box = "geerlingguy/ubuntu2004"
    host2.vm.network "private_network", ip: "192.168.56.12"  # IP for mongodbserver
  end
  

  config.vm.provider "virtualbox" do |vb|

    # Customize the amount of memory on the VM:
    vb.memory = "1024"
  end
  
  # Provisioning Ansible on vagrant guest
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/playbook.yml"
  end

end
