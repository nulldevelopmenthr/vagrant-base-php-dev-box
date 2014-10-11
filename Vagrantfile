# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty32"
   
  config.vm.network "private_network", ip: "10.1.0.80"
  config.vm.synced_folder ".", "/vagrant", type: "nfs"
    
  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--memory", 1024]
    v.customize ["modifyvm", :id, "--ioapic", "on"]
    v.customize ["modifyvm", :id, "--cpus", "2"]
  end

  config.vm.provision :ansible do |ansible|
    ansible.playbook = "etc/provisioning/setup.yml"
    ansible.inventory_path = "etc/provisioning/hosts"
    ansible.verbose = true
    ansible.limit = 'all'
  end
end
