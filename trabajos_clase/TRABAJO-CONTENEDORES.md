# VIRTUALIZACIÓN
## JUAN SALVADOR MOLINA MARTÍN
## JOSE MIGUEL PELEGRINA PELEGRINA


## 1.VIRTUALIZACIÓN

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

Un hipervisor es un proceso que separa el sistema operativo de unordenador y las aplicaciones del hardware físico subyacente. Normalmente se hace como software, aunque se pueden crear hipervisores integrados para cosas como dispositivos móviles.

El hipervisor dirige el concepto de virtualización al permitir que la máquina física opere múltiples máquinas virtuales como invitados para ayudar a maximizar el uso efectivo de los recursos informáticos, como la memoria, el ancho de banda de la red y los ciclos de la CPU.

**Beneficios de los hipervisores**

A pesar de que las máquinas virtuales pueden ejecutarse en el mismo hardware físico, todavía están lógicamente separadas entre sí. Esto significa que si una VM experimenta un error, un bloqueo o un ataque de malware, no se extiende a otras máquinas virtuales en la misma máquina o incluso a otras máquinas.

Las VM también son móviles, ya que son independientes del hardware subyacente, se pueden mover o migrar entre servidores virtualizados remotos o locales mucho más fácilmente que las aplicaciones tradicionales que están vinculadas al hardware físico.

**Tipos de Hipervisores**

Podemos encontrar fundamentalmente tres tipos:



Tipo-1.Los hipervisores tipo 1, a veces denominados hipervisores "nativos" o "bare metal", se ejecutan directamente en el hardware del host para controlar el hardware y administrar las máquinas virtuales invitadas. Los hipervisores modernos incluyen Xen, Oracle VM Server para SPARC, Oracle VM Server para x86, Microsoft Hyper-V y VMware ESX / ESXi.

A su vez podemos encontrar dos tipos.

        Monolíticos: son hipervisores que emulan hardware para sus máquinas virtuales.Este funcionamiento obliga a desarrollar drivers específicos para el hipervisor de cada componente hardware.
        De MicroKernel: en esta aproximación el hipervisor se reduce a una capa de software muy sencilla, cuya única funcionalidad es la de particionar el sistema físico entre los diversos sistemas virtualizados.Con esta manera de funcionar los hipervisores de microkernel no requieren de drivers específicos para acceder al hardware.


Tipo-2.Los hipervisores tipo 2, a veces llamados "hipervisores hospedados", se ejecutan en un sistema operativo convencional, al igual que otras aplicaciones en el sistema. En este caso, un sistema operativo invitado se ejecuta como un proceso en el host, mientras que los hipervisores separan el sistema operativo invitado del sistema operativo host. Entre los ejemplos de hipervisores Tipo 2 se incluyen VMware Workstation, VMware Player, VirtualBox y Parallels Desktop para Mac.

Hipervisores híbridos.En este modelo tanto el sistema operativo anfitrión como el hipervisor interactúan directamente con el hardware físico.

![img](https://github.com/salva12345678/SWAP/blob/master/trabajos_clase/foto_1.png)









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

http://www.datakeeper.es/?p=716
