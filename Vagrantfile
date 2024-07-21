# -*- mode: ruby -*-
# vi: set ft=ruby :
machines = [
    {
        :name => "instance01",
        :eth1 => "192.168.100.100",
        :mem => "2048",
        :cpu => "2"
    },
    {
        :name => "instance02",
        :eth1 => "192.168.100.200",
        :mem => "2048",
        :cpu => "2"
    },
    {
        :name => "mysql",
        :eth1 => "192.168.100.150",
        :mem => "2048",
        :cpu => "2"
    }
]

Vagrant.configure(2) do |config|

  config.vm.box = "generic/ubuntu1804"

  machines.each do |opts|
    config.vm.define opts[:name] do |config|
      config.vm.hostname = opts[:name]

      # config.vm.synced_folder "jgroups/", "/jgroups", owner: "vagrant"

      config.vm.provider "virtualbox" do |v|
        v.customize ["modifyvm", :id, "--name", opts[:name]]
        v.customize ["modifyvm", :id, "--memory", opts[:mem]]
        v.customize ["modifyvm", :id, "--cpus", opts[:cpu]]
      end

      config.vm.network :private_network, ip: opts[:eth1]
    end
  end
end