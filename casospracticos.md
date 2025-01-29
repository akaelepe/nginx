<h1 align="center"> CASOS PRÁCTICOS </h1>  
<BR>
<BR>

## ENUNCIADO  
Acabamos de terminar el CFGS ASIR y encuentramos trabajo en la empresa Servicios Web RC, SA en Huelva. Anteriormente utilzaban Apache como servidor web y quiere migrar a Nginx. Una vez instalado y configurado procedemos a realizar todos los casos prácticos solicitados.  
<br>
<br>

### A) VERSIÓN DE NGINX INSTALADO  
Para ver la versión de Nginx hay que ejecutar en un terminal *__nginx -v__*  
<br>

![nginx -v](./img/nginx-v.png)  

<br>
<br>

### B) SERVICIO ASOCIADO  
Para ver que Nginx está configurado correctamente y en ejecución se utiliza *__systemctl status nginx__*  
<br>

![nginx status](./img/nginx_status.png)  
<br>
> [!NOTE]
> Otros comandos para gestionar el servicio son:
> - systemctl start nginx
> - systemctl stop nginx
> - systemctl reload nginx
> - systemctl restart nginx
<br>
<br>

### C) INSPECCIONAR LOS FICHEROS DE CONFIGURACIÓN  
El directorio de Nginx está situado en *__/etc/nginx__*  
<br>

![ls /etc/nginx](./img/ls-nginx.png)  
<br>
Su archivo de configuración es el *__nginx.conf__*  
<br>

![nfinx conf](./img/nginx-conf.png)  
<br>

### D) MODIFICACIÓN DE LA PÁGINA WEB  
Para modificar la página predeterminada de Nginx hay que modificar el archivo *__/var/www/html/index.nginx-debian.html__*
<br>

![página predeterminada nginx](./img/index-nginx.png)  
<br>

### E) VIRTUAL HOSTING  
El servidor poseerá dos sitios webs. Para ello hay que seguir los siguientes pasos:
<br>

*__Creación de los directorios__*
<br>

![mkdir de los directorios](./img/mkdir-web.png)
<br>

*__Concesión de permisos para los directorios__*  
![permisos a los directorios](./img/permisos-directorios.png)  
<br>

*__Creación de los index.html para sitio web__*
<br>

![index.html de las dos webs](./img/index-webs.png)  
<br>

*__Creación de los sites-available para cada sitio__*
<br>

![sites available](./img/sites-available.png)  
<br>

*__Configuración del archivo hosts para las webs__*
<br>

![archivo hosts](./img/hosts.png)  
<br>

*__Resultado final__*  
<br>

![resultado final](./img/resultado_final.png)  
<br>

### F) AUTENTICACIÓN, AUTORIZACIÓN Y CONTROL DE ACCESO  
La web1 puede acceder desde la red externa y la red interna, pero la web2 solo desde la interal. Para conseguir esto necesitamos hacer:  
<br>
*__Modificar los sites-available de cada uno__*  
<br>

![sites available 2](./img/sites-available2.png)  
<br>

*__Modificar el archivo hosts con las ips que permitimos tanto para red externa como interna__*  
<br>

![hosts modificado](./img/hosts2.png)  
<br>

*__Comprobacion de la red interna usando curl__*  
<br>

![comprobacion interna](./img/comprobacion-interna.png)  
<br>

*__Comprobación de la red externa__*  
<br>

![comprobación red externa](./img/comprobacion-externa.png)  
<br>

### G) AUTENTICACIÓN, AUTORIZACIÓN Y CONTROL DE ACCESO  
<br>
Web1.org contiene un directorio privado al que sólo pueden acceder usuarios válidos.  
<br>

*__Volver a modificar el sites available__*  
<br>

![sites available 3](./img/sites-available3.png)  
<br>

*__Comprobación de que web1.org/privado requiere acceso__*  
<br>

![web1 privado](./img/web1-privado.png)  
<br>

*__Comprobación de que tengo acceso__*  
<br>

![acceso privado](./img/acceso-privado.png)  
<br>  

### H) AUTENTICACIÓN, AUTORIZACIÓN Y CONTROL DE ACCESO  

La web1 contiene un directorio llamado privado. Desde la red externa pide autorización y desde la red interna NO.  

*__Volver a modificar el sites-available__*  
<br>

![sites available 4](./img/sites-available4.png)  
<br>


### I) SEGURIDAD  
<br>
Configurar el sitio de web1 para que el acceso sea seguro. Para ello hay que crear una key privada:  

<br>

> openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/selfigned.key -out /etc/ssl/certs/selfsigned.crt
<br>

![key privada](./img/key-private.png)  
<br>

*__Por último volver a modificar el archivo sites-available__*  
<br>

![sites available final](./img/key-sitesavailable.png)  
<br>


