# Contribuciones

Usamos el siguiente comando para ver las ramas existentes

-git branch

En primer lugar nos situamos en la rama adecuada con el comando (La primera vez que lo usemos deberiamos hacer un checkout a master)

-git checkout nombrerama

Si tenemos que crear una rama, usaremos el comando

-git checkout -b nombrerama

Cuando estemos en la rama, deberemos actualizar su contenido, haciendo un pull de lo que contenga

-git pull origin nombrerama

Una vez esté la rama con la última versión, podemos modificar nuestro repositorio local.

Antes de subir los cambios, es conveniente usar el siguiente comando para ver los ficheros que hemos tocado con el comando:

-git status

Nos saldrá un listado de ficheros, para ver concretamente lo que hemos cambiado en cada fichero, usaremos el comando:

-git diff nombrefichero

Una vez que estemos seguros de que los cambios realizados son correctos, procederemos a hacer el commit con su descripción

-git add nombrefichero 
o
-git add . (para todos los archivos a la vez)

(Se pueden añadir varios ficheros al mismo commit, por lo que podemos usar varias veces el git add)

Cuando estén todos en la pila de subida, haremos el commit

-git commit -m "descripcion" (La descripcion debe ser clara e indicar la funcionalidad o cambio que estamos haciendo)

Y para finalizar:

-git push origin nombrerama (En la que estás situado)


**Escribe tu nombre en una linea:**

Fran 🥐 

Adrián

Santi

 





