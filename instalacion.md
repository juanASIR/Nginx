## Instalación NGINX
´´´
sudo apt update
sudo apt install nginx
´´´

## Ajustar el firewall

Necesitamos permitir el acceso a nginx previamente. Este se registra de manera automática como un servicio con ***ufw**, para ello necesitamos ver la lista de configuraciones de la aplicación para ver su compatibilidad.

´´´
sudo ufw app list
sudo ufw allow 'Nginx HTTP'
sudo ufw delete allow 'Nginx Full'
sudo ufw delete allow 'Nginx HTTPS'
sudo ufw status
´´´

En nuestro caso, habilitaremos el perfil mas restrictivo, solo necesitamos el tráfico en el puerto 80.

* Nginx HTTP: Abre unicamente el puerto 80 (Tráfico no cifrado)
* Nginx Full: Abre puerto 80 y el 443 (Tráfico TLS/SSL cifrado)
* Nginx HTTPS: Abre unicamente el puerto 443.



