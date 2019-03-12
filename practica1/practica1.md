# PRACTICA 1:PREPARACION DE LAS PRACTICAS.
## 1 Sesión.

La practica consiste en llevar a cabo la instalación de dos máquinas virtuales y que tengamos instalado el **Apache**,**Php** y **Mysql**.

Para ello hemos decidido usar el **VirtualBox**.

![img](https://github.com/salva12345678/SWAP/blob/master/practica1/Foto_1.png)

Cuando hemos terminado de instalar las máquinas virtuales tenemos que asignarle una **IP** a cada máquina virtual.Para ello nos metemos en cada máquina en el fichero:*/etc/network/interface*.

Añadimos en el **enp0s8**.
Tenemos que decir que a cada máquina se le ha asignado una **IP** distinta.Maquina 1(192.168.1.100) y Maquina 2(192.168.1.102).

![img](https://github.com/salva12345678/SWAP/blob/master/practica1/foto_2.png)

Después de ello tenemos que reiniciar el servicio ya que sino no tendremos servicio a internet.

Para ello escribimos en la terminal-->*systemctl restart networking.service*.

![img](https://github.com/salva12345678/SWAP/blob/master/practica1/foto_3.png)

Ahora podemos llevar a cabo la instalación del **Apache**,**Php** y **Mysql**.

Ahora debemos ver la versión del **Apache** instalado y ver si está en ejecución.

![img](https://github.com/salva12345678/SWAP/blob/master/practica1/foto_4.png)

Tenemos que crearnos un *Html* en el directorio  **/var/www** y con el comando *curl* mostrar el fichero por pantalla.

Básicamente en cada máquina virtual hacemos un *curl* de la dirección del servidor añadiendo el nombre del fichero--> curl htpp://192.168.1.100/hola.html y curl htpp://192.168.1.102/hola.html

**Maquina 1:**

![img](https://github.com/salva12345678/SWAP/blob/master/practica1/foto_6.png)

**Maquina 2:**

![img](https://github.com/salva12345678/SWAP/blob/master/practica1/foto_7.png)

Por último tenemos que comprobar que funciona el *ssh* para desde la máquina 1 o 2  poder conectarnos a la otra o viceversa.

Lo unico que tenemos que hacer es desde la *Maquina 1* y la *Máquina 2* --> ssh 192.168.1.100 y ssh 192.168.1.102 de forma respectiva.

**Maquina 1:**

![img](https://github.com/salva12345678/SWAP/blob/master/practica1/foto_8.png)

**Maquina 2:**

![img](https://github.com/salva12345678/SWAP/blob/master/practica1/foto_9.png)
