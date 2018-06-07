# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "guneysu/ubuntu-xenial"
  config.ssh.insert_key = false
  config.vm.provider :virtualbox do |v|
    v.name = "vggw"
    v.memory = 512
    v.cpus = 2
  end
  config.vm.hostname = "vggw"
  config.vm.network :private_network, ip: "192.168.13.13"
  config.vm.network "public_network", ip: "192.168.0.252"
  config.vm.network "public_network", ip: "192.168.0.251"

  # Ansible provisioner.
  config.vm.provision "ansible" do |ansible|
    ansible.limit = "all"
    ansible.playbook = "provisioning/vggw-playbook.yml"
    ansible.inventory_path = "provisioning/inventory"
    ansible.inventory_path = "provisioning/hosts"
  end
end
