# PRÁCTICA 5. REPLICACIÓN DE BASES DE DATOS MYSQL
## 2 Sesión.

Los objetivos concretos de esta práctica son:

      **1.Crear una BD con al menos una tabla y algunos datos.**
      **2.Realizar la copia de seguridad de la BD completa usando mysqldump en lamáquina principal y copiar el archivo de copia de seguridad a la máquina
      secundaria.**
      **3.Restaurar dicha copia de seguridad en la segunda máquina (clonado manual  de la BD), de forma que en ambas máquinas esté esa BD de forma idéntica.**
      **4.Realizar la configuración maestro-esclavo de los servidores MySQL para que la  replicación de datos se realice automáticamente.**


**1.Crear una BD con al menos una tabla y algunos datos.**

Desde la *maquina-1* nos creamos una pequeña base de datos utilizando *MySQL*.Además de tener que introducir algunos datos para comprobar que nos funciona.

Para conectarnos a *MySQL* tenemos que:

~~~
mysql -uroot -p
~~~

![img](https://github.com/salva12345678/SWAP/blob/master/practica5/foto_1.png)

Nos creamos la base de datos llamada *contactos* y dentro de ella nos crearemos la tablas.

~~~
create database contactos;
use contactos;
create table datos(nombre varchar(100),tlf int);
show tables;
~~~

![img](https://github.com/salva12345678/SWAP/blob/master/practica5/foto_2.png)

Vemos que nuestras tablas están vacias por lo que insertamos datos de prueba.

~~~
insert into datos(nombre,tlf) values ("pepe",95834987);
insert into datos(nombre,tlf) values ("paco",65834887);
insert into datos(nombre,tlf) values ("manuel",15854987);
insert into datos(nombre,tlf) values ("salva",25834487);
insert into datos(nombre,tlf) values ("fran",25852937);
~~~

Y ahora podemos ver las tablas

![img](https://github.com/salva12345678/SWAP/blob/master/practica5/foto_3.png)

**2.Realizar la copia de seguridad de la BD completa usando mysqldump en la máquina principal y copiar el archivo de copia de seguridad a la máquina
secundaria.**

MySQL ofrece la una herramienta para clonar las BD que tenemos en nuestra maquina. Esta herramienta es mysqldump.Mysqldump es parte de los programas de cliente de MySQL, que puede ser utilizado para generar copias de seguridad de BD.

La idea es que tenemos que tener en cuenta que los datos pueden estar actualizándose constantemente en el servidor de BD principal. En este caso, antes de hacer la copia de seguridad en el archivo .SQL debemos evitar que se acceda a la BD para cambiar nada.

Desde la *máquina-1* hacemos:

~~~
mysql -u root –p
FLUSH TABLES WITH READ LOCK;
quit
~~~

![img](https://github.com/salva12345678/SWAP/blob/master/practica5/foto_4.png)

Guardamos los datos.

~~~
mysqldump contactos -u root -p > /tmp/ejemplodb.sql
~~~

Como habíamos bloqueado las tablas, debemos desbloquearlas (quitar el “LOCK”):

~~~
mysql -u root –p
mysql> UNLOCK TABLES;
mysql> quit
~~~

![img](https://github.com/salva12345678/SWAP/blob/master/practica5/foto_5.png)

Desde la *maquina-2*.

~~~
scp maquina1:/tmp/ejemplodb.sql /tmp/
~~~

![img](https://github.com/salva12345678/SWAP/blob/master/practica5/foto_6.png)

Nos tenemos que crear la base de datos en la *máquina-2*:
~~~
mysql -u root –p
mysql> CREATE DATABASE contactos;
quit
~~~

Ahora los exportamos.

~~~
mysql -u root -p contactos < /tmp/ejemplodb.sql
~~~

![img](https://github.com/salva12345678/SWAP/blob/master/practica5/foto_7.png)

Nos metemos en sql de la *máquina-2*.

~~~
mysql -u root –p
use contactos;
select * from datos;
~~~

![img](https://github.com/salva12345678/SWAP/blob/master/practica5/foto_8.png)


**3.Restaurar dicha copia de seguridad en la segunda máquina (clonado manual  de la BD), de forma que en ambas máquinas esté esa BD de forma idéntica.**










**4.Realizar la configuración maestro-esclavo de los servidores MySQL para que la  replicación de datos se realice automáticamente.**







      solo tocar la máquina-1 y maquina-2(backend)


      |  Memoria                                      | GDDR5                             | GDDR5X                                                                  | HBM                               | HBM2                                                                                                                    |
      |-----------------------------------------------|-----------------------------------|-------------------------------------------------------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------------------|
      | Fabricantes                                   | Samsung,Hynix,Elpida              | Micron                                                                  | Hynix,Samsumg                     | Samsung, Hynix                                                                                                          |
      | Capacidad Máxima                              | 8GB                               | 16GB                                                                    | 1GB por die                       |  4GB / 8GB por die                                                                                                      |
      | Velocidad Máxima                              | 8 Gbps                            | 10 to 14 Gbps (16 Gbps in future)                                       | 1 Gbps                            | 2.4 Gbps                                                                                                                |
      | Ancho de Bus                                  | 32-bit per chip                   | 64-bit per chip                                                         | 1024-bit por die                  | 1024-bit por die or more                                                                                                |
      | Consumo                                       | 1,5V                              | 1,5V                                                                    | Menos que la GDDR5                | Menos que el HBM                                                                                                        |
      |  Tarjetas Gráficas   que usan   la tecnologia |  GT 740, GTX 1070,   RX 480, etc. |  GeForce GTX 1080,   GTX 1080 Ti,   GTX 1060,   Nvidia Titan X (Pascal) |  Radeon R9 Fury X, Radeon Pro Duo |  Nvidia Tesla P100,   Nvidia Quadro GP100,   Radeon RX Vega 56,   Radeon RX Vega 64,   Nvidia Titan V,   AMD Radeon VII |
