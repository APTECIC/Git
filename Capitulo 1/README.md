# Por donde empezar 
===================

## Que es Version Control 

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


### Los 3 estados 

Esta es la parte mas importante de Git, si comprenden los estados de Git su aprendizaje para sobre el resto del material sera muy sencillo.

Git tiene principalmente 3 estados (stages) donde tus archivos pueden estar.

* Committed
* Modified
* Staged

Commited : Significan que la data esta guardad en tu base de datos local.

Modified : Significa que tu has modificado un archivo y no lo has guardado (Commited) aun.

Staged : Significa que has marcado un archivo modificado en la version actual para ser considerado para el siguiente foto.

Todos estos estados se manejan en el directorio de Git. En el directorio Git es donde el sistema guarda la metadata y los objectos de la base de datos. Esto es lo mas importante de Git y es lo que se copia cuando se clona un projecto. 

## Installar Git 



