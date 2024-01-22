1. ## Creamos y preparamos una nueva MV

   Con esta MV balancearemos la carga entre ambos servidores.

```
sudo apt update
sudo apt install nginx
 ```

3. ## Configuración del servidor primario.

   * Modificación fichero /etc/nginx/nginx.conf

     Hay que tener cuidado con los {}

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
``
