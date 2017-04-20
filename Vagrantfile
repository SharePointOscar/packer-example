# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "vagrant_machine"

  config.vm.network :private_network, ip: "192.168.50.5"
  config.vm.network :forwarded_port, guest: 5000, host: 5000
  config.vm.network :forwarded_port, guest: 22, host: 2258

  # Forward X11
  config.ssh.forward_x11 = true

  config.vm.provider "virtualbox" do |v|
    v.gui = true
    v.customize ["modifyvm", :id, "--memory", 2048]
    v.customize ["modifyvm", :id, "--cpus", 2]
    v.customize ["modifyvm", :id, "--vram", 128]
    v.customize ["modifyvm", :id, "--clipboard", "bidirectional"]
    v.customize ["modifyvm", :id, "--accelerate3d", "on"]
    v.customize ["modifyvm", :id, "--accelerate2dvideo", "on"]
    v.linked_clone = true if Vagrant::VERSION =~ /^1.8/

  end


 ## Using NFS as it has much better performance
 ## On linux install nfs-kernel-server, MacOS works by default
 ## Will ask for root password to set some things up
 #config.vm.synced_folder ".", "/vagrant", :nfs => true
 config.vm.synced_folder ".", "/vagrant", disabled: true
end
