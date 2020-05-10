# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "generic/ubuntu2004"
  config.vm.hostname = "level1"

  config.vm.synced_folder ".", "/vagrant", type: "rsync",
                          rsync__exclude: ".git/"
  box_folder=ENV['HOME'] + "/.vagrant.d"
  config.vm.synced_folder box_folder, "/vagrant.d", type: "nfs"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", inline: <<-SHELL
   dpkg -i /vagrant/vagrant*.deb
   mkdir -p /root/.vagrant.d/
   ln -s /vagrant.d /root/.vagrant.d
  SHELL

  config.vm.provider :libvirt do |libvirt|
    # Enable KVM nested virtualization
    libvirt.nested = true
    libvirt.cpu_mode = "host-model"

    # Increase memory allocation
    libvirt.memory = 4096

    # Use a different management network
    libvirt.management_network_name = 'vagrant-libvirt-level1'
    libvirt.management_network_address = '192.168.124.0/24'
  end

  #  apt caching
  if Vagrant.has_plugin?("vagrant-cachier")
    # Configure cached packages to be shared between instances of the same base box.
    # More info on http://fgrehm.viewdocs.io/vagrant-cachier/usage
    config.cache.scope = :box

    # OPTIONAL: If you are using VirtualBox, you might want to use that to enable
    # NFS for shared folders. This is also very useful for vagrant-libvirt if you
    # want bi-directional sync
    config.cache.synced_folder_opts = {
      type: :nfs,
      # The nolock option can be useful for an NFSv3 client that wants to avoid the
      # NLM sideband protocol. Without this option, apt-get might hang if it tries
      # to lock files needed for /var/cache/* operations. All of this can be avoided
      # by using NFSv4 everywhere. Please note that the tcp option is not the default.
      mount_options: ['rw', 'vers=3', 'tcp', 'nolock']
    }
  end
end