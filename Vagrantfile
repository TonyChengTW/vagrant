Vagrant.configure("2") do |config|
  config.vm.provider :libvirt do |libvirt|
    libvirt.host = '127.0.0.1'
    libvirt.driver = "kvm"
    libvirt.username = 'jenkins'
    libvirt.connect_via_ssh = true
    libvirt.storage_pool_name = "default"
    libvirt.nested = true
  end
  # Ubuntu 1
  config.vm.define :ubuntu1 do |ubuntu|
    ubuntu.vm.box = "trusty64"
    #ubuntu.vm.network :public_network, ip: '192.168.48.193', :dev => "br0", :mode => 'bridge'
    ubuntu.vm.provider :libvirt do |domain|
      domain.memory = 1024
      domain.cpus = 2
    end
    #ubuntu.vm.provision :shell, path: "bootstrap.sh", args: "42", keep_color: true
  end
  # PXE
  config.vm.define :pxe1 do |pxe|
    pxe.vm.box = "trusty64"
    #pxe.vm.network :public_network, ip: '192.168.48.193', :dev => "br0", :mode => 'bridge'
    pxe.vm.provider :libvirt do |domain|
      domain.memory = 1024
      domain.cpus = 4
      domain.boot 'network'
      domain.boot 'hd'
    end
    #pxe.vm.provision :shell, path: "bootstrap.sh", args: "42", keep_color: true
  end
end
