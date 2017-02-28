# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  #config.ssh.username = "erik"
  #config.ssh.password = "123456"

  #config.vm.provider :virtualbox do |vb|
  #  vb.customize ["modifyvm", :id, "--memory", "512"]
  #end

  config.vm.define :server1 do |a_config|
    a_config.vm.network "forwarded_port", guest: 80, host: 8080
    a_config.vm.network "private_network", ip: "192.168.33.10"
    a_config.vm.synced_folder "./www", "/var/www/html"

    a_config.vm.provision "shell", path: "vagrant_config/server1.sh"
    a_config.vm.provision "shell", inline: "echo \"PROVISIONAMENTO TERMINADO, ERIK\""
  end

  config.vm.define :server2 do |b_config|
    b_config.vm.network "forwarded_port", guest: 80, host: 8081
    b_config.vm.network "private_network", ip: "192.168.33.11"
    b_config.vm.synced_folder "./www2", "/var/www/html"

    b_config.vm.provision "shell", path: "vagrant_config/server2.sh"
  end

  config.vm.define :server3 do |c_config|
    c_config.vm.network "forwarded_port", guest: 80, host: 8082
    c_config.vm.network "private_network", ip: "192.168.33.12"
    c_config.vm.synced_folder "./www2", "/var/www/html"

    c_config.vm.provision "shell", inline: <<-SHELL
      echo "SERVIDOR SEM PROVISIONAMENTO"
    SHELL
  end

end
