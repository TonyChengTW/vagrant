Vagrant.configure("2") do |config|
  config.vm.provider :libvirt do |libvirt|
    libvirt.host = '127.0.0.1'
    libvirt.driver = "kvm"
    libvirt.username = 'jenkins'
    libvirt.connect_via_ssh = true
    libvirt.storage_pool_name = "default"
    libvirt.nested = true
  end
  # CentOS 7
  config.vm.define :devstack1 do |centos7|
    centos7.vm.box = "centos/7"
    centos7.vm.network :public_network,
                                ip: '192.168.120.3',
                                :netmask => "255.255.252.0",
                                :gateway => "192.168.120.254",
                                :mac => '52:54:00:ed:bf:53',
                                :dev => "br0",
                                :type => 'bridge',
                                :mode => 'bridge'

    centos7.vm.provider :libvirt do |domain|
      domain.memory = 16384
      domain.cpus = 16
      domain.management_network_name = 'vagrant-libvirt-mgmt'
      domain.management_network_address = '172.20.178.0/24'
      domain.management_network_mode = 'nat'
    end
    centos7.vm.provision :shell, run: "always", inline: "yum -y install net-tools"
    centos7.vm.provision :shell, run: "always", inline: "ifup eth1"
    centos7.vm.provision :shell, run: "always", inline: "eval `route -n|awk '{ if ($8 ==\"eth0\" && $2 != \"0.0.0.0\") print \"route del default gw \" $2; }'`"
  end
end
