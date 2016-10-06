# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"
LOCAL_CODE_DIRECTORY = '~/tack'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "ubuntu/trusty64"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  config.vm.network "forwarded_port", guest: 443, host: 4443

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.33.33"

  # If true, then any SSH connections made will enable agent forwarding.
  # Default value: false
  config.ssh.forward_agent  = true
  config.ssh.insert_key     = false

  # NFS NOTES:
  # - NFS mount support is native on OSX and Linux
  # - For Windows support, you will need to run: vagrant plugin install vagrant-winnfsd
  # - You will need to enter your local password for the mount directory to sync.
  # - You will need to enter the vagrant user password on login (default=vagrant)
  # - All synced code on the VM will live in ~/code. It will need to be synced from a local directory (default=~/tack)

  # NFS Mount Options for Speedy Vagrant NFS - https://www.jverdeyen.be/vagrant/speedup-vagrant-nfs/
  config.vm.synced_folder LOCAL_CODE_DIRECTORY, '/home/vagrant/code', type: 'nfs', mount_options: ['rw', 'vers=3', 'tcp', 'fsc' ,'actimeo=2']

  # VirtualBox Provider
  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "512"]
  end

  # Ansible provisioning
  config.vm.provision :ansible do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    ansible.sudo = true
  end

  # Shell Provision - Symlinks vagrant_bootstrap.sh
  # config.vm.provision "shell", inline: "ln -sf /vagrant/vagrant_bootstrap.sh /home/vagrant/vm_bootstrap.sh"

end
