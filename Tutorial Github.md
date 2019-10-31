# Cómo trabajar con git en este repositorio

En este documento se explica cómo usar git y github a los que
nunca lo hayan usado así como la metodología que vamos a
seguir y un resumen de los comandos más interesantes.  
Si ya sabes cómo funciona git con github, solo tienes que
leerte el método con el que tienes que trabajar con el
repositorio.

## Contenidos

- [Cómo trabajar con git en este repositorio](#c%c3%b3mo-trabajar-con-git-en-este-repositorio)
  - [Contenidos](#contenidos)
  - [Requisitos](#requisitos)
  - [Principios básicos de git](#principios-b%c3%a1sicos-de-git)
    - [Clonar el repositorio y comenzar a hacer cambios](#clonar-el-repositorio-y-comenzar-a-hacer-cambios)
    - [Trabajar con un repositorio remoto](#trabajar-con-un-repositorio-remoto)
  - [Cómo vamos a trabajar en este proyecto](#c%c3%b3mo-vamos-a-trabajar-en-este-proyecto)
  - [Resumen de comandos](#resumen-de-comandos)
    - [Clonar un repositorio](#clonar-un-repositorio)
    - [Ver todas las ramas](#ver-todas-las-ramas)
    - [Cambiar a otra rama](#cambiar-a-otra-rama)
    - [Crear y cambiar a otra rama](#crear-y-cambiar-a-otra-rama)
    - [Ver el estado del repositorio](#ver-el-estado-del-repositorio)
    - [Añadir cambios al stage](#a%c3%b1adir-cambios-al-stage)
    - [Añadir todos los cambios al stage](#a%c3%b1adir-todos-los-cambios-al-stage)
    - [Crear un commit con los cambios en el stage](#crear-un-commit-con-los-cambios-en-el-stage)
    - [Actualizar repositorio local desde remoto](#actualizar-repositorio-local-desde-remoto)
    - [Subir cambios al remoto de la rama local](#subir-cambios-al-remoto-de-la-rama-local)
    - [Ver el log de commits del repositorio](#ver-el-log-de-commits-del-repositorio)

## Requisitos

* Es necesario tener instalado git. Podemos comprobar que funciona
con el comando `git --version`, y asi ver la versión que tenemos.

* Tener git configurado. Haciendo lo que dice [aqui](https://git-scm.com/book/es/v1/Empezando-Configurando-Git-por-primera-vez). Lo necesario es
mail y nombre, el resto si queréis. Usad por favor
el mismo mail que en github.

Además podemos tener alguna interfaz gráfica para interactuar
con git, hay varias, no se van a explicar aqui y cuidado con
ellas que es fácil liarla.

## Principios básicos de git

### Clonar el repositorio y comenzar a hacer cambios

El primer paso es clonar el repositorio en nuestro ordenador, es decir,
descargarlo.

Lo hacemos con `git clone <URL de github>`. La URL la podemos copiar del botón verde del respositorio que pone _"Clone or Download"_.

Ahora se habrá creado una carpeta con el nombre del repositorio con todo el contenido de la rama _master_.

En un repostorio de git existen varias ramas sobre las que
cada equipo trabajará. Para ver todas las ramas podemos usar
`git branch`, si usamos el flag `-a` veremos tanto las
locales como las que estan en remoto. También podemos ver
las ramas existentes en el github, que hay un menú desplegable
con todas las ramas.

Ahora tenemos que elegir la rama en la que vamos a trabajar.
**NUNCA VAMOS A TRABAJAR DIRECTAMENTE EN LA RAMA MASTER**,
espero que quede claro. Por defecto estamos en la rama master,
para cambiar a otra rama, usamos el comando `git checkout <nombre de la rama>`.
Si usamos el flag `-b` creamos la rama
si no existe. Si usamos el flag `-B` creamos la rama si no
existe, y si existe la reseteamos, es decir cuidado. **La rama la crearemos a partir de la rama donde estemos**, así que
si tenéis que crear una rama nueva, aseguraos que estáis donde tenéis que estar, sea por ejemplo la rama de frontend,
por ejemplo, o cual sea.

Una vez estamos en nuestra rama de trabajo, es posible que los
ficheros del directorio hayan cambiado, es normal. Ahora
podemos editar ficheros o crear nuevos según lo que requiera
nuestra tarea.  
En git existen dos lugares (que se vayan a explicar aquí) para los cambios: _staged_ o no. El comando `git status` nos dirá información de: la rama
actual, los cambios _staged_ y sin incluir, y si estamos al día con el repositorio remoto.

Ahora es momento de introducir el concepto de _commit_. Un _commit_ es un conjunto de cambios (en principio) inmutable y
que van a quedar registrados en la historia del proyecto. En
la medida que se pueda, un _commit_ ha de ser una **unidad de
cambios**. Es decir, que sea un método que funcione, un conjunto de cambios que arreglen un error, etc.. Que no sea
un metodo a medias, ni 600 lineas de código.

El _stage_ es la zona donde podemos ver los cambios que
estamos agregando a nuestro siguiente "paquetito" de cambios, nuestro
_commit_. Para agregar el fichero cambiado/creado al _stage_
usamos el comando `git add <nombre del fichero>`. En lugar del
nombre podemos poner un `.`, y se agregarán al _stage_ todos
los cambios.  
Ahora podemos ver con `git status` los cambios que hemos
añadido.

>Ahora conviene realizar un `git pull`, explicación en el
siguiente punto

Cuando hayamos terminado de agregar al _stage_ los cambios que
queramos incluir en un _commit_, podemos realizar este commit
con `git commit -m <mensaje descriptivo>`. Es importante
incluir mensajes descriptivos y concisos a nuestro commit. Algunos ejemplos pueden ser: "Añadida autenticación de
usuario", o "Arreglado error #14", para referir a un error de
github. Es posible agregar mensajes más detallados a parte de
este, que es como el "título" del commit, pero no se entrarán
en esos detalles.

### Trabajar con un repositorio remoto

En este momento hemos obtenido el código, realizado cambios y
los hemos registrado. Ahora tenemos que subir estos cambios.
Debido a que estamos trabajando con más gente, nos conviene
comprobar si alguien ha hecho cambios en nuestra rama, en el
mismo fichero que nosotros, sobre las mismas líneas que
nosotros, ya que esto puede ser un problema.  
Obviamente, si nosotros creamos la rama como antes se explicó,
y todavía no hemos publicado nada, nadie habrá hecho cambios
así que no hace falta tener cuidado en esto.

Para descargar los cambios de la rama actual, desde un remoto
usamos el comando `git pull`. Podemos especificar también la
rama con `git pull <remoto> <rama>`. El remoto es un nombre
identificativo de el repositorio remoto, si habéis seguido
este documento, por defecto se llama `origin`.

>Es posible que surjan conflictos con los cambios realizados
si hay más programadores realizando commits en la misma rama.
No se va a explicar cómo solucionar conflictos, ya que puede
ser muy lioso si no hay un ejemplo. Si os surgen y no sabéis
solucionarlos, contactad con alguien que sepa del tema o el
inmediato superior.

Ahora que tenemos nuestra rama actualizada, podemos subir los cambios con `git push <remoto> <rama>` donde, como antes, remoto por defecto es `origin`.  
Si la rama la hemos creado nosotros, para publicarla al remoto
por primera vez, necesitamos añadirla con la opción `--set-upstream`, quedándonos el comando, `git push --set-upstream <remoto> <rama>`.

En este caso no tendréis que hacerlo, porque se encargarán los
administradores del repositorio, pero en otro proyecto que
trabajéis, para unir las ramas tendréis que hacer un pull
request en github, para solicitar unir vuestro trabajo a la rama principal.

## Cómo vamos a trabajar en este proyecto

Seguiremos el siguiente plan de trabajo:

* [Situarnos en la rama](#cambiar-a-otra-rama) sobre la que vamos a trabajar.
  * Si no sabemos cuál es, preguntar a un superior.
* [Crear una rama](#crear-y-cambiar-a-otra-rama) para realizar cambios o trabajar en nuevas características.
  * Podemos tambien ir a trabajar a la rama de otro compañero si lo hablamos, para evitar conflictos indeseados.
* Realizar nuesra tarea.
  * Podemos realizar varios _commits_, que sean unidades de cambios/características con sentido independiente unos de otros, no hacer _commits_ por hacerlos.
  * Realizar solo la tarea. Aunque veamos otros errores, o creamos que algo se deba cambiar, hacer la tarea que tenemos asignada. En caso de que veamos algo mal, abrir un _issue_ en github comentándolo.
* Realizar un [pull](#actualizar-repositorio-local-desde-remoto) de nuestra rama si estamos trabajando con alguien más.

> Podemos hacer varios _push_ de nuestra rama, no tiene por qué ser cuando hayamos terminado la tarea.

* [Hacer un push](#subir-cambios-al-remoto-de-la-rama-local)  de nuestros cambios al repositorio en github
  * Si la rama es nueva, recordad que hay que modificar el comando.

## Resumen de comandos

### Clonar un repositorio

`git clone <link>`

### Ver todas las ramas

`git branch -a`

### Cambiar a otra rama

`git checkout <nombre rama>`

### Crear y cambiar a otra rama

Se creará como rama de la rama actual.

`git checkout -b <nombre rama>`

### Ver el estado del repositorio

`git status`

### Añadir cambios al stage

`git add <nombre del fichero>`

### Añadir todos los cambios al stage

`git add .`

### Crear un commit con los cambios en el stage

`git commit -m <mensaje descriptivo>`

### Actualizar repositorio local desde remoto

De una rama del remoto con el mismo nombre a la actual:  
`git pull`

De una rama en concreto del remoto, a la actual:  
`git pull <remoto> <nombre rama>`

### Subir cambios al remoto de la rama local

Si la rama existe en el remoto:  
`git push <remoto> <nombre rama>`

Si la rama **NO** existe en el remoto:  
`git push --set-upstream <remoto> <nombre rama>`

### Ver el log de commits del repositorio

`git log`

Podemos ver tambien el "arbol" de ramas con:  
`git log --graph --all`