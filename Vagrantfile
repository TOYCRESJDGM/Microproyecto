# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  if Vagrant.has_plugin? "vagrant-vbguest"
    config.vbguest.no_install  = true
    config.vbguest.auto_update = false
    config.vbguest.no_remote   = true
  end

  config.vm.define :server do |haproxy|
    haproxy.vm.box = "bento/ubuntu-20.04"
    haproxy.vm.network :private_network, ip: "192.168.10.4"
    #haproxy.vm.provision "shell", path: "haproxyServerScript.sh"
    haproxy.vm.hostname = "server"
  end

  NODOS=2

  1.upto(NODOS) do |i|
    config.vm.define vm_name = "server#{i}" do |nodo|
    config.vm.box ="bento/ubuntu-20.04"
     nodo.vm.hostname = "server#{i}"
     nodo.vm.network "private_network", ip: "192.168.10.#{1+i}"
     nodo.vm.provider :virtualbox do |vb|
     vb.name = "server#{i}"
     vb.memory = 2048
     vb.cpus = 1
     end
     #nodo.vm.provision "shell", path: "haproxyClientScript.sh", args: "#{i} 192.168.50.#{1+i}"
    end
  end
  
end