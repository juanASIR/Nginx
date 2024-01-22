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

  * Registros .log:

    ***/var/log/nginx/access.log***: Registra cada solicitud al servidor web.
    ***/var/log/nginx/error.log***: Almacena errores de Nginx.
