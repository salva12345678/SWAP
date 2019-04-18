# VIRTUALIZACIÓN
## JUAN SALVADOR MOLINA MARTÍN
## JOSE MIGUEL PELEGRINA PELEGRINA


# 1.VIRTUALIZACIÓN

La virtualización crea un entorno informático simulado, o virtual, en lugar de un entorno físico. A menudo, incluye versiones de hardware, sistemas operativos, dispositivos de almacenamiento, etc., generadas por un equipo. Esto permite a las organizaciones particionar un equipo o servidor físico en varias máquinas virtuales. Cada máquina virtual puede interactuar de forma independiente y ejecutar sistemas operativos o aplicaciones diferentes mientras comparten los recursos de una sola máquina host.

Al crear varios recursos a partir de un único equipo o servidor, la virtualización mejora la escalabilidad y las cargas de trabajo, al tiempo que permite usar menos servidores y reducir el consumo de energía, los costos de infraestructura y el mantenimiento. La virtualización se divide en cuatro categorías principales. La primera es la virtualización de escritorio, que permite que un servidor centralizado ofrezca y administre escritorios individualizados. La segunda es la virtualización de red, diseñada para dividir el ancho de banda de una red en canales independientes que se asignan a servidores o dispositivos específicos. La tercera categoría es la virtualización de software, que separa las aplicaciones del hardware y el sistema operativo. Y la cuarta es la virtualización de almacenamiento, que combina varios recursos de almacenamiento en red en un solo dispositivo de almacenamiento accesible por varios usuarios.

**Ventajas generales:**

      Permite una mejor utilización de los recursos de infraestructura de hardware y software.
      Aumenta la seguridad del ambiente, pues contar con una administración centralizada mejora el monitoreo y control de los datos, además de facilitar la aplicación de políticas de seguridad.
      Actualización más rápida y sencilla de las versiones y el despliegue de las nuevas aplicaciones.
      Mayor disponibilidad y continuidad de negocios (DRP: replicación y sitio de contingencia, en caso de ser necesario).
      Flexibilidad y agilidad en despliegues y crecimiento.

**Beneficios de la virtualización de escritorios:**

      Los dispositivos de los usuarios (thin clients) son más económicos que una PC y solo sirven para ese propósito.
      Las tasas de falla de los clientes delgados son muy bajas, debido a que no tienen partes móviles. Por lo tanto, la vida útil actual supera los seis años.
      El costo total de propiedad para proyectos de evaluación mayor a seis años puede ser relevante, considerando entornos de muchos usuarios y con mucha dispersión geográfica.
      Acceso remoto con múltiples dispositivos, lo que permite mayor movilidad de los usuarios.

**Beneficios de la virtualización de servidores:**

      Mayor control del costo total de propiedad. Los departamentos de TI pueden distribuir mejor las plataformas y costos por diferentes unidades de negocio.
      Los ambientes virtualizados están hospedados normalmente en centros de datos de clase mundial (idealmente Tier III o IV), que tienen niveles mayores de disponibilidad y seguridad que los centros de datos empresariales tradicionales.
      Los sistemas de respaldo de datos son más eficientes y económicos, y las opciones de tener sitio de contingencia son más sencillas.
      Al incorporarse herramientas de orquestación o automatización, se aumenta el uso, el control y la eficiencia del entorno virtual.

**Aumento de los costos iniciales:**

      La elevada inversión en software para gestionar servidores virtuales.
      Es necesario realizar un estudio previo para conocer cuáles serán los gastos de implementación.
      Tienes la opción de alquilar los servidores a una empresa proveedora pero debes asegurarte de que la empresa contratada asegure al 100 % los datos de tu negocio.

**Necesidad de aprender a manejar el nuevo entorno virtual:**

      Antes de implementar la virtualización en tu empresa deberás tener en cuenta que, si tus administradores de sistemas no están familiarizados con la gestión de este tipo de entornos virtuales, deberán aprender a manejar multitud de nuevas herramientas, lo cual no siempre es fácil.

**Menor rendimiento:**

      Dado que los servidores virtuales corren en una capa intermedia a la del hardware real el rendimiento será inferior que mediante el uso de servidores tradicionales.
      Por otro lado, si instalas muchas máquinas virtuales en un solo servidor físico acabarás saturando el mismo, lo cual también implicará una reducción considerable del rendimiento. Es importante que solo se creen las máquinas virtuales indispensables, ni una más.



## 2.HIPERVISOR

un hipervisor es un proceso que separa el sistema operativo de unordenador y las aplicaciones del hardware físico subyacente. Normalmente se hace como software, aunque se pueden crear hipervisores integrados para cosas como dispositivos móviles.

El hipervisor dirige el concepto de virtualización al permitir que la máquina física opere múltiples máquinas virtuales como invitados para ayudar a maximizar el uso efectivo de los recursos informáticos, como la memoria, el ancho de banda de la red y los ciclos de la CPU.






En el mundo de la virtualización podemos encontrar diferentes tipos de técnicas por las cuales podemos obtener bastantes ventajas unas respecto a otras:

      Virtualización completa del hardware o nativa.
      Virtualización de emulación de hardware o no nativa.
      Virtualización a nivel de Sistema Operativo.



##VIRTUALIZACIÓN COMPLETA DEL HARDWARE O NATIVA.

VMWare Server, XenServer, VMWare ESX
VIRTUALBOX


##VIRTUALIZACIÓN DE EMULACIÓN DE HARDWARE O NO NATIVA.

Xen

##VIRTUALIZACIÓN A NIVEL DE SISTEMA OPERATIVO.

OpenVZ, Docker, Virtuozzo, Chroot Jails, LXC, etc.



![img](https://github.com/salva12345678/SWAP/blob/master/practica1/Foto_1.png)


[Enlace del producto](https://www.pccomponentes.com/msi-mpg-z390-gaming-plus)


https://elpuig.xeill.net/Members/vcarceler/articulos/contenedores-con-lxd-lxc

https://profesorweb.es/wp-content/uploads/2017/10/tema3_iso_virtualizacion.pdf

https://www.campusmvp.es/recursos/post/Docker-vs-Vagrant-diferencias-y-similitudes-y-cuando-usar-cada-uno.aspx

https://www.networkworld.es/m2m/que-es-un-hipervisor
