docker-vagrant
==============

A basic Ubuntu (precise64) Vagrant, for playing with [Docker](http://www.docker.io).

The Docker project actually includes it's own Vagrantfile, but this one is a little different:

- assumes (VirtualBox) guest extensions are already installed
- installs Chef (using Omnibus package)
- installs Docker and Ruby-1.9 using Chef
