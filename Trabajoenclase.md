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

3. 