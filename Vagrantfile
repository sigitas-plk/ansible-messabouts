$NODE_COUNT=2
$public_ssh_key="#{Dir.home}/.ssh/id_rsa.pub"

Vagrant.configure("2") do |config|

    config.vm.provider :virtualbox do |vb|
      vb.memory = 2048
      vb.cpus = 2
    end

    # config.ssh.username = 'root'
    # config.ssh.password = 'vagrant'
    # config.ssh.insert_key = 'true'

    (0...$NODE_COUNT).each do |c|
      
      node_name = "node#{c}"
      if (c == 0) 
        node_name = "cpn"
      end 

        config.vm.define node_name do |node|
           
            node.vm.box = "bento/ubuntu-22.04"
            node.vm.hostname = node_name
            node.vm.network :private_network, ip: "192.168.56.1#{c}"
    
            # Copy public key to our VM (root, and vagrant are default users)
            node.vm.provision "shell" do |s|
              ssh_pub_key = File.readlines($public_ssh_key).first.strip
              s.inline = <<-SHELL
                  echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys
                  mkdir -p /root/.ssh
                  echo #{ssh_pub_key} >> /root/.ssh/authorized_keys
                  sed -ie "/#{node_name}/d" /etc/hosts
                  echo "192.168.56.1#{c} #{node_name}" >> /etc/hosts
              SHELL
            end
        end
    end
end
