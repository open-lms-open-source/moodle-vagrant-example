# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # Latest Ubuntu 16.04 box.
  config.vm.box = "moodlerooms/ubuntu-16.04-moodle-dev"

  # Host manager plugin settings.  This updates /etc/hosts on guest and host.
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
  config.hostmanager.aliases = %w(moodle.dev core-moodle.dev webgrind.dev)

  # Forward port for MySQL.
  config.vm.network "forwarded_port", guest: 3306, host: 3306

  # Forward port for PostgreSQL.
  config.vm.network "forwarded_port", guest: 5432, host: 5432

  # Create a private network, which allows host-only access to the machine using a specific IP.
  config.vm.network "private_network", ip: "192.168.100.100"

  # If true, then any SSH connections made will enable agent forwarding.
  config.ssh.forward_agent = true

  # Mount current directory to the /vagrant directory in the VM.
  config.vm.synced_folder ".", "/vagrant", type: "nfs"

  # Customize virtual machine.
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", "8192"]
    vb.customize ["modifyvm", :id, "--name", "moodle-dev-example"]
  end
end
