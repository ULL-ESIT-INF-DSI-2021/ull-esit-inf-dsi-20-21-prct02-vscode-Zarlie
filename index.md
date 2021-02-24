# **Práctica 2: Instalación y configuración de Visual Studio Code**
[Acceso a la Github Page](https://ull-esit-inf-dsi-2021.github.io/ull-esit-inf-dsi-20-21-prct01-iaas-Zarlie/)

 
## Introducción
En esta práctica se lleva a cabo la instalación y configuración del entorno de desarrollo que utilizaremos durante toda la asignatura, esto es, Visual Studio Code. El VSC es un editor de código fuente, el cual es compatible con varios lenguajes de programación e incluye soporte para la depuración, control integrado de Git, resaltado de sintaxis, finalización inteligente de código, fragmentos y refactorización de código.


## Objetivos
- Configurar VSC


### **Instalación del Visual Studio Code** 
Como ya hemos mencionado, esta práctica se basará en configurar el editor Visual Studio Code, que nos permitirá, entre muchas otras cosas, editar nuestro código fuente así como depurarlo. Para comenzar a familiarizarnos con este entorno, comenzaremos con instalarlo en nuestra máquina si aún no lo habíamos hecho anteriormente:
```
zarlie@melinux-VirtualBox:~$ sudo apt install code
```
O también podríamos hacer uso del comando *snap*, el cual es equivalente al comando de uso ms frecuente *apt*, este se usa para instalar software desde la Snap Store, en lugar de paquetes desde los repositorios Apt:
```
zarlie@melinux-VirtualBox:~$ sudo snap install code --classic
```
EL argumento *--classic* lo añadimos para que Snapcraft se instale sin las funciones de banco de pruebas estrictas que normalmente se usan en las Snaps. Snapcraft requiere este argumento, ya que necesita más acceso privilegiado a su sistema para empaquetar las aplicaciones de forma fiable.


### **Primeras configuraciones de Visual Studio Code** 
Una vez hemos instalado el editor de código fuente, procederemos a hacer ciertas configuraciones que nos serán útiles de cara a trabajar en este enorno en un futuro próximo, puesto que nos facilitar mucho el trabajo.  
En primer lugar, queremos poder conectarnos a nuestra máquina virtual del IaaS desde cualquier máquina independientemente el lugar en el que nos encontremos, para ello deberemos configurar VSCode para poder conectarnos por SSH como bien vimos en la práctica anterior, debiendo estar siempre conectados a la VPN de la ULL, ya que de lo contrario no será posible realizar dicha conexión.  
Abrimos la aplicación de VSCode y localizamos el buscador en la barra lateral izquierda con el símbolo de la lupa, ahí deberemos buscar la extensión ***Remote - SSH*** y le daremos al botón azul que dice *Install*, este proceso sólo tardará unos segundos. Una vez instalado, pulsaremos la tecla *F1* o bien *Ctrl + Shift + P*, eso nos abrirá un menú con varias de las funcionalidades que tenemos a instaladas en nuestro sistema; teclearemos *ssh* y de entre todas las opciones haremos click sobre *Connect to Host...* para configurar nuestra primera conexión por SSH en este entorno.




## Bibliografía
- [Visual Studio Code](https://es.wikipedia.org/wiki/Visual_Studio_Code)
- [Paquetes Snap de Ubuntu](https://www.profesionalreview.com/2016/04/21/conoce-los-paquetes-snap-ubuntu/)
- [Snap en Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-package-and-publish-a-snap-application-on-ubuntu-18-04-es#:~:text=El%20comando%20snap%20es%20equivalente,snap%20install%20snapcraft%20%2D%2Dclassic)
- [SSH](https://es.wikipedia.org/wiki/Secure_Shell)
