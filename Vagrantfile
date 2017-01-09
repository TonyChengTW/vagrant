Vagrant.configure("2") do |config|
  config.vm.provider :libvirt do |libvirt|
    libvirt.host = '127.0.0.1'
    libvirt.driver = "kvm"
    libvirt.username = 'jenkins'
    libvirt.connect_via_ssh = true
    libvirt.storage_pool_name = "default"
  end
  config.vm.define :ubuntu1 do |machine|
    machine.vm.box = "trusty64"
    #machine.vm.network :public_network, ip: '192.168.48.193', :dev => "br0", :mode => 'bridge'
    machine.vm.provider :libvirt do |domain|
      domain.memory = 1024
      domain.cpus = 2
    end
    #machine.vm.provision :shell, path: "bootstrap.sh", args: "42", keep_color: true
  end
end
