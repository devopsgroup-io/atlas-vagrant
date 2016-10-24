# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # windows
  config.vm.define "windows_server-2012r2-standard-amd64-nocm" do |config|
    # source => https://atlas.hashicorp.com/opentable/boxes/win-2012r2-standard-amd64-nocm
    config.vm.box = "devopsgroup-io/windows_server-2012r2-standard-amd64-nocm"
    config.vm.provider :virtualbox do |provider|
      provider.memory = 512
      provider.cpus = 1
    end
    config.vm.guest = :windows
    config.vm.boot_timeout = 60 * 7
    config.vm.communicator = "winrm"
  end

end
