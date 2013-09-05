# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # Setup virtual machine box. This VM configuration code is always executed.
  config.vm.box = "ubuntu"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.vm.provision :shell, :inline => <<-BASH

    sed -i -e 's/us\.archive\.ubuntu\.com/au.archive.ubuntu.com/g' /etc/apt/sources.list

    wget -q -O - https://get.docker.io/gpg | apt-key add -
    echo deb http://get.docker.io/ubuntu docker main > /etc/apt/sources.list.d/docker.list
    apt-get update

    # Docker
    apt-get install -y --force-yes lxc-docker

    # Ubuntu raring backported kernel
    apt-get install -y linux-image-generic-lts-raring

  BASH

  config.vm.synced_folder "#{ENV['HOME']}/Projects", "/projects"
  config.vm.network :forwarded_port, host: 8888, guest: 80

end
