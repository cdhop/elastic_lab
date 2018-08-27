Vagrant.configure("2") do |config|

  config.vm.define "elastic" do |elastic|
    elastic.vm.box = "ubuntu/bionic64"

    elastic.vm.provider "virtualbox" do |v|
      v.memory = 2048
      v.cpus = 2  
    end

    elastic.vm.network "forwarded_port", guest: 80, host: 8080
    elastic.vm.network "private_network", ip: "192.168.2.5", netmask: "255.255.255.0"

    elastic.vm.provision "ansible" do |ansible|
      ansible.playbook = "elastic.yml"
    end
  end

  config.vm.define "webserver" do |webserver|
    webserver.vm.box = "ubuntu/bionic64"

    webserver.vm.network "private_network", ip: "192.168.2.10", netmask: "255.255.255.0"

    webserver.vm.provision "ansible" do |ansible|
      ansible.playbook = "webserver.yml"
    end
  end
end
