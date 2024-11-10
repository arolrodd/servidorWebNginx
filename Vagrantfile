Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"

  config.vm.define "vb" do |vb|

    vb.vm.network "private_network", ip: "192.168.57.14"

    vb.vm.provision "shell", inline: <<-SHELL
      # Actualizamos el sistema e instalamos Nginx
      apt-get update
      apt-get install -y nginx
      sudo systemctl start nginx

      # Eliminamos el directorio si ya existia para evitar conflictos
      sudo rm -rf /var/www/webAntonio/html/static-website-example

      # Creamos la carpeta donde se va a encontrar el sitio web
      sudo mkdir -p /var/www/webAntonio/html

      # Clonamos el repositorio
      cd /var/www/webAntonio/html
      sudo git clone https://github.com/cloudacademy/static-website-example

      # Cambiamos permisos y propietario del sitio web
      sudo chown -R www-data:www-data /var/www/webAntonio/html/static-website-example
      sudo chmod -R 755 /var/www/webAntonio/html

      # Movemos el archivo de configuración para el sitio en sites-available
      cp /vagrant/webAntonio /etc/nginx/sites-available/webAntonio

      # Creamos un enlace simbólico en sites-enabled
      sudo ln -sf /etc/nginx/sites-available/webAntonio /etc/nginx/sites-enabled/

      # Verificamos la configuración de Nginx y reiniciamos el servicio
      sudo nginx -t
      sudo systemctl restart nginx
    SHELL
  end
end
