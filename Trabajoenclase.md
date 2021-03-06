#Anexo
###Preguntas y respuestas

1. ¿Como puedo deshacer el ultimo commit?
>Si quieres mantener los cambios:
git reset [--mixed] HEAD~1

>Si además no quieres cargarte el commit (sólo mover el head al anterior):
git reset --soft HEAD~1

Y si no quieres mantenerlos (y volver al estado del commit anterior, en la práctica, destruir el último commit completamente como si nunca hubiera existido):
>git reset --hard HEAD~1

2. ¿Cuál es la diferencia entre pull y fetch en git?
>De la documentación:
git pull is shorthand for git fetch followed de git merge FETCH_HEAD.

>o haciendo una traducción libre:
git pull es una abreviación de git fetch seguido de git merge FETCH_HEAD.

Es decir, **git fetch trae los cambios, pero los deja en otro branch, hasta que se hace el git merge para traerlos al branch local**.

3. ¿Cómo cambiar el mensaje de un commit?
>Acabo de hacer un commit:
git commit -m "este es un comentario"
>Si vuelvo a escribir git commit -m "un nuevo comentario" hará otro commit en lugar de modificar el que ya hice.

4. ¿Como regresar un repositorio a un commit especifico?
>Sólo debes hacer *git checkout commitC* donde **commitC** es el hash de dicho commit.

Ejemplo:

Buscas en el log de git cuál es el commit al que quieres regresar:

**git log**

5. ¿Cómo revertir un commit, si ya subí los cambios al origen?

>Tienes que hacer de nuevo el comit, para eso puedes ver cómo acá, luego tienes que hacer *push* forzando tu versión:

**git push -f origin master**

6. ¿Cómo ignorar los cambios de permisos en git (chmod)?

>Para ignorar los cambios de permisos en git, se realiza con:

**% git config core.file Mode false**

7. ¿Como volver commit anterior?
 
 >Puedes volver a una revisión antigua usando checkout y pasando el hash del commit. Por ejemplo:

**git checkout ab25f1ln2b4o3a9c4u1v6k4n1m7 **
>No olvidar el punto al final. 
También puedes descartar cambios mediante reset pasándole el numero de commits. Por ejemplo, para descartar los últimos 3 commits:
**git reset --hard HEAD~3**

La diferencia entre checkout y reset es que en éste último se descartan las revisiones, mientras que con checkout se preservan.

8. ¿Cuál es la diferencia entre 'git rebase' y 'git merge'?

>Cuando haces git **rebase**:

Los commits locales se eliminan de la rama temporalmente.
-se ejecuta un **git pull**.
-los commits locales se insertan nuevamente.
-Esto quiere decir que todos tus commits locales aparecen al final, después de los commits remotos. 

Esto es, si haces git log, los commits de la rama que has rebasado aparecen como si fueran más antiguos, independientemente de cuándo se hicieran

>Supongamos que tienes 3 commits A,B,C:
![alt tag](https://i.stack.imgur.com/lJRq7.png)

>Entonces viene Daniel y crea un commit D. Luego Enrique crea un commit E:
![alt tag](https://i.stack.imgur.com/pK7Zb.png)

>Obviamente, este conflicto debe ser resuelto de alguna forma. Para ello hay dos maneras:

***MERGE:***
![alt tag](https://i.stack.imgur.com/9Ul5w.png)

Ambos commits D y E aún están allí, pero creamos un commit de unión (merge commit) M que hereda los cambios de ambos commits D y E. Sin embargo, esto crea la estructura en forma de diamante, que a mucha gente confunde.

***REBASE:***
![alt tag](https://i.stack.imgur.com/TvXuJ.png)

Creamos un commit R, cuyo contenido es idéntico al del commit M descrito arriba. Sin embargo, nos cargamos el commit E como si nunca hubiera existido (se ve con los puntitos, en la línea evanescente). De acuerdo con esta anulación, E debería ser un commit local de Enrique y no debería haber hecho push a ningún repositorio. La ventaja de este método es que se evita la forma de diamante y el historial permanece lineal, que es algo que la mayoría de los desarrolladores agradecen.

9. ¿Cómo ver qué archivos son diferentes entre 2 ramas con Git?

>Básicamente el comando para ver las diferencias entre dos branches es:

**$ git diff branch1..branch2**

>Para listar qué archivos han cambiado entre dos branches puedes usar:

**$ git diff --name-status branch1..branch2**




10. ¿Cómo averiguar la procedencia de una rama determinada?

Haz un checkout a la rama en cuestión y luego ejecuta:

**git log --oneline --decorate --all --graph**