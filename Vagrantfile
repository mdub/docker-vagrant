# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.berkshelf.enabled = true

  config.vm.provision :shell, :inline => <<-BASH
    chef-solo --version | grep 'Chef: 10' || (apt-get -y install curl; curl -s -L https://www.opscode.com/chef/install.sh | bash -s -- -v 10.28.0)
  BASH

  config.vm.provision :chef_solo do |chef|
    chef.add_recipe 'docker'
    chef.add_recipe 'brightbox::ruby'
  end

end
