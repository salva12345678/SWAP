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

**2.Realizar la copia de seguridad de la BD completa usando mysqldump en la máquina principal y copiar el archivo de copia de seguridad a la máquina secundaria.**

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


**3.Restaurar dicha copia de seguridad en la segunda máquina (clonado manual  de la BD), de forma que en ambas máquinas esté esa BD de forma idéntica.**

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



También podemos hacer la orden directamente usando un “pipe” a un ssh para exportar los datos al mismo tiempo (siempre y cuando en la máquina secundaria ya hubiéramos creado la BD):

~~~
mysqldump contactos -u root -p | ssh 192.168.1.102 mysql
~~~


**4.Realizar la configuración maestro-esclavo de los servidores MySQL para que la  replicación de datos se realice automáticamente.**

Tenemos la opción de configurar el demonio para hacer replicación de las BD sobre un esclavo a partir de los datos que almacena el maestro.


Se trata de un proceso automático que resulta muy adecuado en un entorno de producción real. Implica realizar algunas configuraciones, tanto en el servidor principal como en el secundario.

Disponemos de la version 5.7.25.

![img](https://github.com/salva12345678/SWAP/blob/master/practica5/foto_9.png)

Primero tenemos que configurar la información de */etc/mysql/mysql.conf.d/mysqld.cnf* teniendo que comentar el parámetro #bind-address 127.0.0.1

![img](https://github.com/salva12345678/SWAP/blob/master/practica5/foto_10.png)

Ahora tenemos que descomentar la el parámetro *log_bin = /var/log/mysql/bin.log*.

Guardamos el documento y reiniciamos el servicio:

~~~
/etc/init.d/mysql restart
~~~

Si no nos ha dado ningún error la configuración del maestro, podemos pasar a hacer la configuración del mysql del esclavo (editar como root su archivo de configuración).

En este caso el server-id en esta ocasión será 2.La otra configuración es igual.

Guardamos el documento y reiniciamos el servicio:

~~~
/etc/init.d/mysql restart
~~~

![img](https://github.com/salva12345678/SWAP/blob/master/practica5/foto_11.png)


Podemos volver al maestro(*maquina-1*) para crear un usuario y darle permisos de acceso para la replicación.

![img](https://github.com/salva12345678/SWAP/blob/master/practica5/foto_12.png)

En el esclavo(*maquina-2*) entramos en mysql y le damos los datos del maestro.

![img](https://github.com/salva12345678/SWAP/blob/master/practica5/foto_13.png)

y arrancamos el esclavo:

~~~
mysql> START SLAVE;
~~~

Por último, volvemos al maestro y volvemos a activar las tablas para que puedan meterse nuevos datos en el maestro:

~~~
mysql> UNLOCK TABLES;
~~~

Ahora, si queremos asegurarnos de que todo funciona perfectamente y que el esclavo no tiene ningún problema para replicar la información, nos vamos al esclavo y con la siguiente orden:

~~~
mysql> SHOW SLAVE STATUS\G
~~~

Vemos que la variable **Seconds_Behind_Master** es 0 y por lo tanto ya nos funciona la configuración de *maestro-esclavo*.

![img](https://github.com/salva12345678/SWAP/blob/master/practica5/foto_14.png)

Ahora solo tenemos que introducir los datos y ver como se van replicando.

Metemos datos de ejemplo y como podemos ver en la imagen vemos que se va replicando.

![img](https://github.com/salva12345678/SWAP/blob/master/practica5/foto_15.png)
