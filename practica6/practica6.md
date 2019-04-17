# PRÁCTICA 6.Servidor de disco NFS.
## 1 Sesión.

Los objetivos concretos de esta práctica son:

      **1.Configurar una máquina como servidor de disco NFS y exportar una carpeta a los clientes.**
      **2.Montar en las máquinas cliente la carpeta exportada por el servidor.**
      **3.Comprobar que todas las máquinas pueden acceder a los archivos almacenados en la carpeta compartida.**
      **4.Hacer permanente la configuración en los clientes para que monten automáticamente la carpeta compartida al arrancar el sistema.**


**1.Configurar una máquina como servidor de disco NFS y exportar una carpeta a los clientes.**

En la máquina servidora(*maquina-1* 192.168.100) instalamos las herramientas necesarias:
~~~
sudo apt-get install nfs-kernel-server nfs-common rpcbind
~~~

A continuación, creamos la carpeta que vamos a compartir y cambiamos el propietario y permisos de esa carpeta:
~~~
mkdir /etc/dat/compartida
sudo chown nobody:nogroup /etc/dat/compartida/
sudo chmod -R 777 /etc/dat/compartida/
~~~

![img](https://github.com/salva12345678/SWAP/blob/master/practica6/foto_1.png)

Ahora nos metemos en el fichero de control /etc/exports y ponemos:

~~~
/etc/dat/compartida/ 192.168.1.102(rw) 192.168.1.103(rw)
~~~

![img](https://github.com/salva12345678/SWAP/blob/master/practica6/foto_2.png)

Finalmente, debemos reiniciar el servicio:
~~~
sudo service nfs-kernel-server restart
~~~

En los clientes (M1 y M2) debemos instalar los paquetes necesarios y crear el punto de montaje (el directorio en cada máquina cliente):
~~~
sudo apt-get install nfs-common rpcbind
cd /home/usuario
mkdir carpetacliente
chmod -R 777 carpetacliente
~~~

Ahora ya podemos montar la carpeta remota (la exportada en el servidor) sobre el directorio recién creado:
~~~
sudo mount 192.168.1.100:/etc/dat/compartida carpetacliente
~~~

![img](https://github.com/salva12345678/SWAP/blob/master/practica6/foto_3.png)

Ahora nos creamos un fichero.txt vemos que se han creado en el resto de máquinas.

![img](https://github.com/salva12345678/SWAP/blob/master/practica6/foto_4.png)

Finalmente, para hacer la configuración permanente, debemos añadir una línea al archivo de configuración /etc/fstab en las máquinas cliente:

~~~
192.168.1.100:/etc/dat/compartida /home/salva1234567/carpetacliente/ nfs auto,noatime,nolock,bg,nfsvers=3,intr,tcp,actimeo=1800 0 0
~~~

Hemos apagado un cliente y vemos que funciona perfectamente.
