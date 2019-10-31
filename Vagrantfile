# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|

    #PROVISIONANDO A MAQUINA DATABASE

    config.vm.define "db" do |db|
    db.vm.box = "ubuntu/bionic64"
    db.vm.hostname = "MiniDc-Database"
    db.vm.network "private_network", ip: "172.17.177.21"
     
    db.vm.provider "virtualbox" do |v|
     v.name = "MiniDC-DataBase"
     v.memory = 512
     v.cpus = 1



    end
  end
    
    #PROVISIONANDO A MAQUINA BLOG

  config.vm.define "blog" do |blog|
    blog.vm.box = "ubuntu/bionic64"
    blog.vm.hostname = "MiniDC-Blog"
    blog.vm.network "private_network", ip: "172.17.177.22"
  
    blog.vm.provider "virtualbox" do |v|
     v.name = "MiniDC-Blog"
     v.memory = 512
     v.cpus = 1
    end
  end

  #PROVISIONANDO A MAQUINA CONTROLLER

  config.vm.define "controller" do |controller|
    controller.vm.box = "ubuntu/bionic64"
    controller.vm.hostname = "MiniDC-AnsibleController"
    controller.vm.network "private_network", ip: "172.17.177.11"

    #Restingindo p permissionamento da pasta vagrant
    controller.vm.synced_folder"./", "/vagrant", mount_options: ["dmode=750,fmode=600"]
    
    #Size da VM
    controller.vm.provider "virtualbox" do |v|
     v.name = "MiniDC-AnsibleController"
     v.memory = 512
     v.cpus = 1

    end

    #Configurando ansible para a maquina controller

     controller.vm.provision :ansible_local do |ansible|
     ansible.install_mode = "default"
     ansible.playbook = "playbook.yml"
     ansible.inventory_path="inventory"
     ansible.verbose  = true
     ansible.install  = true
     ansible.limit    = "all"
      
    end
  end
end
