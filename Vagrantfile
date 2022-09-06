# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

   # Install vagrant-disksize to allow resizing the vagrant box disk.
   unless Vagrant.has_plugin?("vagrant-disksize")
      raise  Vagrant::Errors::VagrantError.new, "vagrant-disksize plugin is missing. Please install it using 'vagrant plugin install vagrant-disksize' and rerun 'vagrant up'"
   end

   defaultImage = "ubuntu/focal64"

   servers = [
        {
          :hostname => "pc1",
          :box => defaultImage, 
          :ip => "192.168.56.50",
          :ssh_port => '2200'
        },
        {
          :hostname => "pc2",
          :box => defaultImage,
          :ip => "192.168.56.51",
          :ssh_port => '2201'
        },
        {
          :hostname => "pc3",
          :box => defaultImage,
          :ip => "192.168.56.52",
          :ssh_port => '2202'
        },
        {
          :hostname => "pc4",
          :box => defaultImage,
          :ip => "192.168.56.53",
          :ssh_port => '2203'
        }
    ]

    servers.each do |machine|
        config.vm.define machine[:hostname] do |node|
            node.vm.box = machine[:box]
            node.vm.hostname = machine[:hostname]
            node.vm.network :private_network, ip: machine[:ip]
            node.vm.network "forwarded_port", guest: 22, host: machine[:ssh_port], id: "ssh"
            #node.disksize.size = "45GB"

            node.vm.provider :virtualbox do |vb|
                vb.customize ["modifyvm", :id, "--memory", 1024]
                vb.customize ["modifyvm", :id, "--cpus", 1]
            end
            
	          #node.ssh.insert_key = false

            node.vm.provision "ansible" do |ansible|
                ansible.verbose = "v"
                ansible.playbook = "master_playbook.yaml"
            end
        end
    end
end
