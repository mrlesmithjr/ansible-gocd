# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  config.vm.define "gocd" do |gocd|
    gocd.vm.box = "mrlesmithjr/trusty64"
    gocd.vm.hostname = "gocd"

    gocd.vm.network :private_network, ip: "192.168.202.201"
    gocd.vm.network "forwarded_port", guest: 8000, host: 8000

    gocd.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end
  end
  config.vm.provision :shell, path: "provision.sh", keep_color: "true"
end
