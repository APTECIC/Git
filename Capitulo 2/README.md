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

Para pasar el archivo a la seccion Staged debemos ejecutar de nuevo la instraccion __$ git add __ (Si! , esta instruccion sirve para varios propositos). Hagamos el ejersicio, executemos un git add y un git status.

```
$ git add index.js
$ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git reset HEAD < file >..." to unstage)

	modified:   index.js
```


























  