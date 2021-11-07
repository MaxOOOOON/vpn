# -*- mode: ruby -*-
# vi: set ft=ruby :
 
MACHINES = {
   :server => {
        :box_name => "centos/8",
        :memory => 512,
        :net => [
                   {ip: '10.20.0.1', adapter: 2, netmask: "255.255.255.0", virtualbox__intnet: "net"},
                ]
  },
  :client => {
        :box_name => "centos/8",
        :memory => 512,
        :net => [
                   {ip: '10.20.0.2', adapter: 2, netmask: "255.255.255.0", virtualbox__intnet: "net"},           
                ]
  },

}
 

Vagrant.configure("2") do |config|

    MACHINES.each do |boxname, boxconfig|

        config.vm.define boxname do |box|

            box.vm.box = boxconfig[:box_name]
            box.vm.host_name = boxname.to_s

            boxconfig[:net].each do |ipconf|
            box.vm.network "private_network", ipconf
            end
            box.vm.provider :virtualbox do |vb|
                    vb.customize ["modifyvm", :id, "--memory", "512"]
            end        

            # case boxname.to_s
            # when "server"
            # box.vm.network "forwarded_port", guest: 1194, host: 1194
            # end
            
            box.vm.provision :ansible do |ansible|
                ansible.playbook = "./playbook.yml"
                # ansible.verbose = true
              end
            
    end  
end
end