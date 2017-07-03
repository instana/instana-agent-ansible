#fa -*- mode: ruby -*-
# vi: set ft=ruby :

@OSes = %w(centos6 centos7 jessie rhel6 rhel7)
@OSes << 'trusty'
@OSes << 'xenial'
Vagrant.configure("2") do |config|
  @OSes.each_with_index do |os,idx|
    config.vm.define os do |machine|
      machine.vm.hostname = os
      machine.vm.box = os
      machine.vm.network :private_network,
        ip: "192.168.69.#{idx+4}",
        gateway: "192.168.69.1"
      machine.vm.provider :vmware_workstation do |vm|
        vm.vmx["numvcpus"] = 2
        vm.vmx["memsize"] = (6 * 1024)
      end
    end
  end
end
