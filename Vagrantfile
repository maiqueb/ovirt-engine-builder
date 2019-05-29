# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.network "private_network", ip: "192.168.33.33"
  config.vm.hostname = "engine-test"

  config.vm.provider :libvirt do |vm|
    vm.memory = "8192"
    vm.cpus = 2
  end

  config.vm.provision "shell", inline: <<-SHELL
    yum install -y http://resources.ovirt.org/pub/yum-repo/ovirt-release43.rpm epel-release
    yum install -y ovirt-engine python-pip
    systemctl enable --now ovirt-engine
    engine-setup --config=/vagrant/engine-setup-answers.conf
  SHELL
end
