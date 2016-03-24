# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  (1..2).each do |id|
    config.vm.define "node#{id}" do |node|
      node.vm.box = "bento/centos-6.7"
      node.vm.network "private_network", ip: "192.168.33.#{10+id}"

      node.vm.provision :ansible do |ansible|
        ansible.playbook = "bootstrap-centos67.yml"
        ansible.verbose = "v"
        ansible.extra_vars = {
          env: "local",
          ansible_ssh_user: "vagrant"
        }
      end
    end
  end
end
