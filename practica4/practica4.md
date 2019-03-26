# PRACTICA 4: ASEGURAR LA GRANJA WEB.
## 2 Sesión.

El objetivo de esta práctica es llevar a cabo la configuración de seguridad de la granja
web. Para ello, llevaremos a cabo las siguientes tareas:

      **Instalar un certificado SSL para configurar el acceso HTTPS a los servidores.**
      **Configurar las reglas del cortafuegos para proteger la granja web.**


**1.Instalar un certificado SSL para configurar el acceso HTTPS a los servidores.**

Para generar un certificado **SSL** autofirmado en *Ubuntu Server* solo debemos activar
el módulo **SSL** de **Apache**, generar los certificados y especificarle la ruta a los
certificados en la configuración. Así pues, como *root* ejecutaremos:

~~~

a2enmod ssl

service apache2 restart

mkdir /etc/apache2/ssl

sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/apache2/ssl/apache.key -out /etc/apache2/ssl/apache.crt

~~~

![img](https://github.com/salva12345678/SWAP/blob/master/practica4/foto_1.png)

Editamos el archivo de configuración del sitio default-ssl:

~~~
sudo nano /etc/apache2/sites-available/default-ssl
~~~

![img](https://github.com/salva12345678/SWAP/blob/master/practica4/foto_2.png)

Activamos el sitio default-ssl y reiniciamos apache:

~~~
a2ensite default-ssl

service apache2 reload
~~~

Tenemos que copiar los archivos **apache.crt** y **apache.key** a la otra *máquina-2* y al *balanceador*.Para ello usaremos rsync.

**Máquina-2:**

![img](https://github.com/salva12345678/SWAP/blob/master/practica4/foto_3.png)

**Máquina-balanceador:**

![img](https://github.com/salva12345678/SWAP/blob/master/practica4/foto_4.png)
