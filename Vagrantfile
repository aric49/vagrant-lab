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

  #Deploy 4 Node Lab:
  config.vm.define "node01" do |node01|
    node01.vm.box = "ubuntu/xenial64"
    node01.vm.hostname = 'node01'
    node01.vm.network :forwarded_port, guest: 22, host: 2022, id: "ssh"
  end

  config.vm.define "node02" do |node02|
    node02.vm.box = "ubuntu/xenial64"
    node02.vm.hostname = 'node02'
    node02.vm.network :forwarded_port, guest: 22, host: 2023, id: "ssh"
  end

  config.vm.define "node03" do |node03|
    node03.vm.box = "ubuntu/xenial64"
    node03.vm.hostname = 'node03'
    node03.vm.network :forwarded_port, guest: 22, host: 2024, id: "ssh"
  end


  config.vm.define "node04" do |node04|
    node04.vm.box = "ubuntu/xenial64"
    node04.vm.hostname = 'node04'
    node04.vm.network :forwarded_port, guest: 22, host: 2025, id: "ssh"
  end
  #config.vm.box = "ubuntu/xenial64"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  # config.push.define "atlas" do |push|
  #   push.app = "YOUR_ATLAS_USERNAME/YOUR_APPLICATION_NAME"
  # end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.

  #Install Python using Shell before running Ansible
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y python2.7 python-simplejson
  SHELL

  #Provision with Ansible
  config.vm.provision "ansible" do |ansible|
    ansible.sudo = true
    ansible.playbook = "Deploy_Lab.yml"
  end
end