Vagrant.configure("2") do |config|
    # Configuración para la primera máquina virtual
    config.vm.define "web1" do |web1|
      web1.vm.box = "bento/ubuntu-20.04"
      web1.vm.network "private_network", ip: "192.168.56.101"
      web1.vm.provider "virtualbox" do |vb|
        vb.memory = "512"
      end
      web1.vm.provision "shell", inline: <<-SHELL
        apt-get update
        apt-get install -y apache2
        if ! [ -L /var/www/html ]; then
          rm -rf /var/www/html
          ln -fs /vagrant/html /var/www/html
        fi
      SHELL
    end
  
    # Configuración para la segunda máquina virtual
    config.vm.define "web2" do |web2|
      web2.vm.box = "bento/ubuntu-20.04"
      web2.vm.network "private_network", ip: "192.168.56.102"
      web2.vm.provider "virtualbox" do |vb|
        vb.memory = "512"
      end
      web2.vm.provision "shell", inline: <<-SHELL
        apt-get update
        apt-get install -y apache2
        if ! [ -L /var/www/html ]; then
          rm -rf /var/www/html
          ln -fs /vagrant/html /var/www/html
        fi
      SHELL
    end
  
    # Carpeta compartida para los archivos HTML
    config.vm.synced_folder ".", "/vagrant", type: "virtualbox"
  end
  