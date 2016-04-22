# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.ssh.insert_key = false
  config.vm.synced_folder ".", "/vagrant", disabled: true

  N = 3
  (1..N).each do |id|
    config.vm.define "node#{id}" do |node|
      node.vm.box = "bento/centos-7.1"
      node.vm.network "private_network", ip: "192.168.33.#{10+id}"

      if id == N
        playbooks = ["bootstrap-centos71.yml", "kubernetes-master-centos71.yml", "kubernetes-minion-centos71.yml", "kubernetes-yaml.yml"]
        playbooks.each do |playbook|
          node.vm.provision :ansible do |ansible|
            ansible.verbose = "v"
            ansible.limit = "all"
            ansible.inventory_path = "./local"
            ansible.playbook = playbook
          end
        end
      end
    end
  end
end
