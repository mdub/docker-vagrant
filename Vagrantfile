# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "precise64"

  config.berkshelf.enabled = true

  config.vm.provision :shell, :inline => <<-BASH
    chef-solo --version | grep 'Chef: 11' || (apt-get -y install curl; curl -s -L https://www.opscode.com/chef/install.sh | bash)
  BASH

  config.vm.provision :chef_solo do |chef|
    chef.add_recipe 'docker'
  end

end
