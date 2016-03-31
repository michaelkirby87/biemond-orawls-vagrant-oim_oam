# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "igdadmin" , primary: true do |igdadmin|

    igdadmin.vm.box = "OEL6_6-x86_64"
    igdadmin.vm.box_url = "https://dl.dropboxusercontent.com/s/i247jykp2obw3ln/OEL6_6-x86_64.box"

    igdadmin.vm.provider :vmware_fusion do |v, override|
      override.vm.box = "OEL-6.6-x86_64-vmware"
      override.vm.box_url = "https://dl.dropboxusercontent.com/s/96qaaklh1ya6qnd/OEL6_6-x86_64-vmware.box"
    end

    igdadmin.vm.hostname = "igdadmin.example.com"

    igdadmin.vm.synced_folder ".", "/vagrant", :mount_options => ["dmode=777","fmode=777"]
    # igdadmin.vm.synced_folder "/Users/edwin/software", "/software", :mount_options => ["dmode=777","fmode=777"]


    igdadmin.vm.network :private_network, ip: "10.10.10.70"

    igdadmin.vm.provider :vmware_fusion do |vb|
      vb.vmx["numvcpus"] = "2"
      vb.vmx["memsize"] = "5548"
    end

    igdadmin.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "5548"]
      vb.customize ["modifyvm", :id, "--name"  , "igdadmin"]
      vb.customize ["modifyvm", :id, "--cpus"  , 2]
    end

    igdadmin.vm.provision :shell, :inline => "ln -sf /vagrant/puppet/hiera.yaml /etc/puppet/hiera.yaml;rm -rf /etc/puppet/modules;ln -sf /vagrant/puppet/modules /etc/puppet/modules"

    igdadmin.vm.provision :puppet do |puppet|
      puppet.manifests_path    = "puppet/manifests"
      puppet.module_path       = "puppet/modules"
      puppet.manifest_file     = "site.pp"
      puppet.options           = "--verbose --hiera_config /vagrant/puppet/hiera.yaml"

      puppet.facter = {
        "environment"    => "development",
        "vm_type"        => "vagrant",
      }

    end

  end

  config.vm.define "oimoud" , primary: true do |oimoud|

    oimoud.vm.box = "OEL6_6-x86_64"
    oimoud.vm.box_url = "https://dl.dropboxusercontent.com/s/i247jykp2obw3ln/OEL6_6-x86_64.box"

    oimoud.vm.provider :vmware_fusion do |v, override|
      override.vm.box = "OEL-6.6-x86_64-vmware"
      override.vm.box_url = "https://dl.dropboxusercontent.com/s/96qaaklh1ya6qnd/OEL6_6-x86_64-vmware.box"
    end

    oimoud.vm.hostname = "oimoud.example.com"
    oimoud.vm.synced_folder ".", "/vagrant", :mount_options => ["dmode=777","fmode=777"]
    # oimoud.vm.synced_folder "/Users/edwin/software", "/software", :mount_options => ["dmode=777","fmode=777"]


    oimoud.vm.network :private_network, ip: "10.10.10.71"

    oimoud.vm.provider :vmware_fusion do |vb|
      vb.vmx["numvcpus"] = "2"
      vb.vmx["memsize"] = "2048"
    end

    oimoud.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
      vb.customize ["modifyvm", :id, "--name"  , "oimoud"]
      vb.customize ["modifyvm", :id, "--cpus"  , 1]
    end

    oimoud.vm.provision :shell, :inline => "ln -sf /vagrant/puppet/hiera.yaml /etc/puppet/hiera.yaml;rm -rf /etc/puppet/modules;ln -sf /vagrant/puppet/modules /etc/puppet/modules"

    oimoud.vm.provision :puppet do |puppet|
      puppet.manifests_path    = "puppet/manifests"
      puppet.module_path       = "puppet/modules"
      puppet.manifest_file     = "site.pp"
      puppet.options           = "--verbose --hiera_config /vagrant/puppet/hiera.yaml"

      puppet.facter = {
        "environment"   => "development",
        "vm_type"       => "vagrant",
      }

    end

  end

  config.vm.define "db" , primary: true do |db|

    db.vm.box = "OEL6_6-x86_64"
    db.vm.box_url = "https://dl.dropboxusercontent.com/s/i247jykp2obw3ln/OEL6_6-x86_64.box"

    db.vm.provider :vmware_fusion do |v, override|
      override.vm.box = "OEL-6.6-x86_64-vmware"
      override.vm.box_url = "https://dl.dropboxusercontent.com/s/96qaaklh1ya6qnd/OEL6_6-x86_64-vmware.box"
    end

    db.vm.hostname = "db.example.com"
    db.vm.synced_folder ".", "/vagrant", :mount_options => ["dmode=777","fmode=777"]
    # db.vm.synced_folder "/Users/edwin/software", "/software", :mount_options => ["dmode=777","fmode=777"]

    db.vm.network :private_network, ip: "10.10.10.20"

    db.vm.provider :vmware_fusion do |vb|
      vb.vmx["numvcpus"] = "2"
      vb.vmx["memsize"] = "2532"
    end

    db.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm"     , :id, "--memory", "2532"]
      vb.customize ["modifyvm"     , :id, "--name"  , "db"]
      vb.customize ["modifyvm"     , :id, "--cpus"  , 2]
    end


    db.vm.provision :shell, :inline => "ln -sf /vagrant/puppet/hiera.yaml /etc/puppet/hiera.yaml;rm -rf /etc/puppet/modules;ln -sf /vagrant/puppet/modules /etc/puppet/modules"

    db.vm.provision :puppet do |puppet|
      puppet.manifests_path    = "puppet/manifests"
      puppet.module_path       = "puppet/modules"
      puppet.manifest_file     = "db.pp"
      puppet.options           = "--verbose --hiera_config /vagrant/puppet/hiera.yaml"

      puppet.facter = {
        "environment" => "development",
        "vm_type"     => "vagrant",
      }

    end

  end

end
