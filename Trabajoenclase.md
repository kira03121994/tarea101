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

