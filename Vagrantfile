VAGRANT_API_VERSION = "2"

Vagrant.configure(VAGRANT_API_VERSION) do |config|
  # Use the same key for each machine
  config.ssh.insert_key = false

  # Provision all VMs with the same cpu and memory config
  # Otherwise, specificy inside config.vm.define
  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.cpus = 1
  end  

  # Proxy servers
  config.vm.define "proxy1" do |proxy1|
    proxy1.vm.box = "debian/buster64"
    proxy1.vm.hostname = "proxy1"
    proxy1.vm.network "private_network", ip: "192.168.60.11"
    proxy1.vm.provision "ansible" do |ansible|
      ansible.inventory_path = "inventories/vagrant"
      ansible.playbook = "main.yml"
    end
  end
  config.vm.define "proxy2" do |proxy2|
    proxy2.vm.box = "debian/buster64"
    proxy2.vm.hostname = "proxy2"
    proxy2.vm.network "private_network", ip: "192.168.60.12"
    proxy2.vm.provision "ansible" do |ansible|
      ansible.inventory_path = "inventories/vagrant"
      ansible.playbook = "main.yml"
    end
  end

  # Web servers
  config.vm.define "web1" do |web1|
    web1.vm.box = "debian/buster64"
    web1.vm.hostname = "web1"
    web1.vm.network "private_network", ip: "192.168.60.21"
    web1.vm.provision "ansible" do |ansible|
      ansible.inventory_path = "inventories/vagrant"
      ansible.playbook = "main.yml"
    end
  end
  config.vm.define "web2" do |web2|
    web2.vm.box = "debian/buster64"
    web2.vm.hostname = "web2"
    web2.vm.network "private_network", ip: "192.168.60.22"
    web2.vm.provision "ansible" do |ansible|
      ansible.inventory_path = "inventories/vagrant"
      ansible.playbook = "main.yml"
    end
  end
end
