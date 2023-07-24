$NODE_COUNT=1
$public_ssh_key="#{Dir.home}/.ssh/id_rsa.pub"

Vagrant.configure("2") do |config|

    config.vm.provider :virtualbox do |vb|
      vb.memory = 2048
      vb.cpus = 2
      # v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      # v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
      # vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    end

    (0...$NODE_COUNT).each do |c|
        config.vm.define "node#{c}" do |node|
           
            node.vm.box = "bento/ubuntu-22.04"
            node.vm.hostname = "node#{c}"
            node.vm.network :private_network, ip: "192.168.56.1#{c}"
    
            # Copy public key to our VM (root, and vagrant are default users)
            node.vm.provision "shell" do |s|
              ssh_pub_key = File.readlines($public_ssh_key).first.strip
              s.inline = <<-SHELL
                  echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys
                  mkdir -p /root/.ssh
                  echo #{ssh_pub_key} >> /root/.ssh/authorized_keys
              SHELL
            end
        end
    end
end
