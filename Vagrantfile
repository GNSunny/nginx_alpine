Vagrant.configure("2") do |config|
    config.vm.define "sukesh" do |sukesh|
      sukesh.vm.box = "centos/7"
      sukesh.vm.hostname = "sukesh"
      sukesh.vm.network :private_network, ip: "192.168.33.11"
    
      # saying vagrant to run ansible as a privisioner
      sukesh.vm.provision :ansible do |ansible|
        ansible.playbook = "provisioning/playbook.yml"        
      end
    end
    # shared vagrant directory via NFS
    config.vm.synced_folder ".", "/vagrant", type: "nfs"

    # Copy nginx src to Guest Machine
	  config.vm.provision "file", source: "./src", destination: "$HOME/test/src"

    config.vm.provision "shell", inline: <<-SHELL
      sudo yum install ansible -y
    SHELL

    config.vm.provider "virtualbox" do |vb|
        vb.gui = false
        vb.memory = 1024
        vb.cpus = 2


    end
end