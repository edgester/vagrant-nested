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


## How to use this thing

1. Install and configure vagrant.

2. Clone the git repo to a local folder.

3. Run "vagrant up" in the project folder. Wait for the VM to come up

4. Run "vagrant ssh" to login to the level1 VM.

5. Run the following commands in the level1 VM


Once you're in the level1 VM, you can run the level2 VM by doing the following:

  sudo -i
  cd /vagrant/level2
  vagrant up
