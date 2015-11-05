
##Que es Version Control

Que es version control y por que deberia de interesarles ?. Version Cotrol es un sistema que registra cambios en un archivo o un conjunto archivos atravez del timepo.

Si eres un programador , diseñador web o escritor y te interesa tener versiones de tus layout, codigo o documento; Un sistema de version control es lo mas sano utilizar. Con Version Control podras facilmente revertir cambios , nombrar versiones y saber a detalles que cambios se han hecho.

## La Historia de Git

Linux Kernel es un projecto Open-Source de un enorme alacance. Desde el inicio de mantenimiento del Kernel (1991 - 2002), los cambios hechos al software eran pasado como parches y folders comprimidos. En 2002, el projecto empezo a utilizar el software BitKeeper creado por la empeza DVCS.

En 2005, la relacion entre la comunidad que desarrollaba el Linux Kernel y BitKeeper termino en muy malos terminos. Esto obligo a la comunidad (mayormente empujado por Linus Torvalds) a desarrollar un nuevo sistema de version control. Algunos objectivos de este nuevo sistema fueron los siguientes:

1. Velicidad
2. Diseño simple
3. Gran soporte para desarrollo no-lineares
4. Cien porciento distribuido

Desde el 2005, Git ha evolucionado y madurado, y aun conserva todas la caracteristicas que se establecieron en un inicio.

## Ventajas de Git

1. Utiliza un sistema de Snapshots:
2. Todas las operaciones en Git son locales
3. Git tiene integridad (todas las operaciones hace check-summed , SHA-1)


## Los 3 estados (Commited, Modified, Staged)

Esta es la parte mas importante de Git, si comprenden los estados de Git su aprendizaje para sobre el resto del material sera muy sencillo.

Git tiene principalmente 3 estados (stages) donde tus archivos pueden estar.

* Committed
* Modified
* Staged

__Commited__ : Significan que la data esta guardada en tu base de datos local.

__Modified__ : Significa que tu has modificado un archivo y no lo has guardado (Commited) aun.

__Staged__ : Significa que has marcado un archivo modificado en la version actual para ser considerado para el siguiente foto.

<img src="Operacion_Locales.png" width="450">

Todos estos estados se manejan en el directorio de Git. En el directorio Git es donde el sistema guarda la metadata y los objectos de la base de datos. Esto es lo mas importante de Git y es lo que se copia cuando se clona un projecto.

## Installar Git

Ahora que entendemos los beneficios de Git y su estructura. A continuacion te vamos a mostrar los pasos para installar Git. Nosotros vamos a mostrar el proceso de installacion para los sistemas operativos mas populares (OS X, Linux, Windows).

Si por alguna razon quieren realizar una installacion desde el codigo fuente lo pueden descargar de la pagina de GitHub [https://github.com/git/git](https://github.com/git/git)

###Instalacion en Linux

Para installar en Linux es bien sencillo a travez del "Package Manager":

__Debian/Ubuntu__
```
$ apt-get install git
```

__Fedora__
```
$ yum install git
```

__Gentoo__
```
$ emerge --ask --verbose dev-vcs/git
```

__Arch Linux__
```
$ pacman -S git
```

__openSUSE__
```
$ zypper install git
```

__FreeBSD__
```
$ cd /usr/ports/devel/git
$ make install
```

__Solaris 11 Express__
```
$ pkg install developer/versioning/git
```

__OpenBSD__
```
$ pkg_add git
```
__Nota__: Por default la opcion de auto-completar no esta habilitada. Pera resolver este problema puede usar lo pasos que se encuentran en el siguiente link : [http:blog.jacovarrubias.com](http://blog.jacovarrubias.com/post/99660637170/how-to-add-auto-completion-to-git)


###Instalacion en OS X

Para usuario de la pueden hacer su installacion desde el Codigo Fuente o pueden descargalo desde el siguiente URL [http://git-scm.com/download/mac](http://git-scm.com/download/mac).

Otra opcion es usando [MacPorts](http://www.macports.org).

```
$sudo port install git-core
```

__Nota__: Por default la opcion de auto-completar no esta habilitada. Pera resolver este problema puede usar lo pasos que se encuentran en el siguiente link : [http:blog.jacovarrubias.com](http://blog.jacovarrubias.com/post/99660637170/how-to-add-auto-completion-to-git)

###Instalacion en Windows

Para usuarios de Windows pueden descargar en installador desde la pagina de [http://git-scm.com/download/win](http://git-scm.com/download/win).


###Probar git

Para asegurarse que git a sido installado appropiadamente. Abran un ventana de linea commando (Terminal para Unix o para Window git-shell). Escriban la siguiente sentencia

```
$ git --version
```

Como respuesta les debe de mostrar la version de su instalacion de Git. Y asi se aseguran que Git esta installado correctamente.

## Configuracion de Git

Ahora que ya tenemos instalado git tenemos que realizar un pequeño setup. Esta configuracion solamente la tienes que hacer una vez, estos cambios se conservan a pesar de las actualizaciones que hagas de Git en el futuro y puedes cambiar la configuracion en cualquier momento.

Git viene con una herramienta llamado __git config__ que permite configurar variables que controlan como opera y se visualiza git. Estas variables se pueden almazenar en 3 diferentes lugares:

* __/etc/gitconfig__ : Contiene variables para cada usuario en el systema y todos los repositorios. Si pasas la opcion the __--system__ escribira las variables en el archivo de configuracion.

__Nota__ : En Windows seria "C:\Program Files\Git\etc\gitconfig"

```
$ git config --system [opcion]
```

* __~/.gitconfig__ : Este archivo contiene variables a nivel de usuario. Si pasas la opcion the __--global__ escribira las variables en el archivo de configuracion.

__Nota__: Para sistemas Windows, Git busca por el archivo __.gitconfig__ en el path $HOME (C:\Document and Settings\$USER).

```
$ git config --global [opcion]
```

* Archivo de configuracion a nivel repositorio (nombre_proyecto/.git/config), este archivo se crea para cada repositorio.

###Configurar tu identidad

Lo primero que se tiene que configurar es tu identidad en Git (nombre y correo electronico). Esto es importante por que en cada Git Commit utiliza esta informacion, y es inmutable cuando compartes los Commits:

```
$ git config --global user.name "Nombre Apellido"
$ git config --global user.email "mycorreo@domain.com"
```

###Configurar el Editor para Git

Git necesita tener configurado un editor de Texto por default en caso de que Git requiera que escribas un mensaje. Para configurar puedes usar una de las opciones que mostramos a continuacion:

```
[Para Windows]
$ git config --global core.editor "notepad.exe"
[Para Unix OS]
$ git config --global core.editor "nano"
$ git config --global core.editor "vim"
$ git config --global core.editor "emacs"
```

###Configurar Git para que use Colores

Si no te gusta ver informacion monocromatica en tu terminal puedes configurar Git para que te muestre su informacion en colores. Esto es realmente util para identificar rapidamente en que estado se encuentra nuestros archivos.

```
$ git config --global color.ui true
```

###Revisar las variables

Para ver tu configuracion puede usar esta instruccion :
```
$ git config --list
```
o puedes verlo a nivel variable (__git config {key}__):
```
$ git config user.name
```

##Manual de Ayuda

Para obtener ayuda en como usar Git, siempre esta disponible la instruccion __git help < verb >__ para ver documentacion.

```
$ git help config
```
