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


## 2. Modificamos el default de /etc/nginx/sites-available, asignandole los siguientes parámetros.

Simplemente modificamos el archivo default (Esto no es tan seguro, pues ese archivo es mejor no tocarlo, pero en este caso vamos a hacerlo asi) y ponemos los datos con la nueva pagina creada. Asignamos la nueva ruta, y ponemos en server_name el *dominio obtenido de la web [no_ip](https://www.noip.com/es-MX)* . En esta plataforma de obtención de dominios, crearemos uno, con la ip de de la MV que tenga el servidor primario.

```
server {
    listen 80;
    listen [::]:80;

    root /var/www/nueva_pagina;
    index index.html;

   server_name Dominio de no_ip

    location / {
        try_files $uri $uri/ =404;
    }
}

```

![9](/Imagenes/9.png)

## 3. EXTRA! Creamos un nuevo enlace simbólico en sites-enabled, y reiniciamos nginx.

Al crear un enlace simbólico en sites-enabled que apunta al archivo de configuración de tu sitio en el directorio sites-available, estás efectivamente habilitando esa configuración.

Esto serviría si quiero poner una nueva página web, para que haga como espejo. En este caso, como hemos tocado solamente el default, y este por defecto vienen en ambos sites no haría falta.


```
ln -s /etc/nginx/sites-available/mi_sitio /etc/nginx/sites-enabled/

sudo systemctl restart nginx
```







   

