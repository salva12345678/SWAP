# PRACTICA 3: BALANCEO DE CARGA
## 2 Sesión.

El objetivo de la práctica es:

Conseguir configurar una red entre varias máquinas de forma que tengamos un *balanceador* que reparta la carga entre varios servidores finales para conseguir una infraestructura redundante y de alta disponibilidad.

Para ello tendremos esta organización en red:

![img](https://github.com/salva12345678/SWAP/blob/master/practica3/foto_1.png)

Viendo la situación nos tendremos que crear dos nuevas máquinas virtuales o en mi caso que han sido clonadas y ademas en ellas nos hemos encargado de eliminar el apache2 para dejar libre el puerto80.

En la *máquina-3* que va ha actuar de *balanceador* de carga vamos a instalar el programa nginx.

~~~
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get autoremove

sudo apt-get install nginx

sudo systemctl start nginx

~~~

Ahora que lo tenemos instalado podemos hacerla configuración del balanceador.Para ello nos tenemos que ir al fichero **/etc/nginx/conf.d/default.conf**.

![img](https://github.com/salva12345678/SWAP/blob/master/practica3/foto_2.png)

~~~
sudo systemctl start nginx
~~~

Ahora hacemos un curl a las direcciones de cada máquina.

![img](https://github.com/salva12345678/SWAP/blob/master/practica3/foto_3.png)

En las opciones de configuración **/etc/nginx/conf.d/default.conf** le asignamos como queremos establecer el trabajo entre las máquinas que tenemos.

~~~
upstream backend{

  server 192.168.1.100 weight=1

  server 192.168.1.102 weight=1

}
~~~

Ahora usaremos otro tipo de *balanceador* de carga llamado **haproxy**.

Como en el caso anterior volveremos a instalar el *balanceador*.

~~~
sudo apt-get install haproxy
~~~

Ahora llevaremos a cabo la configuración del *balanceador*.

![img](https://github.com/salva12345678/SWAP/blob/master/practica3/foto_4.png)

Como fue el caso de **nginx** podemos modificar la configuración para repartir el trabajo.

Lo interesante es someter a las máquinas virtuales a una alta carga de trabajo y ver como se reparten el trabajo.Para ello se va usar el **Apache Benchmark (ab)** en una *máquina-4* que actúe como cliente.

Para ello hemos creado otra máquina virtual de modo que tenemos 2 *balanceadores* para que uno de trabaje con **nginx** y el otro con **haproxy**.

**haproxy:**

Abrimos la *máquina-cliente* para lanzar la orden y ver el resultado.

~~~
ab -n 1000 -c 10 http://192.168.1.103/index.html
~~~

![img](https://github.com/salva12345678/SWAP/blob/master/practica3/foto_6.png)

Con el **htop** vemos la *máquina1* y *máquina2*  

![img](https://github.com/salva12345678/SWAP/blob/master/practica3/foto_5.png)

**nginx**

Abrimos la *máquina-cliente* para lanzar la orden y ver el resultado.

~~~
ab -n 1000 -c 10 http://192.168.1.103/index.html
~~~

![img](https://github.com/salva12345678/SWAP/blob/master/practica3/foto_8.png)

Con el **htop** vemos la *máquina1* y *máquina2*

![img](https://github.com/salva12345678/SWAP/blob/master/practica3/foto_7.png)
