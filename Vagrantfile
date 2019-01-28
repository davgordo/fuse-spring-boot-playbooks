# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

cluster = {
  "100.0.44.101" => { :group => "fuse", :ip => "100.0.44.101", :mem => 1024 },
  "100.0.44.102" => { :group => "fuse", :ip => "100.0.44.102", :mem => 1024 }
}

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  groups = { "all" => [] }
    cluster.each do |(hostname, info)|
      if ! groups.has_key?(info[:group])
        groups[info[:group]] = [ hostname ]
      else
        groups[info[:group]].push(hostname)
      end
      groups["all"].push(hostname)
  end

  cluster.each_with_index do |(hostname, info), index|

    config.vm.define hostname do |cfg|

      cfg.vm.provider :libvirt do |lv, config|
        config.vm.box = "centos/7"
        config.vm.network :private_network, ip: "#{info[:ip]}"
        config.vm.hostname = hostname
        lv.memory = info[:mem]
      end

      # provision nodes with ansible
      if index == cluster.size - 1

        cfg.vm.provision :ansible do |ansible|
          #ansible.verbose = "vvvv"
          ansible.groups = groups
          ansible.limit = "all"
          ansible.playbook = "playbook.yml"
        end # end provision

      end #end if

    end # end config

  end #end cluster

end #end vagrant
