# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "ubuntu/trusty64"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.synced_folder "./ansible", "/vagrant_data"

 config.vm.define "opendj" do |v|
        v.vm.hostname = "openam.example.com"
        v.vm.network :private_network, ip: "192.168.33.12"
	v.vm.provider :virtualbox do |vb|
          vb.customize ["modifyvm", :id, "--memory", "2048"]
	end
        v.vm.provision "shell", inline: <<-SHELL
          apt update
          apt install -y openjdk-7-jdk unzip
        SHELL
    end

  config.vm.define "master" do |master|
    
   master.vm.network "private_network", ip: "192.168.33.10"
  
    master.vm.provision "shell", inline: <<-SHELL
      apt update
      apt install -y python python-pip python-dev libffi-dev libssl-dev libxml2-dev libxslt1-dev libjpeg8-dev zlib1g-dev sshpass python-ldap
      pip install ansible
    SHELL
  end
end
