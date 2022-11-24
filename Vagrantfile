# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "staryjie/dockerincentos7"
  config.vm.define "docker"
  config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
  config.vm.synced_folder "./", "/vagrant"
  config.vm.provider "virtualbox" do |vb, override|
    vb.memory = 2048
    vb.name = "centos7-docker" 
  end
  config.vm.provision "docker" do |d|
    d.build_image "/vagrant", args: "-f /vagrant/docker/Dockerfile -t hello_spa"
    d.run "hello_spa", image: "hello_spa", args: "-p 80:80"
  end
end
