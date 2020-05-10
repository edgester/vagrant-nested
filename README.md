# vagrant-nested

A vagrant config for running nested VMs and testing Vagrant using
VirtualBox when you're using libvirt on your host.

sudo apt-get install qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils


sudo apt install virtualbox

Ref: https://nts.strzibny.name/inception-running-vagrant-inside-vagrant-with-kvm/


## Prequisites

This project was developed and tested on Ubuntu 18.04 using the vagrant libvirt plugin.

The configuration assumes that you're running the vagrant-cachier plugin and a local NFS server.


Install vagrant-cachier to save on repeated package download times (optional):

  vagrant plugin install vagrant-cachier

Install the NFS server on Ubuntu:

  sudo apt instal nfs-server

