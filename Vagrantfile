# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  
  config.vm.box = "debian/bookworm64"

  config.vm.define "vb" do |vb|
    vb.vm.network "private_network", ip: "192.168.57.14"
    vb.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y nginx
      sudo systemctl start nginx

      #Creamos la carpeta donde se va a encontar el sitio web
      sudo mkdir -p /var/www/webAntonio/html

      #Vamos al directorio donde se encuentra el sitio web para clonar el repositorio
      cd /var/www/webAntonio/html
      sudo git clone https://github.com/cloudacademy/static-website-example

      #Le damos permisos a la carpeta para que no haya nigun problema y le cambiamos el propietario a www-data
      sudo chown -R www-data:www-data /var/www/webAntonio/html
      sudo chmod -R 755 /var/www/webAntonio
    SHELL
  end
end
