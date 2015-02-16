# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"
$init = <<SCRIPT
sudo apt-get -y update
sudo apt-get install -y git python-pip
sudo pip install -r /vagrant/requirements.txt
SCRIPT

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  
  config.vm.provider "virtualbox" do |v|
    v.memory = 512
    v.cpus = 1
  end
  
  config.vm.define "server" do |v|
    v.vm.box = "ubuntu/trusty64"
    v.vm.hostname = "server"
    v.vm.network "private_network", ip: "192.168.33.20"
    v.ssh.forward_agent = true
    v.vm.provision :shell, :inline => $init
  end
  
end
