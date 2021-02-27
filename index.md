# **Práctica 2: Instalación y configuración de Visual Studio Code**
[Acceso a la Github Page](https://ull-esit-inf-dsi-2021.github.io/ull-esit-inf-dsi-20-21-prct01-iaas-Zarlie/)

 
## Introducción
En esta práctica se lleva a cabo la instalación y configuración del entorno de desarrollo que utilizaremos durante toda la asignatura, esto es, Visual Studio Code. El VSC es un editor de código fuente, el cual es compatible con varios lenguajes de programación e incluye soporte para la depuración, control integrado de Git, resaltado de sintaxis, finalización inteligente de código, fragmentos y refactorización de código.


## Objetivos
- Configurar el entorno de Visual Studio Code
- Aprender a trabajar con diferentes extensiones como Remote-SSH para conectarnos de forma remota a nuestra máquina virtual o Live Share para realizar sesiones colaborativas
- Familiarizarnos con el lenguaje de programación TypeScript realizando un primer proyecto: Hola Mundo 


## Instalación del Visual Studio Code 
Como ya hemos mencionado, esta práctica se basará en configurar el editor Visual Studio Code para la realización de un pequeño proyecto inicial, que nos permitirá, entre muchas otras cosas, editar nuestro código fuente así como depurarlo. Para empezar a familiarizarnos con este entorno, comenzaremos por instalarlo en nuestra máquina si aún no lo habíamos hecho anteriormente:
```
zarlie@melinux-VirtualBox:~$ sudo apt install code
```
Para instalar el programa, podemos hacerlo o bien mediante el ya conocido *apt* o también podríamos hacer uso del comando *snap*, el cual es su equivalente; este se usa para instalar software desde la Snap Store, en lugar de paquetes desde los repositorios Apt:
```
zarlie@melinux-VirtualBox:~$ sudo snap install code --classic
```
EL argumento *--classic* lo añadimos para que Snapcraft se instale sin las funciones de banco de pruebas estrictas que normalmente se usan en las Snaps. Snapcraft requiere este argumento ya que necesita más acceso privilegiado a su sistema para empaquetar las aplicaciones de forma fiable.


## Primeras configuraciones de Visual Studio Code
### **Conexión SSH** 
Una vez hemos instalado el editor de código fuente, procederemos a hacer ciertas configuraciones que nos serán útiles de cara a trabajar en este enorno en las próximas prácticas puesto que nos va a facilitar mucho el trabajo.  
En primer lugar, queremos poder conectarnos a nuestra máquina virtual del IaaS desde cualquier máquina, independientemente del lugar en el que nos encontremos; para ello, debemos configurar VSCode para poder conectarnos por SSH como bien vimos en la [**práctica anterior**](https://ull-esit-inf-dsi-2021.github.io/ull-esit-inf-dsi-20-21-prct01-iaas-Zarlie/), debiendo estar siempre conectados a la VPN de la ULL, ya que de lo contrario no será posible realizar dicha conexión.  

Abrimos la aplicación de VSCode y localizamos el buscador en la barra lateral izquierda con el símbolo de la lupa, ahí deberemos buscar la extensión **Remote - SSH** y le daremos al botón azul que dice *Install* (este proceso sólo tardará unos segundos). Una vez instalado, pulsaremos la tecla *F1* o bien la combinación de teclas *Ctrl + Shift + P*, eso nos abrirá un menú con varias de las funcionalidades que tenemos a instaladas en nuestro sistema; teclearemos *ssh* y de entre todas las opciones haremos click sobre *Connect to Host...* y, si seguimos todos los pasos correctamente en la práctica anterior, nos debería de aparecer el nombre de nuestra máquina virtual en el menú desplegable como ***iaas-dsiXX***:
```
CyA
Admin
iaas-dsi36
+ Add New SSH Host...
Configure SSH Hosts...
```
En caso de que no nos aparezca entre las opciones, sólo debemos pulsar sobre la última opción *Configure SSH Hosts...* y en el menú desplegable que nos aparece con los distintos ficheros a configurar seleccionamos el *~/.ssh/config* donde nos aparecerán las configuraciones de todas las máquinas que hayamos añadido en algún momento dado:
```
Host CyA
  HostName 10.6.131.85
  User usuario
  
Host Admin
  HostName 10.6.129.97
  User zarlie
  
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
Una vez configurado el fichero, podremos comprobar si los cambios se han guardado correctamente con tan sólo volver a realizar los pasos que hicimos anteriormente, esto es: pulsaremos la tecla *F1* o bien *Ctrl + Shift + P*, escribimos *ssh* y volvemos a hacer click sobre la opción *Connect to Host...* y ahora deberíamos de visualizar el nombre de nuestra máquina.  Si pulsamos sobre ella, se debería de abrir una nueva ventana de VSCode donde se comenzara a establecer nuestra conexión SSH con la máquina virtual del IaaS, en la parte inferior del lateral izquierdo de la aplicación, debería de aparecer un recuadro verde con las letras ***Opening Remote...*** tardando apenas unos segundos en completarse la conexión.  

En caso de que quisiéramos comprobar que, efectivamente se ha completado la conexión SSH satisfactoriamente, tenemos 2 formas de verlo: se puede comprobar a simple vista dentro del entorno de VSCode volviendo a ver el recuadro verde pero esta vez con las letras ***SSH: iaas-dsi36*** o bien podemos hacerlo abriendo una terminal en VSCode pulsando en la barra superior sobre *Terminal* o bien mediante la combinación de teclas *Ctrl + Shift + ñ* y ejecutamos el siguiente comando:
```
[~()]$ hostname
iaas-dsi36
[~()]$
```

### **Extensión de LiveShare: Sesiones colaborativas** 
En este apartado, nos familiarizaremos con otra extensión del VSCode: **Live Share Extension Pack**. Esta extensión es muy útil de cara a proyectos colaborativos ya sea de pocas o muchas personas, ya que nos permite compartir nuestro espacio de trabajo desde cualquier lugar así como editar y depurar todo el código fuente en tiempo real. Entre sus diversas funcionalidades incluye la posibilidad de hablar por su chat incorporado o bien mediante llamadas de voz.  

Para instalar esta extensión tenemos que seguir los mismos pasos que ya realizamos previamente al instalar la extensión de SSH: en la aplicación de VSCode localizamos el buscador en la barra lateral izquierda con el símbolo de la lupa y escribimos ***Live Share*** e instalamos las principales extensiones, estas son: *Live Share*, *Live Share Audio* y *Live Share Extension Pack*. Si queremos indagar más sobre otras extensiones de utilidad de esta herramienta podemos hacerlo desde la página [**Live Share Extension Pack**](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare-pack).  

Una vez las hayamos instalado debemos recargar la ventana del VSC. Ahora, abriremos nuestro proyecto como siempre y veremos que nos ha aparecido un nuevo símbolo en la barra lateral izquierda con forma de flecha. Si pulsamos sobre dicho símbolo nos llevará a una nueva pestaña donde podremos comenzar una sesión colaborativa iniciándola nosotros o uniéndonos a una ya existente.  

En esta ocasión inciaremos nosotros mismos una nueva sesión de colaboración, esto lo haremos pulsando el botón de *Share* o bien en la barra inferior púrpura sobre el botón de *Live Share*. Si es la primera vez que realizamos una sesión colaborativa, al pulsar sobre alguna de estas opciones nos pedirá iniciar sesión mediante una cuenta de Github o de Microsoft; elegimos la opción que más nos convenga y seguimos los pasos que nos indican sus respectivas páginas.

Habiendo iniciado sesión nos debe aparecer en el lateral izquierdo los detalles de nuestra sesión:
```
ᐯ SESSION DETAILS
  ᐯ Participants (0)
     Invite particpants...
  ᐯ Shares Servers (0)
     Share server...
  ᐯ Shared Terminals (0)
     Share terminal...
    Comments (0)
  ᐯ Audio Call (0)
     Start audio call...
```
Como podemos observar, en *Session Details* nos detalla los participantes que hay en la sesión, los servidores y terminales que estamos compartiendo, así como los comentarios que nos hayan podido hacer y la opción de comenzar una llamada de voz. Por otro lado, más abajo en la sección de *Contacts* nos da la posibilidad de invitar a que uno o más participantes se unan a esta sesión:
```
ᐯ CONTACTS
  ᐯ Recent contacts (0)
     Invite particpants...
  ᐯ Sugested contacts (0)
     null...
```
Esta sería la vista previa de una sesión colaborativa en VSCode en la que se está realizando una llamada de audio:
![Sesión colaborativa](https://raw.githubusercontent.com/ULL-ESIT-INF-DSI-2021/ull-esit-inf-dsi-20-21-prct02-vscode-Zarlie/gh-pages/img/vsc.png)


## Introducción a TypeScript 
TypeScript es un lenguaje de programación de alto nivel libre y de código abierto que implementa muchos de los mecanismos más habituales de la programación orientada a objetos; la característica fundamental es que compila en JavaScript nativo, por lo que se puede usar en todo proyecto donde se esté usando JavaScript.  
En definitiva, se trata esencialmente de un superconjunto de JavaScript que añade tipos estáticos y objetos basados en clases.

### **Primer proyecto en TypeScript** 
Antes de comenzar con nuestro primer proyecto, debemos instalar la extensión ESLint. Esta extensión nos permitirá realizar comprobaciones de estilo sobre ficheros que incluyen código fuente en JavaScript y TypeScript. Para ello, nos posicionaremos una vez más en la pestaña de extensiones en la barra lateral izquierda del VSCode, introduciremos *ESLint* en el buscador y pulsaremos en *Install*; al cabo de unos segundos estará lista para usar.  

Ahora pasaremos a instalar el compilador de TypeScript mediante el gestor de paquetes NPM (Node Package Manager) en nuestra máquina virtual; pulsamos *Ctrl + Shift + ñ* para abrir una terminal en VSC y ejecutamos el comando con la opción --global para asegurarnos de que se va a instalar el paquete de manera global:
```
[~()]$npm install --global typescript

added 1 package, and audited 2 packages in 3s

found 0 vulnerabilities
npm notice
npm notice New patch version of npm available! 7.5.3 -> 7.5.6
npm notice Changelog: https://github.com/npm/cli/releases/tag/v7.5.6
npm notice Run npm install -g npm@7.5.6 to update!
npm notice

[~()]$tsc --version
Version 4.1.5
```
Tras haber instalado el compilador de TypeScript, comenzaremos nuestro pequeño proyecto. Para ello, bajo nuestro directorio */home/usuario* crearemos una carpeta con el nombre *hello-world*. Nos posicionamos en dicho directorio y ejecutamos el comando *npm init* el cual activará la inicialización de nuestro proyecto creando el fichero *package.json* que establecerá las dependencias de desarrollo y ejecución del proyecto a modo de paquetes de los que depende el proyecto actual: 
```
[~()]$pwd
/home/usuario
[~()]$mkdir hello-world
[~()]$cd hello-world/
[~/hello-world()]$npm init --yes
Wrote to /home/usuario/hello-world/package.json:

{
  "name": "hello-world",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}

[~/hello-world()]$ls -lrtha
total 12K
drwxr-xr-x 12 usuario usuario 4,0K feb 26 01:08 ..
-rw-rw-r--  1 usuario usuario  225 feb 23 19:08 package.json
drwxrwxr-x  4 usuario usuario 4,0K feb 23 19:12 .
```
Una vez inicializado el proyecto, debemos abrirlo en nuestro espacio de trabajo de VSC para trabajar más cómodamente. Para ello, en el menú de la barra superior pulsaremos sobre *File* y luego en *Open Folder* y se deplegará un menú con los directorios de nuestra máquina virtual; buscamos el directorio *hello-world* y lo seleccionamos para así poder ver el contenido del directorio instanciado en VSCode.  

Acto seguido, en la terminal de la máquina virtual procederemos a crear el fichero *tsconfig.json* bajo el directorio *hello-world* donde especificaremos las opciones del compilador de TypeScript indicándole lo siguiente en los diversos campos:
- **Target**: Indicamos que el código que generemos sea compatible con uno de los últimos estándares de JavaScript, el *ES2018*
- **outDir**: Se indica que el directorio donde se van a colocar los archivos JavaScript, ".js", una vez transpilados sea *dist*
- **rootDir**: Especificamos dónde están los archivos fuente, con el código  TypeScript, ".ts", que debe ser traducido, en *src*
- **module**: Se establece que el estándar para cargar código desde ficheros independientes sea *CommonJS*  

```
[~/hello-world()]$touch tsconfig.json
[~/hello-world()]$cat tsconfig.json 
{
  "compilerOptions": {
    "target": "ES2018",
    "outDir": "./dist",
    "rootDir": "./src",
    "module": "CommonJS"
  }
}
```
Sólo nos queda añadir un fichero con código TypeScript, para ello primero creamos el directorio *src* y luego lo creamos en el mismo con el nombre *index.ts*:
```
[~/hello-world()]$pwd
/home/usuario/hello-world
[~/hello-world()]$mkdir src
[~/hello-world()]$cd src
[~/hello-world/src()]$touch index.ts
```
¡Ya podemos crear nuestro primer Hola Mundo en TypeScript! Esto es, abrir el fichero que acabamos de crear (index.ts) y añadir las siguientes líneas en las que simplemente creamos un string con "Hola Mundo" y lo imprimos por pantalla: 
```
let myString: string = "Hola Mundo";
console.log(myString);
```
Para compilar el código que acabamos de crear, basta con ejecutar el siguiente comando en la terminal de VSC:
```
[~/hello-world()]$tsc
```
Ejecutar la línea anterior, también habrá supuesto la creación del directorio *dist* y el fichero *index.js* automáticamente como lo habíamos indicado en pasos anteriores en las configuraciones de los ficheros *package.json* y *tsconfig.json*. Además, podemos comprobar los ficheros *./src/index.ts* y *./dist/index.js* para ver si hay alguna diferencia entre el código ".js" generado y el código ".ts" que hemos creado nosotros:
```
[~/hello-world()]$diff src/index.ts dist/index.js 
1c1
< let myString: string = "Hola Mundo";
---
> let myString = "Hola Mundo";
```
Como podemos, ver ambos códigos son prácticamente iguales, la única diferencia notable es la declaración de la variable *myString*.


Finalmente, ejecutaremos el código JavaScript generado a partir del código TypeScript:
```
[~/hello-world()]$node dist/index.js
Hola Mundo
```


## Conclusiones
La realización de esta práctica ha sido bastante fácil y llevadera puesto que ya se había trabajado durante un par de años con el editor de VSCode y sus extensiones para la realización de los diversos proyectos de las prácticas del resto de asignaturas, por lo que no se ha presentado ningún problema durante el desarrollo de la práctica.  
Cabe mencionar, que tanto las conexiones remotas con SSH o las sesiones colaborativas haciendo uso de Live Share me parecen de suma importancia en cualquier proyecto tanto profesional como personal puesto que pueden sernos de gran ayuda para afrontarlo y llevarlo a cabo satisfactoriamente.  
Por otro lado, en lo que respecta a TypeScript nunca había realizado ningún proyecto en este lenguaje de programación pero ha sido bastante intuitivo y fácil de entender, desde la sintaxis hasta la compilación del código. 


## Bibliografía
- [Guión de la Práctica](https://ull-esit-inf-dsi-2021.github.io/prct02-vscode/)
- [Visual Studio Code](https://es.wikipedia.org/wiki/Visual_Studio_Code)
- [Paquetes Snap de Ubuntu](https://www.profesionalreview.com/2016/04/21/conoce-los-paquetes-snap-ubuntu/)
- [Snap en Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-package-and-publish-a-snap-application-on-ubuntu-18-04-es#:~:text=El%20comando%20snap%20es%20equivalente,snap%20install%20snapcraft%20%2D%2Dclassic)
- [SSH](https://es.wikipedia.org/wiki/Secure_Shell)
- [VSCode Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery)
- [Remote SSH: Tips and Tricks](https://code.visualstudio.com/blogs/2019/10/03/remote-ssh-tips-and-tricks)
- [Live Share Extension Pack](https://visualstudio.microsoft.com/es/services/live-share/)
- [TypeScript](https://es.wikipedia.org/wiki/TypeScript)
- [Introducción a TypeScript](https://desarrolloweb.com/articulos/introduccion-a-typescript.html)
- [¿Qué es npm?](https://www.hostinger.es/tutoriales/que-es-npm#:~:text=Si%20ya%20tienes%20Node%20y,la%20inicializaci%C3%B3n%20de%20tu%20proyecto.&text=Este%20comando%20funciona%20como%20una,json%20de%20un%20proyecto.)
- [Configurar un proyecto para usar TypeScript](https://desarrolloweb.com/articulos/configurar-proyecto-typescript.html)
- [Diferencias entre compilación y transpilación](https://ingenieriadesoftware.es/diferencia-transpilacion-compilacion/)
