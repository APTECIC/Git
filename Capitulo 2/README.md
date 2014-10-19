#Inicializar un Repositorio Git

Para poder utilizar todos los beneficios de Git primeramente tenemos que inicializar un repositorio. Tenemos dos opciones para hacerlo, numero uno es inicializar el repositorio desde un projecto existente o directorio local he importalo a Git y numero dos es mediante una clonacion de un proyecto existente en un servidor remoto.

###Inicializar un Repositorio desde un Directorio Existente

Si tienes un projecto ya avanzado o vas a iniciar uno puedes initializar Git. Esto son los pasos:

1. Abrir la Terminal (Command en Windows)
2. Ubiquemonos dentro de la raiz del folder de nuestro projecto (__$ cd /User/< username >/Desktop/Proyecto__)
3. Ejecuta la siguiente instruccion:
```
$ git init 
```

Esta instruccion inicializa el repositorio creando el subdirectorio __.git__ que es donde se van a guardar todos los archivos necesarios para que el sistema Git funcione.

__Nota__: Cabe mencionar que en este punto ningun archivo esta siendo monitoriado, si quieres iniciar el monitoreo de archivos existentes en el direcctorio deberas agregarlos y hacer un __Commit__ inicial. (__$ git add * ; git commit -m "Primer Commit"__)

### Clonar un repositorio existente 

Si quieres obtener una copia de un repositorio ya existente (Por ejemplo un proyecto Open Source), el comando que necesitas utilizar es __$ git clone__ . Al ejecutar esta instruccion Git copiara todos los archivos de Repositorio remoto (Historia, version y mas).

La instruccion completa para clonar el repositorio es __$ git clone [url]__ . Por ejemplo si queremos copiar la documentacion de este curso lo pueden hacer con siguiente instruccion:

```
$ git clone https://github.com/APTECIC/Git.git
```

Por default , git va a crear un folder con el nombre del proyecto, pero si lo deseamos podemos cambiar el nombre del folder desde un inicio.

```git
$ git clone https://github.com/APTECIC/Git.git miCursoGit
```
Esta instruccion hace lo mismo que la anterio, pero el nombre del folder se a ser __myCursoGit__

__Nota__ : Git puede utilizar varios tipo de protocolos de transmision. En los ejemplos utilizamos el protocolo __https__ pero tambien puede utilizar __git://, http:// o usuario@servidor:/path.git__ el cual usa SSH.

#Guardar los Cambios en el Repositorio Git

El proceso y la parte mas importante que deben tener siempre presente en Git es que los archivos de tu proyecto pueden estar en dos estados __tracked (monitoreados)__ y __untracked (no-monitoreados)__ .

* Archivos Monitoreados : Son archivos que estuvieron en la ultima foto (snapshot) que se paso al repositorio Git. Estos archivos pueden estar en el estado __no modificados,  modificados y staged__.

* Archivos No-Monitoreados : Son todos los archivos que no son Monitoreados. En otras palabras archivos que no han sido marcados como rasteables (Staging) en Git.

Cada vez que se modifique un archivo monitoreado por Git. El sistema lo marca como __modificado__, por que ya es una copia diferente. Lo que el usuario tiene que hacer es pasar al __Staged__ y despues hacer un __Commit__. Este ciclo se repite una y otra vez.

<img src="git-lifecycle.png" width="600">

###Revisar el estatus de tus archivos 

La herramienta que te va ayudar a identificar en que estatus se encuentran los archivos (Untrack, Track, Modified, Staged) es la funcion __$ git status__. Despues de haber hecho nuestro primer commit o clonado un repositorio, nos va a mostrar el siguiente mensaje : 

```
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.

nothing to commit, working directory clean
```

Lo que significa es que tenemos un repositorio limpio, no hay ningun cambio y todos los archivos estan siendo monitoreados. Ahora agregemos a nuestro directorio un archivo llamado __README__ y ejecutemos de nuevo el __$ git status__.

```
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.

Untracked files:
  (use "git add < file >..." to include in what will be committed)

	README

nothing added to commit but untracked files present (use "git add" to track)
```

Como se pueden dar cuenta Git te esta notificando que el archivo que creamos __README__ esta en el estatus de __Archivo No-Monitoreado (Untracked)__. Esto significa que Git sabe que hay un archivo nuevo pero no lo va a monitorear si no se le indica explicitamente. Esto se hace como precaucion para no agregar accidentalmente archivos inecesarios.

### Monitorear los Archivos

Para poder agregar el archivo __README__ como archivo monitoreado (Tracked) necesitamos ejecutar la instruccion __$ git add__.

```
$ git add README
```

Ahora veamos que pasa si ejecutamos un __$ git status__.

```
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD < file >..." to unstage)

	new file:   README
```

Nos podemos dar cuenta que el archivo esta __Staged__ por que esta en la seccion "Changes to be committed:".

__Nota__: Si realizamos un Commit en este momento, la version del archivo al momento de haber ejecutado el __$ git add__ es la version que se va a registrar.


###Mandar a Staged archivos Modificados

Ahora que pasa cuando modificamos un archivo que Git si esta monitoreando. Por ejemplo, digamos que tenemos un archivo llamado index.js y realizamos una actualizacion al codigo. Ahora executemos un __$ git status__.

