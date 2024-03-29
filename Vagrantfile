# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
# The most common configuration options are documented and commented below.
# For a complete reference, please see the online documentation at
# https://docs.vagrantup.com.

# Every Vagrant development environment requires a box. You can search for
# boxes at https://vagrantcloud.com/search.
# config.vm.box = "ubuntu/trusty64"

# Disable automatic box update checking. If you disable this, then
# boxes will only be checked for updates when the user runs
# `vagrant box outdated`. This is not recommended.
# config.vm.box_check_update = false

# Create a forwarded port mapping which allows access to a specific port
# within the machine from a port on the host machine. In the example below,
# accessing "localhost:8080" will access port 80 on the guest machine.
# NOTE: This will enable public access to the opened port
# config.vm.network "forwarded_port", guest: 80, host: 8080

# Create a forwarded port mapping which allows access to a specific port
# within the machine from a port on the host machine and only allow access
# via 127.0.0.1 to disable public access
# config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

# Create a private network, which allows host-only access to the machine
# using a specific IP.
# config.vm.network "private_network", ip: "192.168.33.10"

# Create a public network, which generally matched to bridged network.
# Bridged networks make the machine appear as another physical device on
# your network.
# config.vm.network "public_network"

# Share an additional folder to the guest VM. The first argument is
# the path on the host to the actual folder. The second argument is
# the path on the guest to mount the folder. And the optional third
# argument is a set of non-required options.
# config.vm.synced_folder "../data", "/vagrant_data"

# Provider-specific configuration so you can fine-tune various
# backing providers for Vagrant. These expose provider-specific options.
# Example for VirtualBox:
#
# config.vm.provider "virtualbox" do |vb|
#   # Display the VirtualBox GUI when booting the machine
#   vb.gui = true
#
#   # Customize the amount of memory on the VM:
#   vb.memory = "1024"
# end
#
# View the documentation for the provider you are using for more
# information on available options.

# Enable provisioning with a shell script. Additional provisioners such as
# Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
# documentation for more information about their specific syntax and use.
# config.vm.provision "shell", inline: <<-SHELL
#   apt-get update
#   apt-get install -y apache2
# SHELL
Vagrant.configure("2") do |config|
    	(1..3).each do |i|
    		config.vm.define "node#{i}" do |node|
        		# 设置虚拟机的Box
        		node.vm.box = "ubuntu/trusty64"
        		# 设置虚拟机的主机名
        		node.vm.hostname="node#{i}"
        		# 设置虚拟机的port forwarding
        		node.vm.network "private_network", ip: "192.168.170.#{i}"
        		# 设置主机与虚拟机的共享目录
        		node.vm.synced_folder "./sharefolders/node#{i}", "/home/vagrant/share"
        		# VirtaulBox相关配置
            		node.vm.provider "virtualbox" do |v|
            			# 设置虚拟机的名称
            			v.name = "node#{i}"
            			# 设置虚拟机的内存大小
            			v.memory = 2048
            			# 设置虚拟机的CPU个数
            			v.cpus = 1
            end
      		# 使用shell脚本进行软件安装和配置
      		# node.vm.provision "shell", inline: <<-SHELL
      		# 安装docker 1.11.0
      		# wget -qO- https://get.docker.com/ | sed 's/docker-engine/docker-engine=1.11.0-0~trusty/' | sh
      		# usermod -aG docker vagrant
      		# SHELL
      	end
  	end
end
