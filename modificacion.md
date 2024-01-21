Vemos, como al instalar NGINX este nos crea una página web por defecto.

Para cambiar esto tenemos que modificar los siguientes ficheros:

## 1. Creación de carpeta en /var/www y dentro un fichero .html
   
```
mkdir nueva_pagina
chown -R www-data:www-data /var/www/nueva_pagina
sudo nano /var/www/nueva_pagina/index.html

```

![7](/Imagenes/7.PNG)

![8](/Imagenes/8.PNG)


## 2. Desactivar web por defecto de la carpeta donde se habilitan las páginas web, sites-enabled

```
/etc/nginx/sites-enabled$ ls
default

/etc/nginx/sites-enabled$ rm default
```
![6](/Imagenes/6.PNG)

## 3. Copiamos la web por defecto en la carpeta donde se muestan disponibles, sites-available. Y activamos la ruta de nuestro nuevo directorio y su respectivo archivo .html

```
cp /etc/nginx/sites-available/default /etc/nginx/sites-available/nueva_pagina.html

server {
    listen 80;
    listen [::]:80;

    root /var/www/nueva_pagina;
    index index.html;

   server_name www.nueva_pagina.com

    location / {
        try_files $uri $uri/ =404;
    }
}

```

## 4. Creamos un nuevo enlace simbólico en sites-enabled, y reiniciamos nginx.

Al crear un enlace simbólico en sites-enabled que apunta al archivo de configuración de tu sitio en el directorio sites-available, estás efectivamente habilitando esa configuración.


```
ln -s /etc/nginx/sites-available/mi_sitio /etc/nginx/sites-enabled/

sudo systemctl restart nginx
```







   

