# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.box = "puppetlabs/centos-6.6-64-nocm"
  config.vm.box_url = "https://vagrantcloud.com/puppetlabs/boxes/centos-6.6-64-nocm/versions/1.0.2/providers/virtualbox.box"

  config.vm.define :"web1" do |host|
    host.vm.hostname = "web1"
    host.vm.network :private_network, ip: "192.168.100.11", netmask: "255.255.255.0"
    host.vm.synced_folder ".", "/vagrant"
    host.vm.synced_folder "./fuelphp", "/srv/example/fuelphp", mount_options: ['dmode=777','fmode=666']
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/site.yml"
    ansible.inventory_path = "provisioning/hosts"
    ansible.limit = 'all'
  end
end
