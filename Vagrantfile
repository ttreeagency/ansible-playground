# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "ttree/wheezy-64-chef"

  config.ssh.forward_agent = true

  config.vm.network :private_network, ip: "192.168.23.4"

  config.vm.provision "ansible" do |ansible|
  	ansible.playbook = "neos.yml"
  end

  config.vm.provider "virtualbox" do |v|
  	v.customize ["modifyvm", :id, "--memory", "2048"]
  end

end
