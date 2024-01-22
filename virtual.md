## 1. Creamos y preparamos dos nuevas MV

   Con esta MV balancearemos la carga entre ambos servidores. Solo instalaremos nginx y modificaremos el fichero que viene en /var/www/html (En las dos nuevas MV) , para mostrar ese balanceo de carga.

```
sudo apt update
sudo apt install nginx
nano /var/www/html/index.nginx-debian.html
 ```

![10](/Imagenes/10.PNG)

## 2. Configuración del servidor primario, y reinicio nginx

   * Modificación fichero /etc/nginx/nginx.conf

     Hay que tener cuidado con los {}, y poner en server secundario las ip de las dos MV.

     **IMPORTANTE !** En el server_name pondremos el dominio que nos bajaremos de la web no_ip. Al crear este nuevo dominio, se nos pide una ip, esta será la ip del servidor primario. Sin este dominio no podremos hacer dicho balanceo de carga.

```
     http {
    upstream backend {
        server secundario1_ip;
        server secundario2_ip;
        # Agrega más servidores según sea necesario
    }

    server {
        listen 80;
        server_name tunombre.com www.tunombre.com;

        location / {
            proxy_pass http://backend;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
        }
    }
}

systemctl restart nginx
```

## 3. Comprobación

En el navegador pondremos el nuevo nombre del dominio, y refrescaremos muchas veces (Sobrecarga de tráfico), y en algún momento nos saldrá la web del servidor secundario.

