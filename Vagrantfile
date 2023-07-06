# -*- mode: ruby -*-
# vi: set ft=ruby :
machines = [
    {
        :name => "instance01",
        :eth1 => "192.168.101.180",
        :mem => "2048",
        :cpu => "2"
    },
    {
        :name => "instance02",
        :eth1 => "192.168.101.200",
        :mem => "2048",
        :cpu => "2"
    },
    {
        :name => "mysql",
        :eth1 => "192.168.101.150",
        :mem => "2048",
        :cpu => "2"
    }
]

Vagrant.configure(2) do |config|

  config.vm.box = "generic/ubuntu1804"

  machines.each do |opts|
    config.vm.define opts[:name] do |config|
      config.vm.hostname = opts[:name]

      config.vm.provider "virtualbox" do |v|
        v.name = opts[:name]
        v.memory = opts[:mem]
        v.cpus = opts[:cpu]
      end

      config.vm.network :public_network, bridge: "en0: Ethernet", ip: opts[:eth1]

      config.ssh.username = "vagrant"
      config.ssh.password = "vagrant"
      config.ssh.insert_key = false
    end
  end
end

