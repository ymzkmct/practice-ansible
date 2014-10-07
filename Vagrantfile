# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # web servers
  config.vm.define "web" do |node|
    node.vm.box = "chef/centos-6.5"
    node.vm.hostname = "web"
    node.vm.network :private_network, ip:"192.168.43.20"

    node.vm.provision :ansible do |ansible|
      ansible.playbook = "ansible/webservers.yml"
      ansible.limit = 'web'
    end

  end

  # mysql servers
  config.vm.define "mysql-master" do |node|
    node.vm.box = "chef/centos-6.5"
    node.vm.hostname = "mysql-master"
    node.vm.network :private_network, ip:"192.168.43.30"

    node.vm.provision :ansible do |ansible|
      ansible.playbook = "ansible/mysqlservers.yml"
      ansible.limit = 'mysql-master'
    end
  end
  config.vm.define "mysql-slave" do |node|
    node.vm.box = "chef/centos-6.5"
    node.vm.hostname = "mysql-slave"
    node.vm.network :private_network, ip:"192.168.43.31"

    node.vm.provision :ansible do |ansible|
      ansible.playbook = "ansible/mysqlservers.yml"
      ansible.limit = 'mysql-slave'
    end
  end

end
