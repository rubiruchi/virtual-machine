# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANT_COMMAND = ARGV[0]

Vagrant.configure(2) do |config|
  config.vm.box = "debian/jessie64"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.33.10"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end

  if VAGRANT_COMMAND == "ssh"
    config.ssh.username = 'root'
  else
    config.ssh.username = 'vagrant'
  end
  config.ssh.insert_key = "true"
  config.ssh.forward_x11 = "true"

  config.vm.provision "shell", path: "scripts/provision.sh"
end
