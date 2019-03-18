
# PRACTICA 2: CLONAR LA INFORMACIÓN DE UN SITIO WEB
## 2 Sesión.

El objetivo de la práctica son:

1.Aprender a copiar archivos mediante *ssh*

2.Clonar contenido entre máquinas

3.Configurar el *ssh* para acceder a máquinas remotas sin contraseña

4.Establecer tareas en *cron*


**1 Aprender a copiar archivos mediante ssh**

Desde las dos maquinas virtuales que tenemos que pasar un directorio y mediante ssh del equipo que queremos enviar en un tar.gz.

Nosotros enviaremos un directorio desde la *maquina-1* a la *maquina-2*.Esta podremos reconorcerla por la IP.

Pondremos el siguiente comando:

-->tar czf - ./hola/paquete.txt | ssh 192.168.1.102 'cat > ~/tar.tgz'

![img](https://github.com/salva12345678/SWAP/blob/master/practica2/foto_1.png)

Desde la *maquina-2* ejecutamos el comando para descomprimirlo:

-->tar -xvf tar.tgz

![img](https://github.com/salva12345678/SWAP/blob/master/practica2/foto_2.png)

Observamos que el paquete.txt lo tenemos.

Sin embargo, esto que puede ser útil en un momento dado, no nos servirá para sincronizar grandes cantidades de información. En ese caso, va mejor la herramienta **rsync**.

**2.Clonar contenido entre máquinas**

Para clonar el contenido haremos uso de la herramienta **rsync**.Lo primero que debemos hacer es llevar a cabo su instalación:

-->sudo apt-get install rsync
~~~
hola
~~~

Lo primero que tenemos que hacer es darle permiso al directorio donde vamos a clonar la información y en el directorio donde vamos a tenerlo.Además vamos a crear algunos ficheros para que podamos clonarlos.

![img](https://github.com/salva12345678/SWAP/blob/master/practica2/foto_3.png)

Ahora ya podemos clonar la información escribiendo el siguiente comando:
-->rsync -avz -e ssh 192.168.1.100:/var/www/ /var/www/

![img](https://github.com/salva12345678/SWAP/blob/master/practica2/foto_4.png)

Ahora miramos desde la *máquina-2* para comprobar que están los ficheros con el siguiente comando:

-->ls /var/www


para la clave
en ambas generamos la clave
ssh-keygen -b 4096 -t rsa
