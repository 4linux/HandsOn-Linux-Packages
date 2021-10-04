# -*- mode: ruby -*-
# vi: set ft=ruby :

vms = { 
  'debian-handson' => {'memory' => '512', 'cpus' => '1', 'ip' => '10', 'box' => 'debian/buster64', 'provision' => 'debian.sh'}, 
  'centos-handson' => {'memory' => '752', 'cpus' => '1', 'ip' => '11', 'box' => 'centos/8', 'provision' => 'centos.sh'} 
}


Vagrant.configure('2') do |config|
  vms.each do |name, conf|
     config.vm.define "#{name}" do |my|
       my.vm.box = conf['box']
       my.vm.hostname = "#{name}.example.com"
       my.vm.network 'private_network', ip: "192.168.1.#{conf['ip']}"
       my.vm.provision 'shell', path: "Provision/#{conf['provision']}"
       my.vm.provider 'virtualbox' do |vb|
          vb.memory = conf['memory']
          vb.cpus = conf['cpus']
       end
     end
  end
end

