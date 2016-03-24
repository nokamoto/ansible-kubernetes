# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.ssh.insert_key = false

  N = 2
  (1..N).each do |id|
    config.vm.define "node#{id}" do |node|
      node.vm.box = "bento/centos-7.1"
      node.vm.network "private_network", ip: "192.168.33.#{10+id}"

      if id == N
        node.vm.provision :ansible do |ansible|
          ansible.verbose = "v"
          ansible.limit = "all"
          ansible.inventory_path = "./local"
          ansible.playbook = "bootstrap-centos71.yml"
          ansible.extra_vars = { env: "local" }
        end
      end
    end
  end
end
