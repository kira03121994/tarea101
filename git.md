## Fundamentos de GIT
### Comandos básicos
Aprendamos los primeros comandos con git

- git version
- git help
- git init
- git status
- git add .
- git commit -m "primer commit"
- git log

Trucos:

1. git log --oneline
2. git log --oneline --decorate --all --graph
3. git status -s

Creando alias globales

1. git config --global alias.lg "log --oneline --decorate --all --graph"
2. git config --global -e
    - git config --global -l
    - git commit -am "más comandos agregados"
        1. git commit --amend
        2. git reset --mixed f52f3da
Al texto en Markdown puedes añadirle formato como **negrita** o *