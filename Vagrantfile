# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  boxes = [
           { :name => :nimbus, :ip => '192.168.33.100', :cpus => 2, :memory => 512 },
           { :name => :supervisor1, :ip => '192.168.33.101', :cpus => 4, :memory => 1024 },
           { :name => :supervisor2, :ip => '192.168.33.102', :cpus => 4, :memory => 1024 },
           { :name => :zookeeper1, :ip => '192.168.33.201', :cpus => 1, :memory => 512 }
          ]

  boxes.each do |opts|
    config.vm.define opts[:name] do |config|
      config.vm.box = "precise32"
      config.vm.hostname = "storm.%s" % opts[:name].to_s
      config.vm.network "private_network", ip: opts[:ip]
      config.vm.provider "virtualbox" do |v|
        v.memory = opts[:memory]
        v.cpus = opts[:cpus]
      end
    end
  end
end
