
# PRACTICA 2: CLONAR LA INFORMACIÓN DE UN SITIO WEB
## 2 Sesión.

El objetivo de la práctica son:

1.Aprender a copiar archivos mediante *ssh*

2.Clonar contenido entre máquinas

3.Configurar el *ssh* para acceder a máquinas remotas sin contraseña

4.Establecer tareas en *cron*


**1 Aprender a copiar archivos mediante ssh**

Desde las dos maquinas virtuales que tenemos que pasar un directorio y mediante ssh del equipo que queremos enviar en un tar.gz.

Nosotros enviaremos un directorio desde la maquina1 a la maquina2.Esta podremos reconorcerla por la IP.

Pondremos el siguiente comando:

-->tar czf - ./hola/paquete.txt | ssh 192.168.1.102 'cat > ~/tar.tgz'

![img](https://github.com/salva12345678/SWAP/blob/master/practica1/Foto_1.png)

comandos:
maquina1:

maquina2:
tar -xvf tar.tgz //nos muestra el paquete

primera parte echa.

maquina1



para la clave
en ambas generamos la clave
ssh-keygen -b 4096 -t rsa
