# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.hostname = "fusordev.example.com"
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
  config.hostmanager.ignore_private_ip = false
  config.hostmanager.include_offline = true

  config.vm.box = "fusor_centos_7.0_20150310.box"
  config.vm.box_url = "https://s3.amazonaws.com/fusor-vagrant/fusor_centos_7.0_20150310.box"

  config.vm.provision :shell, :path => "setup.sh"
  #config.vm.synced_folder ".", "/vagrant", type: "nfs"
  
  config.vm.network :private_network,
    :ip => "192.168.180.10",
    :libvirt__netmask => "255.255.255.0",
    :libvirt__network_name => "fusor_devel_net",
    :libvirt__dhcp_enabled => false

  config.vm.provider :libvirt do |libvirt|
    libvirt.driver = "kvm"
    libvirt.memory = 8192
    libvirt.cpus = 2
  end
end
