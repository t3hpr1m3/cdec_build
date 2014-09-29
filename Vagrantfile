# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure('2') do |config|
  config.vm.box = 'precise64'
  config.vm.box_url = 'http://files.vagrantup.com/precise64.box'
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
  config.ssh.forward_agent = true
  config.ssh.forward_x11 = true

  config.vm.provider :virtualbox do |vb|
    vb.customize ['modifyvm', :id, '--natdnshostresolver1', 'on']
    vb.customize ['modifyvm', :id, '--natdnsproxy1', 'on']
    vb.cpus = 2
    vb.memory = 1024
  end

  config.vm.boot_timeout = 120

  config.omnibus.chef_version = :latest

  if Vagrant.has_plugin?('vagrant-cachier')
    config.cache.scope = :box
  end

  if Vagrant.has_plugin?('berkshelf')
    config.berkshelf.enabled = true
  end

  config.vm.network :private_network, ip: '10.2.2.2'
  config.vm.synced_folder '.', '/vagrant', type: 'nfs'

  config.vm.provision :chef_solo do |chef|
    chef.custom_config_path = 'Vagrantfile.chef'
    chef.add_recipe 'cdec'
  end
end

