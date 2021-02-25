# **Práctica 2: Instalación y configuración de Visual Studio Code**
[Acceso a la Github Page](https://ull-esit-inf-dsi-2021.github.io/ull-esit-inf-dsi-20-21-prct01-iaas-Zarlie/)

 
## Introducción
En esta práctica se lleva a cabo la instalación y configuración del entorno de desarrollo que utilizaremos durante toda la asignatura, esto es, Visual Studio Code. El VSC es un editor de código fuente, el cual es compatible con varios lenguajes de programación e incluye soporte para la depuración, control integrado de Git, resaltado de sintaxis, finalización inteligente de código, fragmentos y refactorización de código.


## Objetivos
- Configurar VSC


## **Instalación del Visual Studio Code** 
Como ya hemos mencionado, esta práctica se basará en configurar el editor Visual Studio Code, que nos permitirá, entre muchas otras cosas, editar nuestro código fuente así como depurarlo. Para comenzar a familiarizarnos con este entorno, comenzaremos con instalarlo en nuestra máquina si aún no lo habíamos hecho anteriormente:
```
zarlie@melinux-VirtualBox:~$ sudo apt install code
```
O también podríamos hacer uso del comando *snap*, el cual es equivalente al comando de uso ms frecuente *apt*, este se usa para instalar software desde la Snap Store, en lugar de paquetes desde los repositorios Apt:
```
zarlie@melinux-VirtualBox:~$ sudo snap install code --classic
```
EL argumento *--classic* lo añadimos para que Snapcraft se instale sin las funciones de banco de pruebas estrictas que normalmente se usan en las Snaps. Snapcraft requiere este argumento, ya que necesita más acceso privilegiado a su sistema para empaquetar las aplicaciones de forma fiable.


## **Primeras configuraciones de Visual Studio Code** 
### **Conexión SSH** 
Una vez hemos instalado el editor de código fuente, procederemos a hacer ciertas configuraciones que nos serán útiles de cara a trabajar en este enorno en un futuro próximo, puesto que nos facilitar mucho el trabajo.  
En primer lugar, queremos poder conectarnos a nuestra máquina virtual del IaaS desde cualquier máquina independientemente el lugar en el que nos encontremos, para ello deberemos configurar VSCode para poder conectarnos por SSH como bien vimos en la práctica anterior, debiendo estar siempre conectados a la VPN de la ULL, ya que de lo contrario no será posible realizar dicha conexión.  
Abrimos la aplicación de VSCode y localizamos el buscador en la barra lateral izquierda con el símbolo de la lupa, ahí deberemos buscar la extensión ***Remote - SSH*** y le daremos al botón azul que dice *Install*, este proceso sólo tardará unos segundos. Una vez instalado, pulsaremos la tecla *F1* o bien *Ctrl + Shift + P*, eso nos abrirá un menú con varias de las funcionalidades que tenemos a instaladas en nuestro sistema; teclearemos *ssh* y de entre todas las opciones haremos click sobre *Connect to Host...* y, si seguimos todos los pasos correctamente en la práctica anterior, nos debería de aparecer el nombre de nuestra máquina virtual en el menú desplegable como ***iaas-dsiXX***:
```
CyA
Admin
iaas-dsi36
+ Add New SSH Host...
Configure SSH Hosts...
```
En caso de que no nos aparezca entre las opciones, sólo debemos pulsar sobre la última opción *Configure SSH Hosts...* y en el menú desplegable que nos aparece con los distintos ficheros a configurar seleccionamos el *~/.ssh/config* donde nos aparecerán las configuraciones de todas las máquinas que hayamos añadido en algún momento dado:
```
Host 10.6.131.85
  HostName CyA
  User usuario
  
Host 10.6.129.97
  HostName Admin
  User usuario
  
Host iaas-dsi36
  HostName iaas-dsi36
  User usuario
```
Como se puede observar, en mi caso ya la tenía añadida junto a unas cuantas más correspondientes a otras asignaturas, pero en caso de no tenerla simplemente bastaría con seguir el mismo esquema, introduciendo los valores que introdujimos en un momeno inicial en nuestra máquina virtual del IaaS:
```
Host iaas-dsiXX
  HostName iaas-dsiXX
  User usuario
```
Una vez configurado el fichero, podremos comprobar si los cambios se han guardado correctamente con tan sólo volver a realizar los pasos que hicimos anteriormente, esto es: pulsaremos la tecla *F1* o bien *Ctrl + Shift + P*, escribimos *ssh* y volvemos a hacer click sobre la opción *Connect to Host...* y ahora deberíamos de visualizar el nombre de nuestra máquina.  Si pulsamos sobre ella, se debería de abrir una nueva ventana de VSCode donde se comenzara a establecer nuestra conexión SSH con la máquina virtual del IaaS, en la parte inferior del lateral izquierdo de la aplicación, debería de aparecer un recuadro verde con las letras ****Opening Remote...*** tardando apenas unos segundos en completarse la conexión.  
En caso de que quisiéramos comprobar que, efectivamente se ha completado la conexión SSH satisfactoriamente, tenemos 2 formas: se puede comprobar a simple vista dentro del entorno de VSCode volviendo a ver el recuadro verde pero esta vez con las letras ***SSH: iaas-dsi36*** o bien podemos hacerlo abriendo una terminal en VSCode pulsando en la barra superior sobre *Terminal* o bien mediante la combinación de teclas *Ctrl + SHift + '*  y ejecutamos el siguiente comando:
```
[~()]$ hostname
iaas-dsi36
[~()]$
```


### **Extensión de LiveShare: Sesiones colaborativas** 
En este apartado, nos familiarizaremos con otra extensión del VSCode: Live Share Extension Pack. Esta extensión es muy útil de cara a proyectos colaborativos ya sea de pocas o muchas personas, ya que nos permite compartir nuestro espacio de trabajo y todo el código fuente




## Bibliografía
- [Guión de la Práctica](https://ull-esit-inf-dsi-2021.github.io/prct02-vscode/)
- [Visual Studio Code](https://es.wikipedia.org/wiki/Visual_Studio_Code)
- [Paquetes Snap de Ubuntu](https://www.profesionalreview.com/2016/04/21/conoce-los-paquetes-snap-ubuntu/)
- [Snap en Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-package-and-publish-a-snap-application-on-ubuntu-18-04-es#:~:text=El%20comando%20snap%20es%20equivalente,snap%20install%20snapcraft%20%2D%2Dclassic)
- [SSH](https://es.wikipedia.org/wiki/Secure_Shell)
- [VSCode Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery)
- [Remote SSH: Tips and Tricks](https://code.visualstudio.com/blogs/2019/10/03/remote-ssh-tips-and-tricks)
- [Live Share Extension Pack](https://visualstudio.microsoft.com/es/services/live-share/)
