Vagrant.configure("2") do |config|
  config.vm.provision "shell", path: "script.sh"

	config.vm.define "controle" do |controle|
        	controle.vm.box = "shekeriev/debian-11"
	        controle.vm.hostname = "controle"
	        controle.vm.network "private_network", ip:"172.17.177.100"
	        controle.vm.provider "virtualbox" do |vb|
        	        vb.name = "controle"
	                vb.memory = "11124"
	                vb.cpus = 12
        	end          
          #controle.vm.provision "shell", inline:"apt -y install git"
          controle.vm.provision "ansible_local" do |ansible|
            ansible.playbook = "playbook.yml"
            ansible.install_mode = "pip"
          end
	end

  config.vm.define "web" do |web|
    web.vm.box = "shekeriev/debian-11"
    web.vm.hostname = "web"
    web.vm.network "private_network", ip:"172.17.177.101"
    web.vm.provider "virtualbox" do |vb|
            vb.name = "web"
            vb.memory = "11124"
            vb.cpus = 12
    end
  end

  config.vm.define "db" do |db|
    db.vm.box = "shekeriev/debian-11"
    db.vm.hostname = "controle"
    db.vm.network "private_network", ip:"172.17.177.102"
    db.vm.provider "virtualbox" do |vb|
            vb.name = "db"
            vb.memory = "11124"
            vb.cpus = 12
    end
  end
end