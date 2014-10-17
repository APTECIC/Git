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


  