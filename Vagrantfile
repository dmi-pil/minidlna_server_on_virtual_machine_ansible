# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/trusty64"

  config.vm.define "node1" do |machine|

    config.vm.hostname = "ubuntu"
  
    config.vm.network "forwarded_port", guest: 8200, host: 8221

    config.vm.network :public_network, ip: "10.10.1.6"

    config.vm.synced_folder "/home/user/Dlna", "/home/vagrant/Dlna"

    config.vm.provider "virtualbox" do |v|
  
        v.gui = false
 
        v.memory = "1024"
    end
  
    config.vm.provision :shell, path: "bootstrap.sh"
   

    config.vm.provision "ansible" do |ansible|
      compatibility_mode = "2.0"
      ansible.playbook = "playbook.yml"
      ansible.inventory_path = "inventory"
      
    end
  end
end
