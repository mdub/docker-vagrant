# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.berkshelf.enabled = true

  config.vm.provision :shell, :inline => <<-BASH
    set -e
    apt-get update
    apt-get -y install python-software-properties
    apt-add-repository ppa:brightbox/ruby-ng
    apt-get update
    apt-get -y install ruby1.9.3 ruby-switch build-essential
    ruby-switch --set ruby1.9.1
    gem install chef --no-ri --no-rdoc
  BASH

  config.vm.provision :chef_solo do |chef|
    chef.add_recipe 'docker'
  end

  config.vm.synced_folder "#{ENV['HOME']}/Projects", "/projects"

end
