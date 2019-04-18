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

## 3.TIPOS DE VIRTUALIZACIÓN.

En el mundo de la virtualización podemos encontrar diferentes tipos de técnicas por las cuales podemos obtener bastantes ventajas unas respecto a otras:

      Virtualización de hardware
      Virtualización a nivel de Sistema Operativo.
      Paravirtualización (paravirtualization)
      Virtualización completa (full virtualization)


## VIRTUALIZACIÓN DE HARDWARE

Este es el tipo de virtualización más complejo de lograr. Consiste en emular, mediante máquinas virtuales, los componentes de hardware. De esta manera el sistema operativo no se ejecuta sobre el hardware real sino sobre el virtual.


![img](https://github.com/salva12345678/SWAP/blob/master/trabajos_clase/foto_2.png)

## PARAVIRTUALIZACIÓN

La paravirtualización consiste en ejecutar sistemas operativos guests sobre otro sistema operativo que actúa como hipervisor (host). Los guests tienen que comunicarse con el hypervisor para lograr la virtualización.

![img](https://github.com/salva12345678/SWAP/blob/master/trabajos_clase/foto_3.png)

## VIRTUALIZACIÓN A NIVEL DE SISTEMA OPERATIVO.

Este es el otro extremo de la virtualización. En este esquema no se virtualiza el hardware y se ejecuta una única instancia del sistema operativo (kernel). Los distintos procesos perteneciente a cada servidor virtual se ejecutan aislados del resto.

![img](https://github.com/salva12345678/SWAP/blob/master/trabajos_clase/foto_4.png)

## VIRTUALIZACIÓN COMPLETA

La virtualización completa es similar a la paravirtualización pero no requiere que los sistemas operativos guest colaboren con el hypervisor. En plataformas como la x86 existen algunos inconvenientes para lograr la virtualización completa, que son solucionados con las últimas tecnologías propuestas por AMD e Intel.

![img](https://github.com/salva12345678/SWAP/blob/master/trabajos_clase/foto_5.png)

## 4.HERRAMIENTAS Y PRODUCTOS PARA LA VIRTUALIZACIÓN.

### 4.1.Workstation Player (VMware).

![img](https://github.com/salva12345678/SWAP/blob/master/trabajos_clase/foto_6.png)

Es una aplicación de virtualización de escritorios para uso personal. Se puede aplicar una licencia comercial para que Workstation Player ejecute las máquinas virtuales restringidas creadas por VMware Workstation Pro y Fusion Pro.Mware Workstation Player se basa en la misma plataforma que VMware Workstation Pro y vSphere, lo que la convierte en la solución más estable y consolidada para la virtualización de escritorios locales.

Con VMware Workstation Player podrá aislar los escritorios corporativos de los dispositivos BYOD desactivando las funciones de copiar y pegar, arrastrar y soltar, las carpetas compartidas y el acceso a los dispositivos USB.

Las funciones de aislamiento y entorno de pruebas de VMware Workstation Player lo convierten en la herramienta perfecta para aprender todo lo que necesita saber sobre sistemas operativos, aplicaciones y su funcionamiento. El hecho de ejecutar un entorno de servidor en un PC de escritorio también le permite explorar el desarrollo de software y aplicaciones en un entorno real sin interferir con el escritorio host.

Ejecute un segundo escritorio seguro con distintos ajustes de privacidad, herramientas y configuraciones de red para garantizar la seguridad de su sistema host mientras navega en línea.

Compatabilidad con la mayoria de los sistemas operativos actuales como:


    Windows 10
    Windows 8.X
    Windows 7
    Windows XP
    Ubuntu
    Red Hat
    SUSE
    Oracle Linux
    Debian
    Fedora
    openSUSE
    Mint
    CentOS

[Workstation Player](https://www.vmware.com/es/products/workstation-player.html)

### 4.2.DOCKER.

![img](https://github.com/salva12345678/SWAP/blob/master/trabajos_clase/foto_7.png)

Docker es una plataforma de software que le permite crear, probar e implementar aplicaciones rápidamente. Docker empaqueta software en unidades estandarizadas llamadas contenedores que incluyen todo lo necesario para que el software se ejecute, incluidas bibliotecas, herramientas de sistema, código y tiempo de ejecución. Con Docker, puede implementar y ajustar la escala de aplicaciones rápidamente en cualquier entorno con la certeza de saber que su código se ejecutará.

Docker le proporciona una manera estándar de ejecutar su código. Docker es un sistema operativo para contenedores. De manera similar a cómo una máquina virtual virtualiza (elimina la necesidad de administrar directamente) el hardware del servidor, los contenedores virtualizan el sistema operativo de un servidor. Docker se instala en cada servidor y proporciona comandos sencillos que puede utilizar para crear, iniciar o detener contenedores.

![img](https://github.com/salva12345678/SWAP/blob/master/trabajos_clase/foto_8.png)

[Docker](https://www.docker.com/)


### 4.3.LXD(Linux containers).

![img](https://github.com/salva12345678/SWAP/blob/master/trabajos_clase/foto_9.png)

Aparentemente en un contenedor se ejecuta un sistema operativo GNU/Linux independiente de otros contenedores y del propio SO anfitrión. Se trata de un producto de la virtualización pero, en lugar de utilizar máquinas virtuales dentro de las cuales se ejecuta un sistema operativo que puede ser diferente del anfitrión, aquí se utilizan técnicas de virtualización a nivel de sistema operativo. De modo que sólo hay un núcleo, en nuestro caso el Linux que se ejecuta en el equipo anfitrión, que mediante diferentes funciones (namespaces, cgroups, ...) muestra vistas parciales a algunos procesos para que crean que se ejecutan en un sistema aislado.

Así que el sistema anfitrión y todos los contenedores utilizan el mismo núcleo. En el sistema anfitrión se pueden ver todos los procesos y en cada uno de los contenedores únicamente los propios. La red, la raíz del sistema de archivos, los ficheros de dispositivo y otros recursos también están virtualizados así que cada contenedor puede tener su propia interfaz de red y sistema de archivos raíz. Incluso es posible que un contenedor utilice una distribución de GNU/Linux diferente del resto pero, eso sí, compartiendo el único núcleo que se ejecuta en el equipo anfitrión.

Las ventaja de los contenedores frente a las máquinas virtuales tradicionales es la eficiencia. Un contenedor es mucho más ligero pues no necesita recrear el hardware de la máquina virtual ni ejecutar dentro otro sistema operativo. Los procesos que se ejecutan en un contenedor al fin y al cabo son procesos nativos del equipo anfitrión. Por lo tanto se consigue un mayor rendimiento y es posible ejecutar en un mismo ordenador un número mucho mayor de contenedores que de máquinas virtuales.El inconveniente de los contenedores frente a la virtualización completa asistida por hardware es que se apoya en Linux y todos los contenedores deben ejecutar una distribución de GNU/Linux.

![img](https://github.com/salva12345678/SWAP/blob/master/trabajos_clase/foto_10.png)

[LXD](https://linuxcontainers.org/)


### 4.4.VAGRANT.

![img](https://github.com/salva12345678/SWAP/blob/master/trabajos_clase/foto_11.png)






[VAGRANT](https://www.vagrantup.com/)












https://elpuig.xeill.net/Members/vcarceler/articulos/contenedores-con-lxd-lxc

https://profesorweb.es/wp-content/uploads/2017/10/tema3_iso_virtualizacion.pdf

https://www.campusmvp.es/recursos/post/Docker-vs-Vagrant-diferencias-y-similitudes-y-cuando-usar-cada-uno.aspx

https://www.networkworld.es/m2m/que-es-un-hipervisor

http://www.datakeeper.es/?p=716

https://blog.smaldone.com.ar/2008/09/20/virtualizacion-de-hardware/
