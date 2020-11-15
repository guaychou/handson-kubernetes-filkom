BOX_IMAGE = "ubuntu/bionic64"
require 'yaml'
NODES=0
settings = YAML.load_file('cluster.yml')
Vagrant.configure("2") do |config|
  settings["nodes"].each do |instance|
    config.vm.define "#{instance["hostname"]}" do |machine|
    config.ssh.insert_key = false
    config.vm.boot_timeout = 800
    config.ssh.private_key_path = ["~/.ssh/vagrant_rsa", "~/.vagrant.d/insecure_private_key"]
    config.vm.provision "file", source: "~/.ssh/vagrant_rsa.pub", destination: "~/.ssh/authorized_keys"
    NODES=NODES+1
    machine.vm.box = BOX_IMAGE
    machine.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.cpus = instance["cpu"]
      vb.memory = instance["memory"]
      vb.name = "#{instance["hostname"]}"
    end 
    machine.vm.network "private_network",ip: instance["address"]
    config.vm.provision "shell", inline: "swapoff -a"
    if settings["nodes"].length == NODES
      machine.vm.provision :ansible do |ansible|
        ansible.limit = "all"
        ansible.playbook = "master.yml"
        ansible.tags = "setup"
      end
end
end
end
end