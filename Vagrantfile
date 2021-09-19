IMAGE_NAME = "generic/ubuntu1804"

Vagrant.configure("2") do |config|
    config.ssh.insert_key = false
    config.vm.box_check_update = false 
    config.vm.synced_folder ".", "/vagrant", disabled: false

    config.vm.provider "virtualbox" do |v|
        v.memory = 2048
        v.cpus = 2
    end
      
    config.vm.define "k8s-master" do |master|
        master.vm.box = IMAGE_NAME
        master.vm.network "private_network", ip: "192.168.50.10"
        master.vm.hostname = "k8s-master"
        master.vm.provision "ansible" do |ansible|
            ansible.playbook = "setup-playbook/master-playbook.yml"
            ansible.extra_vars = {
                node_ip: "192.168.50.10",
            }
        end
    end


    config.vm.define "k8s-worker1" do |node|
        node.vm.box = IMAGE_NAME
        node.vm.network "private_network", ip: "192.168.50.11"
        node.vm.hostname = "k8s-worker1"
        node.vm.provision "ansible" do |ansible|
            ansible.playbook = "setup-playbook/node-playbook.yml"
            ansible.extra_vars = {
                 node_ip: "192.168.50.11",
            }
        end
    end

    config.vm.define "common" do |node|
        node.vm.box = IMAGE_NAME
        node.vm.network "private_network", ip: "192.168.50.12"
        node.vm.hostname = "common"
        node.vm.provision "ansible" do |ansible|
            ansible.playbook = "setup-playbook/common-playbook.yml"
        end
    end
end
