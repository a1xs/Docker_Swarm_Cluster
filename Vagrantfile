# -*- mode: ruby -*-
# vi: set ft=ruby :

$node_mach = 4

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.box_check_update = false

   (1..$node_mach).each do |i|
  	config.vm.define "node-#{i}" do |node|
#  	     node.vm.network  "public_network", ip: "192.168.2.#{250+i}"
# автовыбор сетевого интерфейса bridge: "wlp0s20f3"
         node.vm.network  "public_network", ip: "192.168.2.#{250+i}", bridge: "wlp0s20f3"

         node.vm.hostname = "node-#{i}"
         node.vm.provider "virtualbox" do |vb|
                vb.memory = "1024"

#    config.vm.provision "ansible" do |ansible|
#    ansible.verbose = "v"
#    ansible.playbook = "deploy.yml"
#  end
         end
      end
   end
    config.vm.provision "shell", path: "script/AddUserAndKey.sh"
end
