# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

config.ssh.forward_agent = true

  config.vm.define "c7", autostart: false do |c7|
    c7.vm.box = "jdoss/centos-7"
    c7.vm.hostname = "c7"
    c7.vm.synced_folder '.', '/vagrant', disabled: true
    c7.vm.provider "libvirt" do |vm|
      vm.memory = 1024
      vm.cpus = 1
      vm.driver = "kvm"
      vm.nic_model_type = "e1000"
      vm.qemu_use_session = false
    end
  end

  config.vm.define "c8", autostart: false do |c8|
    c8.vm.box = "jdoss/centos-8"
    c8.vm.hostname = "c8"
    c8.vm.synced_folder '.', '/vagrant', disabled: true
    c8.vm.provider "libvirt" do |vm|
      vm.memory = 1024
      vm.cpus = 2
      vm.driver = "kvm"
      vm.nic_model_type = "e1000"
      vm.qemu_use_session = false
    end

    {
      "/home/jdoss/rpmbuild" => "/home/vagrant/rpmbuild",

    }.each do |system_path, vagrant_path|
      c8.vm.synced_folder system_path, vagrant_path,
        type: "nfs",
        nfs: true,
        nfs_version: 3,
        nfs_udp: false,
        mount_options: ['rw', 'tcp', 'fsc' ,'actimeo=2']
    end
  end

  config.vm.define "c8s", autostart: false do |c8s|
    c8s.vm.box = "jdoss/centos-8-stream"
    c8s.vm.hostname = "c8s"
    c8s.vm.synced_folder '.', '/vagrant', disabled: true
    c8s.vm.provider "libvirt" do |vm|
      vm.memory = 1024
      vm.cpus = 1
      vm.driver = "kvm"
      vm.nic_model_type = "e1000"
      vm.qemu_use_session = false
    end
  end

end
