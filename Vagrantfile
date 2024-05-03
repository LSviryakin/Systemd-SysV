# -*- mode: ruby -*-
# vim: set ft=ruby :
ENV['VAGRANT_SERVER_URL'] = 'https://vagrant.elab.pro'

Vagrant.configure("2") do |config|
    config.vm.define "systemd" do |systemd|
    systemd.vm.box = "centos/7"
	systemd.vm.box_version = "1.0.0"
    systemd.vm.network "private_network", ip: "192.168.10.22"
    systemd.vm.hostname = "systemd"
    systemd.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "1024"]
      vb.customize ["modifyvm", :id, "--cpus", "1"]
end
    systemd.vm.provision "shell", inline: <<-SHELL
       mkdir -p ~root/.ssh; cp ~vagrant/.ssh/auth* ~root/.ssh
       sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config
       yum install epel-release -y
       yum check-update
    SHELL
end
end