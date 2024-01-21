# Introducción

Nginx es un servidor web de alto rendimiento diseñado para servir aplicaciones escalables de alto rendimiento de manera eficiente y receptiva. Se puede utilizar para servir contenido estático, equilibrar la carga de solicitudes HTTP, proxy inverso FCGI/PSGI/USWGI y conexiones TCP arbitrarias. Dado esto, es importante poder configurar e implementar de forma segura las instalaciones de Nginx para proporcionar una interfaz web segura para tu aplicación y minimizar las superficies de ataque. Por lo tanto, puede manejar correctamente altas cargas con muchas conexiones de clientes concurrentes y puede funcionar fácilmente como servidor web, servidor de correo o servidor de proxy inverso.

Este software fue lanzado oficialmente en octubre del 2004. El creador del software, Igor Sysoev, comenzó su proyecto en el 2002 como un intento de solucionar el problema C10k. C10k es el reto de gestionar diez mil conexiones al mismo tiempo.

Hoy en día, los servidores web tienen que manejar un número aún mas grande de conexiones. Por esa razón, NGINX ofrece una arquitectura asíncrona y controlada por eventos, característica que hace de NGINX uno de los servidores más confiables para la velocidad y la escalabilidad.

Ejemplo de arquitectura de alojamiento:

![ejemplo](https://kinsta.com/wp-content/uploads/2018/11/kinsta-hosting-architecture-v8.png)
