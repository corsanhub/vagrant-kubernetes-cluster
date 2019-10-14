IMAGE_NAME = "bento/ubuntu-18.04"
N = 2

Vagrant.configure("2") do |config|
    config.ssh.insert_key = false

    config.vm.define "k8s-master" do |master|
        master.vm.box = IMAGE_NAME
        master.vm.network "private_network", ip: "10.30.50.10"
        master.vm.hostname = "k8s-master"
        master.vm.provision "ansible" do |ansible|
            ansible.playbook = "kubernetes-setup/master-playbook.yml"
            ansible.extra_vars = {
                node_ip: "10.30.50.10",
            }
        end
        master.vm.provider "virtualbox" do |vbox|
            vbox.customize ["modifyvm", :id, "--memory", 2048]
            vbox.customize ["modifyvm", :id, "--cpus", 2]
            vbox.customize ["modifyvm", :id, "--name", "k8s-master"]
        end
    end

    (1..N).each do |i|
        config.vm.define "k8s-node-#{i}" do |node|
            node.vm.box = IMAGE_NAME
            node.vm.network "private_network", ip: "10.30.50.#{i + 10}"
            node.vm.hostname = "k8s-node-#{i}"
            node.vm.provision "ansible" do |ansible|
                ansible.playbook = "kubernetes-setup/node-playbook.yml"
                ansible.extra_vars = {
                    node_ip: "10.30.50.#{i + 10}",
                }
            end
            node.vm.provider "virtualbox" do |vbox|
                vbox.customize ["modifyvm", :id, "--memory", 2048]
                vbox.customize ["modifyvm", :id, "--cpus", 2]
                vbox.customize ["modifyvm", :id, "--name", "k8s-node-#{i}"]
            end
        end
    end
end

