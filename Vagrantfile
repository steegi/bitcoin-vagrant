# -*- mode: ruby -*-
# vi: set syntax=ruby

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "hashicorp/precise64"
  config.vm.provision :shell, :path => "bootstrap.sh", privileged: false

  # NFS synced_folder
  # Fix for "Error opening block database."
  # http://qiita.com/hshimo/items/3ca8444c33f339de66d2
  config.vm.network :private_network, ip: "192.168.33.30"
  config.vm.synced_folder "data/", "/home/vagrant/.bitcoin/", type: "nfs"

  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", "1536"]
  end

  config.vm.provider "vmware" do |vmw|
    vmw.customize ["modifyvm", :id, "--memory", "1536"]
  end
end

