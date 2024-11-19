# servidorWebNginx

## Configuración para configurar el servidor web con Nginx y mostrar la pagina de prueba del repositorio que hemos clonado

### Añadimos vagrant con vagrant init y hacemos la configuración inicial de la máquina con la instalación e inicio de nginx
![alt text](images/image.png)

### añadimos esta configuración en el archivo .gitignore para que toda la configuración de vagrant no  se suba a github
![alt text](images/image1.png)

###  Añadimos los comandos necesarios para crear la carpeta donde se va a situar el sitio web, accedemos a él, clonamos el sitio de prueba, le damos los permisos necesarios y le cambiamos el propietario a www-data
![alt text](images/image2.png)



### Configuramos el servidor web nginx

1. Primero añadimos una linea en el archivo vagrantfile para eliminar el directorio static-website-example para evitar conflictos al ejecutar vagrant provision
![alt text](images/image4.png)

2. Creamos un archivo llamado webAntonio en vagrant con la configuración del servidor nginx
![alt text](images/image5.png)

3. Copiamos el archivo webAntonio de vagrant al directorio /etc/nginx/sites-available/webAntonio, creamos un enlace simbólico en sites-enabled, comprobamos y reiniciamos el servicio de nginx
![alt text](images/image6.png)

4. Archivo vagrantfile completo
![alt text](images/image3.png)

5. Comprobamos que funciona correctamente poniendo en el navegador la url http://webAntonio
añadimos al archivo etc/hosts la direccion ip y el nombre del servidor
![alt text](images/image7.png)

Página web de ejemplo
![alt text](images/image8.png)

## Configuración Para configurar el servidor web con Nginx y mostrar nuestra pagina
