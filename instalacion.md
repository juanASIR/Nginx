## Instalación NGINX

```
sudo apt update
sudo apt install nginx
```

![1](/Imagenes/1.PNG)

## Ajustar el firewall

Necesitamos permitir el acceso a nginx previamente. Este se registra de manera automática como un servicio con ***ufw***, para ello necesitamos ver la lista de configuraciones de la aplicación para ver su compatibilidad.

```
sudo apt install ufw
sudo ufw app list
sudo ufw allow 'Nginx HTTP'
sudo ufw delete allow 'Nginx Full'
sudo ufw delete allow 'Nginx HTTPS'
sudo ufw status
```

![2](/Imagenes/2.PNG)

En nuestro caso, habilitaremos el perfil mas restrictivo, solo necesitamos el tráfico en el puerto 80.

* Nginx HTTP: Abre unicamente el puerto 80 (Tráfico no cifrado)
* Nginx Full: Abre puerto 80 y el 443 (Tráfico TLS/SSL cifrado)
* Nginx HTTPS: Abre unicamente el puerto 443.

![3](/Imagenes/3.PNG)

## Ajustes en NGINX

```
# Estado Nginx
systemctl status nginx

# Iniciar Nginx
sudo systemctl start nginx

# Detener Nginx
sudo systemctl stop nginx

# Reiniciar Nginx
sudo systemctl restart nginx

# Recargar Configuración
sudo systemctl reload nginx

# Verificar Configuración
sudo nginx -t

# Habilitar al Inicio
sudo systemctl enable nginx

# Deshabilitar al Inicio
sudo systemctl disable nginx
```

## Directorios claves

  * Contenido Web:

    ***/var/www/html***: Contiene el contenido web real. Por defecto, presenta la página predeterminada de Nginx. Puedes modificarlo ajustando los archivos de configuración de Nginx.

  * Configuración del Servidor:

    ***/etc/nginx***: Directorio de configuración principal de Nginx, que contiene todos los archivos de configuración.
    ***/etc/nginx/nginx.conf***: Archivo de configuración principal de Nginx. Modifícalo para realizar cambios en la configuración general.
    ***/etc/nginx/sites-available/***: Directorio para guardar bloques de servidor por sitio. La configuración se realiza aquí y se habilita al establecer un vínculo en el directorio sites-enabled.

  * Registros del Servidor:

    ***/etc/nginx/sites-enabled/***: Directorio que almacena los bloques de servidor habilitados por sitio. Se crean mediante vínculos con archivos de configuración en sites-available.
    ***/etc/nginx/snippets***: Contiene fragmentos de configuración que pueden incluirse en otras partes de la configuración de Nginx.

  * Registros del Servidor:

    ***/var/log/nginx/access.log***: Registra cada solicitud al servidor web.
    ***/var/log/nginx/error.log***: Almacena errores de Nginx.