```
$ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

Changes not staged for commit:
  (use "git add < file >..." to update what will be committed)
  (use "git checkout -- < file >..." to discard changes in working directory)

	modified:   index.js
```
Nos podemos dar cuenta que el arcihvo index.js se encuentra bajo la seccion de "Changes not staged for commit:", lo cual significa que el archivo que estamos monitoreando a sido modificado pero aun no esta Staged.

Para pasar el archivo a la seccion Staged debemos ejecutar de nuevo la instraccion __$ git add__ (Si! , esta instruccion sirve para varios propositos). Hagamos el ejersicio, executemos un git add y un git status.

```
$ git add index.js
$ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git reset HEAD < file >..." to unstage)

	new file:   README
	modified:   index.js
```

###Ignorar Archivos 

Es muy comun que cuando ejecutamos nuestro codigo genere archivos que no queremos agregar a nuestro repositorio. Por ejemplo los arhicov *.log , archivos de output, archivos temporales, etc. Git nos proporciona una forma de evitar la molestia de ver este tipo de archivos en estado como no __Archivo No-Monitoreado (Untracked)__. Para esto existe el archivo __.gitignore__.

__.gitignore__ es un simple archivo de texto donde podemo especificar que tipo de archivos o nombre de archivo no queremos rastrear.

Este es un ejemplo de un archivo __.gitignore__ :

```
# es un comentario - esto es ignorado por Git
# Descarta todos los archivo que terminen con .a
*.a
# pero si monitorea el que se llame lib.a, a pesar que estoy ignorando todos los archivo .a
!lib.a
# solamente ignora el archivo TODO en el directorio raiz , pero si subdir/TODO
/TODO 
# ignora todo los archivos en el directorio build/
build/
# ignora doc/notes.txt, pero no doc/server/arch.txt
doc/*.txt
# ignora todos los .txt en el directorio doc/ 
doc/**/*.txt
```

###Visualizar tu cambios entre Staged y Non-Staged

La pregunta mas comun que un se hace es como puede ver que cambios voy a afectar entre los archivos. Es decir como vas a ver el verdadero impacto. Para esto se necesita una herramienta de comparacion y para eso Git integra la instruccion __ $ git diff__.

Esta instraccion es muy util, nos ayuda a indetificar los cambios y evitar error al momento de hacer un commit. Por ejemplo, vamos a agregar una line a nuestro archivo de __README__.
```
$ git diff
diff --git a/README b/README
index e69de29..a19abfe 100644
--- a/README
+++ b/README
@@ -0,0 +1 @@
+Hola
```

Como pueden ver la instruccion diff por si solo nos arroja la comparacion entre el archivo __a__ (el cual es el de repositorio) y el archivo __b__(el cual es el que modificamos). Como se pueden dar cuenta es muy claro que agregamos la palabra "Hola" al archivo.

Ahora supongamos que agregamos el archivo a la seccion de __Staged__. Y agremamos agregamos otro mensaje a nuestro archivo README.

```
$ git add README
$ echo "Hola de nuevo" >> README
$ cat README
Hola
Hola de nuevo

```

Si executamos la instruccion __$ git diff__ , nos va a mostrar los cambios entre el archivo en estatus modificado y la ultima foto en el repositorio. Pero que pasa si queremos comparar el archivo __Staged__ y el ultimo __Commit__. Para lograr esto necesitamos utilizar la instruccion __$ git diff --cached__ o __$ git diff --staged__ (la opcion --staged esta activa a partir de la version 1.6.1 de Git). A continuacion mostramos la diferencia entre los dos diff para un mejor entendimiento.

* __$ git diff__ :
```
$ git diff
diff --git a/README b/README
index a19abfe..4b9dea0 100644
--- a/README
+++ b/README
@@ -1 +1,2 @@
 Hola
+Hola de nuevo

```

* __$ git diff --staged__ :
```
$ git diff --staged
diff --git a/README b/README
index e69de29..a19abfe 100644
--- a/README
+++ b/README
@@ -0,0 +1 @@
+Hola
```
###Vamos a hacer Commits !!

Ahora que ya tenemos archivos localizados en el zona Staged, podemos proceder a guardar nuestros cambios en Git con un commit.Es importante mencionar que todos los archivos modificados o actualizados que no hallan pasado por un __$ git add__ no va a ser registrado en Git. Siempre es recomendable revisar el estado de tus archivo con un __$ git status__ para estar seguro que es lo que vamos a guardar. La forma mas ejecutar un Commit es de la siguiente manera : 

```
$ git commit -m < mensaje >
```

Cada commit debe ir acompañado de un mensaje claro especificando que cambios se han guardad, por lo regular se meneja en terminos de Bug fix o addiciones.Vamos a agregar un commit inicial.

```
$ git commit -m "Agregando archivos README y index.js"
[master 383c80f] Agregando archivos README y index.js
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README
 create mode 100644 index.js
```
Como pueden ver una vez finalizado el Commit, nos da informacion sobre el si mismo. Como por ejemplo en que branch (master) y el SHA-1 generado (393c80f), cuantos archivos fueron agregados y informacion adicional.

__Nota:__ Hay que siempre tener en cuenta que los Commits toman una foto (snapshot) de los archivos que estan en la seccion de Staged. 


























  