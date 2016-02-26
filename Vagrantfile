# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define :vagrantwin12 do |cfg|
    cfg.vm.box = "mwrock/Windows2012R2"
    cfg.vm.communicator = "winrm"
    cfg.vm.guest = :windows
    cfg.vm.network :private_network, :ip => "192.168.33.41"

    cfg.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--hardwareuuid", "02f110e7-369a-4bbc-bbe6-6f0b6864ccb6"]
      vb.gui = true
      vb.memory = "1024"
    end
  end

  # Ansible provisioner.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "manage.yml"
    ansible.inventory_path = "hosts"
    ansible.sudo = true
  end

end
