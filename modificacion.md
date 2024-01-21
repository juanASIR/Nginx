Vemos, como al instalar NGINX este nos crea una página web por defecto.

Para cambiar esto tenemos que modificar los siguientes ficheros:

1. Creación de carpeta en /srv/www
   
```
:/srv/www$ mkdir nueva_pagina

```

2. Desactivar web por defecto de la carpeta donde se habilitan las páginas web, sites-enabled

```
/etc/nginx/sites-enabled$ ls
default

/etc/nginx/sites-enabled$ rm default
```

3. Copiamos la web por defecto en la carpeta donde se muestan disponibles, sites-available.

```
/etc/nginx/sites-available$ cp default nueva_pagina
```





   

