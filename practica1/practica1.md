# PRACTICA 1:PREPARACION DE LAS PRACTICAS.
## 1 Sesión.

La practica consiste en llevar a cabo la instalación de dos máquinas virtuales y que tengamos instalado el **Apache**,**Php** y **Mysql**.

Para ello hemos decidido usar el **VirtualBox**.

![img](https://github.com/salva12345678/SWAP/blob/master/practica1/Foto_1.png)

Cuando hemos terminado de instalar las máquinas virtuales tenemos que asignarle una **IP** a cada máquina virtual.Para ello nos metemos en cada máquina en el fichero:*/etc/network/interface*.

Añadimos en el **enp0s8**.
Tenemos que decir que a cada máquina se le ha asignado una **IP** distinta.Maquina 1(192.168.1.100) y Maquina 2(192.168.1.101).

![img](https://github.com/salva12345678/SWAP/blob/master/practica1/foto_2.png)

Después de ello tenemos que reiniciar el servicio ya que sino no tendremos servicio a internet.

Para ello escribimos en la terminal-->*systemctl restart networking.service*.

![img](https://github.com/salva12345678/SWAP/blob/master/practica1/foto_3.png)

Ahora podemos llevar a cabo la instalación del **Apache**,**Php** y **Mysql**.

Ahora debemos ver la versión del **Apache** instalado y ver si está en ejecución.

![img](https://github.com/salva12345678/SWAP/blob/master/practica1/foto_4.png)
