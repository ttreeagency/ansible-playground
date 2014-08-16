# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

host = RbConfig::CONFIG['host_os']
if host =~ /darwin/
  cpus = `sysctl -n hw.ncpu`.to_i
  mem = `sysctl -n hw.memsize`.to_i / 1024 / 1024 / 4
elsif host =~ /linux/
  cpus = `nproc`.to_i
  mem = `grep 'MemTotal' /proc/meminfo | sed -e 's/MemTotal://' -e 's/ kB//'`.to_i / 1024 / 4
else
  cpus = 2
  mem = 1024
end

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define 'webserver' do |machine|
    machine.vm.hostname = 'typo3-playground.box'

    machine.vm.network "private_network", ip: "192.168.77.21"
    machine.vm.box = "ttree/wheezy-64-chef"

	machine.ssh.forward_agent = true

	config.vbguest.auto_update = false

    machine.vm.provider "virtualbox" do |v|
      v.customize ["modifyvm", :id, "--memory", mem]
    end

    machine.vm.provision "ansible" do |ansible|
	  ansible.playbook = "provisioning/neos.yml"
	  ansible.groups = {
	    "dbserver" => ["webserver"],
	    "webserver" => ["webserver"],
	    "webserver-nginx" => ["webserver"]
	  }
	  ansible.extra_vars = {
	    ansible_ssh_user: 'vagrant',
	    ansible_sudo: 'Yes'
	  }
    end
  end

end
