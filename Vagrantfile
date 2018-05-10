# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # 我々は皆CentOS7でできている
  config.vm.box = "centos/7"

  # 君の好きなポートを追加
  config.vm.network "forwarded_port", guest: 80, host: 80

  # 君の好きなフォルダをSync
  config.vm.synced_folder "./", "/var/www/html"

  # 人生で一番面倒な作業
  config.vm.provision "shell", inline: <<-SHELL
    sudo yum install -y yum-utils
    sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
    sudo yum makecache fast
    sudo yum install -y docker-ce
    sudo systemctl enable docker-ce
    sudo systemctl start docker-ce
    sudo curl -L https://github.com/docker/compose/releases/download/1.17.1/docker-compose-`uname -s`-`uname -m` > docker-compose
    sudo mv docker-compose /usr/local/bin/docker-compose
    sudo chmod +x /usr/local/bin/docker-compose
    sudo gpasswd -a vagrant docker
    sudo systemctl restart docker
  SHELL

  if Vagrant.has_plugin?("vagrant-vbguest") then
    config.vbguest.auto_update = false
  end
end
