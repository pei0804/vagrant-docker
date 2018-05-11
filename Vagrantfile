# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.network "private_network", ip: "192.168.33.10", id:"http"
  config.ssh.forward_agent = true
  config.vm.synced_folder "./shared", "/vagrant"
  config.vm.provision "shell", inline: <<-SHELL
    sudo yum install git
    sudo yum install -y yum-utils
    sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
    sudo yum makecache fast
    sudo yum install -y docker-ce
    sudo systemctl enable docker-ce
    sudo systemctl start docker-ce
    sudo curl -L https://github.com/docker/compose/releases/download/1.17.1/docker-compose-`uname -s`-`uname -m` > docker-compose
    sudo mv docker-compose /usr/local/bin/docker-compose
    sudo chmod +x /usr/local/bin/docker-compose
    sudo groupadd docker
    sudo gpasswd -a vagrant docker
    sudo systemctl restart docker
    sudo yum install java-1.7.0-openjdk
    sudo yum install java-1.7.0-openjdk-devel
  SHELL

  if Vagrant.has_plugin?("vagrant-vbguest") then
    config.vbguest.auto_update = false
  end
end
