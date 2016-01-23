# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  config.vm.define "gocd-server" do |gocd-server|
    gocd-server.vm.box = "mrlesmithjr/trusty64"
    gocd-server.vm.hostname = "gocd-server"

    gocd-server.vm.network :private_network, ip: "192.168.202.201"
    gocd-server.vm.network "forwarded_port", guest: 8153, host: 8153

    gocd-server.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end
    gocd-server.vm.provision :shell, inline: 'ansible-galaxy install -r /vagrant/requirements.yml -f'
    gocd-server.vm.provision :shell, inline: 'ansible-playbook -i /vagrant/hosts -c local /vagrant/playbook.yml --limit "gocd-server"'
  end
  config.vm.define "gocd-agent" do |gocd-agent|
    gocd-agent.vm.box = "mrlesmithjr/trusty64"
    gocd-agent.vm.hostname = "gocd"

    gocd-agent.vm.network :private_network, ip: "192.168.202.202"

    gocd-agent.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end
    gocd-agent.vm.provision :shell, inline: 'ansible-galaxy install -r /vagrant/requirements.yml -f'
    gocd-agent.vm.provision :shell, inline: 'ansible-playbook -i /vagrant/hosts -c local /vagrant/playbook.yml --limit "gocd-agent"'
  end
  config.vm.provision :shell, path: "provision.sh", keep_color: "true"
end
