# git-work
# git-work - flujo colaborativo con git

Repositorio de práctica del flujo colaborativo (fork,issue,rama,PR,conflicto,etiqueta y realease) del módulo DPL.

## Índice

- [Entorno e instalación](#entorno-e-instalacion)
- [Configuración](#configuracion)
- [Comprobación](#comprobacion)
- [Problemas encontrados y solución](#problemas-encontrados-y-solucion)
- [Repositorio remoto](#repositorio-remoto)

## Entorno e instalación
Paso 1
Se crean dos usuarios en git, el usuario1 "Raluido" y el usuario2 "raluidotest" para facilitar las pruebas, siendo ésta manera la que se ajusta totalmente a un caso real, evitando así los problemas encontrados cuando se realizó mediante el modo "espejo". Uno de los problemas fue que no se consiguió cerrar la issue del paso 8 porque no la detectaba.
Se crea el repositorio git-work con el usuario1 y se clona. 

Paso 2
Se añade el "index.html" y el css/cover.css", además del .gitignore y se pushean al main del usuario1.

Paso 3
Se añaden los ficheros del workflow para que se construya la documentación con cada push.

Paso 4
Se crea la issue #1 con el usuario1 "Add custom text for startup" desde la web.

Paso 5
Desde la cuenta del usuario2 en github se busca el repositorio público del user 1, se realiza el fork y se hace el clonado.

Paso 6
Se crea una rama nueva "custom-text" con el usuario2 y se realizan cambios en el fork.
Se crea el PR apuntando al usuario1.

Paso 7
Se traen los cambios realizados por el usuario 2 y se plantean mejoras. Notamos que el PR tiene valor #2.
Se continua la conversación y se hacen mas cambios.

Paso 8
Se revisa el PR y da error.
Se mergea y se borra la rama que ya no vamos a necesitar.
Usuario2 sincroniza su repositorio.

Paso 9
Se crea una nueva Issue con el usuario1.
Se realiza un cambio en local sin subirse al remoto.

Paso 10
El usuario2 cambia la misma línea que el usuario1 en el paso anterior pero subiendolo a main.
Se crea un PR y se relaciona con la Issue creada anteriormente #3.

Paso 11
El usuario1 se trae los cambios de main y salta en conflicto tras haber modificado la misma línea.
Se resuelve el conflicto, se suben los cambios apuntando a la Issue y se cierra el PR.

Paso 12
Se edita ahora la línea 11 se suben los cambios y se cierra la Issue.

Paso 13
Se crea el tag que apuntará a todos los cambios realizados hasta ahora.
Se crea la release.


## Configuración
Inicialmente no utilizamos el comando "gh" sino que se realiza desde la web.

## Comprobación
Paso 1
```bash
alumno@37016ff2f098:~/dpl$ git clone https://github.com/raluidotest/git-work.git ae1-user2
Cloning into 'ae1-user2'...
remote: Enumerating objects: 17, done.
remote: Counting objects: 100% (17/17), done.
remote: Compressing objects: 100% (10/10), done.
remote: Total 17 (delta 1), reused 13 (delta 1), pack-reused 0 (from 0)
Receiving objects: 100% (17/17), done.
Resolving deltas: 100% (1/1), done.
alumno@37016ff2f098:~/dpl$ cd ae1-user2/
alumno@37016ff2f098:~/dpl/ae1-user2$ git config --local user.name "Raluido Test"
alumno@37016ff2f098:~/dpl/ae1-user2$ git config --local user.email "raluido.test@gmail.com"
alumno@37016ff2f098:~/dpl/ae1$ git config --local --list
core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
remote.origin.url=https://github.com/Raluido/git-work.git
remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
remote.origin.gh-resolved=base
branch.main.remote=origin
branch.main.merge=refs/heads/main
user.name=Raúl Luis
user.email=raluido@gmail.com
alumno@37016ff2f098:~/dpl/ae1$ git remote -v
origin	https://github.com/Raluido/git-work.git (fetch)
origin	https://github.com/Raluido/git-work.git (push)
```

Paso 2
```bash
alumno@37016ff2f098:~/dpl/ae1$ git add index.html css/cover.css .gitignore
alumno@37016ff2f098:~/dpl/ae1$ git commit -m "Añade documentación con MkDocs e integración continua" -m "Workflow que construye el sitio con mkdocs build --strict en cada push y pull request; la portada enlaza al sitio y al repositorio remoto."
 3 file changed, 0 insertion(+), 0 deletion(-)
alumno@37016ff2f098:~/dpl/ae1$ git push origin main
Enumerating objects: 16, done.
Counting objects: 100% (16/16), done.
Delta compression using up to 4 threads
Compressing objects: 100% (10/10), done.
Writing objects: 100% (13/13), 1.42 KiB | 729.00 KiB/s, done.
Total 13 (delta 6), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (6/6), completed with 2 local objects.
To https://github.com/Raluido/git-work.git
   52e3dda..b88ee19  main -> main
```

Paso 3
```bash
alumno@37016ff2f098:~/dpl/ae1$ git add .github/workflows/ci.yml mkdocs.yml docs/index.md
alumno@37016ff2f098:~/dpl/ae1$ git commit -m "Añade documentación con MkDocs e integración continua" -m "Workflow que construye el sitio con mkdocs build --strict en cada push y pull request; la portada enlaza al sitio y al repositorio remoto."
 3 file changed, 0 insertion(+), 0 deletion(-)
alumno@37016ff2f098:~/dpl/ae1$ git push origin main
Enumerating objects: 16, done.
Counting objects: 100% (16/16), done.
Delta compression using up to 4 threads
Compressing objects: 100% (10/10), done.
Writing objects: 100% (13/13), 1.42 KiB | 729.00 KiB/s, done.
Total 13 (delta 6), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (6/6), completed with 2 local objects.
To https://github.com/Raluido/git-work.git
   52e3dda..b88ee19  main -> main
```

Paso 5
```bash
alumno@37016ff2f098:~/dpl/ae1-user2$ git clone git@github.com:USUARIO_USER2/git-work.git ae1-user2
Cloning into 'ae1-user2'...
remote: Enumerating objects: 12, done.
remote: Counting objects: 100% (12/12), done.
remote: Compressing objects: 100% (8/8), done.
remote: Total 12 (delta 3), reused 9 (delta 2), pack-reused 0
Receiving objects: 100% (12/12), done.
Resolving deltas: 100% (3/3), done.
alumno@37016ff2f098:~/dpl/ae1-user2$ cd ae1-user2
alumno@37016ff2f098:~/dpl/ae1-user2/ae1-user2$ git remote -v
origin	git@github.com:USUARIO_USER2/git-work.git (fetch)
origin	git@github.com:USUARIO_USER2/git-work.git (push)
upstream	https://github.com/Raluido/git-work.git (fetch)
upstream	https://github.com/Raluido/git-work.git (push)
```

Paso 6

```bash
alumno@37016ff2f098:~/dpl/ae1-user2$ nano index.html 
alumno@37016ff2f098:~/dpl/ae1-user2$ git add index.html
git commit -m "Personaliza la portada para la startup" \
           -m "Sustituye el texto genérico por el nombre, el eslogan y la propuesta de valor de la startup."
git push -u origin custom-text
[custom-text 4f07fd9] Personaliza la portada para la startup
 1 file changed, 3 insertions(+), 3 deletions(-)
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 426 bytes | 426.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/raluidotest/git-work.git
 ! [remote rejected] custom-text -> custom-text (permission denied)
error: failed to push some refs to 'https://github.com/raluidotest/git-work.git'
```

Paso 7
```bash
alumno@37016ff2f098:~/dpl/ae1$ gh pr checkout 2
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (1/1), done.
remote: Total 3 (delta 2), reused 3 (delta 2), pack-reused 0 (from 0)
Unpacking objects: 100% (3/3), 406 bytes | 50.00 KiB/s, done.
From https://github.com/Raluido/git-work
 * [new ref]         refs/pull/2/head -> custom-text
Switched to branch 'custom-text'
alumno@37016ff2f098:~/dpl/ae1$ nano index.html
alumno@37016ff2f098:~/dpl/ae1$ nano index.html
alumno@37016ff2f098:~/dpl/ae1$ git add index.html
alumno@37016ff2f098:~/dpl/ae1$ git commit -m "Ajusta el texto del pie de página" -m "Mejora la redacción del pie propuesta en la revisión del PR #1."
[custom-text 69f6a2d] Ajusta el texto del pie de página
 1 file changed, 1 insertion(+), 1 deletion(-)
alumno@37016ff2f098:~/dpl/ae1$ git push upstream custom-text
fatal: 'upstream' does not appear to be a git repository
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
alumno@37016ff2f098:~/dpl/ae1$ git remote -v
origin	https://github.com/Raluido/git-work.git (fetch)
origin	https://github.com/Raluido/git-work.git (push)
alumno@37016ff2f098:~/dpl/ae1$ git add ^C
alumno@37016ff2f098:~/dpl/ae1$ git remote add upstream https://github.com/raluidotest/git-work.git
alumno@37016ff2f098:~/dpl/ae1$ git push upstream custom-text
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 366 bytes | 366.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/raluidotest/git-work.git
 ! [remote rejected] custom-text -> custom-text (permission denied)
error: failed to push some refs to 'https://github.com/raluidotest/git-work.git'
alumno@37016ff2f098:~/dpl/ae1$ git remote set-url upstream https://TOKEN@github.com/raluidotest/git-work.git
alumno@37016ff2f098:~/dpl/ae1$ git push upstream custom-text
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 366 bytes | 366.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/raluidotest/git-work.git
   4f07fd9..69f6a2d  custom-text -> custom-text
   alumno@37016ff2f098:~/dpl/ae1$ gh pr comment 2 --body "He ajustado el pie; ¿puedes revisar el slogan?"
X No default remote repository has been set. To learn more about the default repository, run: gh repo set-default --help

please run `gh repo set-default` to select a default remote repository.
alumno@37016ff2f098:~/dpl/ae1$ gh repo set-default
This command sets the default remote repository to use when querying the
GitHub API for the locally cloned repository.

gh uses the default repository for things like:

 - viewing and creating pull requests
 - viewing and creating issues
 - viewing and creating releases
 - working with GitHub Actions

### NOTE: gh does not use the default repository for managing repository and environment secrets.

? Which repository should be the default? Raluido/git-work
✓ Set Raluido/git-work as the default repository for the current directory
alumno@37016ff2f098:~/dpl/ae1$ gh pr comment 2 --body "He ajustado el pie; ¿puedes revisar el slogan?"
https://github.com/Raluido/git-work/pull/2#issuecomment-5979341673

alumno@37016ff2f098:~/dpl/ae1-user2$ git add index.html && git commit -m "Afina el eslogan de la portada" -m "Atiende el comentario de la revisión."
[custom-text 7f0b4e3] Afina el eslogan de la portada
 1 file changed, 1 insertion(+)
alumno@37016ff2f098:~/dpl/ae1-user2$ git push origin custom-text
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 359 bytes | 359.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/raluidotest/git-work.git
   69f6a2d..7f0b4e3  custom-text -> custom-text

```

Paso 8
```bash
alumno@37016ff2f098:~/dpl/ae1$ gh pr review 1 --approve --body "Revisado y probado en local."
GraphQL: Could not resolve to a PullRequest with the number of 1. (repository.pullRequest)
alumno@37016ff2f098:~/dpl/ae1$ gh pr review 2 --approve --body "Revisado y probado en local."
failed to create review: GraphQL: Review Can not approve your own pull request (addPullRequestReview)
alumno@37016ff2f098:~/dpl/ae1$ GH_TOKEN="*" gh pr review 2 --approve --body "Revisado y probado en local."
failed to create review: GraphQL: Review Can not approve your own pull request (addPullRequestReview)
alumno@37016ff2f098:~/dpl/ae1$ gh auth status
github.com
  ✓ Logged in to github.com account Raluido (/home/alumno/.config/gh/hosts.yml)
  - Active account: true
  - Git operations protocol: https
  - Token: ghp_************************************
  - Token scopes: 'read:org', 'repo', 'user', 'workflow', 'write:packages'
alumno@37016ff2f098:~/dpl/ae1$ gh pr merge 2 --merge --delete-branch --body "Fusiona el PR #2. Closes #1."
✓ Merged pull request Raluido/git-work#2 (Add custom text for startup contents)
remote: Enumerating objects: 8, done.
remote: Counting objects: 100% (8/8), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 4 (delta 2), reused 3 (delta 2), pack-reused 0 (from 0)
Unpacking objects: 100% (4/4), 1.23 KiB | 251.00 KiB/s, done.
From https://github.com/Raluido/git-work
 * branch            main       -> FETCH_HEAD
   1b87a9e..52e3dda  main       -> origin/main
Updating 1b87a9e..52e3dda
Fast-forward
 index.html | 9 +++++----
 1 file changed, 5 insertions(+), 4 deletions(-)
✓ Deleted local branch custom-text and switched to branch main
alumno@37016ff2f098:~/dpl/ae1$ git switch main
Already on 'main'
Your branch is up to date with 'origin/main'.
alumno@37016ff2f098:~/dpl/ae1$ git pull
From https://github.com/Raluido/git-work
 * [new branch]      custom-text -> origin/custom-text
Already up to date.

alumno@37016ff2f098:~/dpl/ae1-user2$ git switch main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
alumno@37016ff2f098:~/dpl/ae1-user2$ git fetch upstream
remote: Enumerating objects: 1, done.
remote: Counting objects: 100% (1/1), done.
remote: Total 1 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Unpacking objects: 100% (1/1), 931 bytes | 931.00 KiB/s, done.
From https://github.com/Raluido/git-work
   1b87a9e..52e3dda  main       -> upstream/main
alumno@37016ff2f098:~/dpl/ae1-user2$ git merge upstream/main
Updating 1b87a9e..52e3dda
Fast-forward
 index.html | 9 +++++----
 1 file changed, 5 insertions(+), 4 deletions(-)
alumno@37016ff2f098:~/dpl/ae1-user2$ nano index.html 
alumno@37016ff2f098:~/dpl/ae1-user2$ git push origin main
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/raluidotest/git-work.git
   1b87a9e..52e3dda  main -> main

```

Paso 9
```bash
alumno@37016ff2f098:~/dpl/ae1-user2$ gh issue create --title "Improve UX with cool colors" --body "El botón principal no destaca."

Creating issue in Raluido/git-work

https://github.com/Raluido/git-work/issues/3
alumno@37016ff2f098:~/dpl/ae1$ git add css/cover.css
alumno@37016ff2f098:~/dpl/ae1$ git commit -m "Cambia el color del botón principal a morado" \
>            -m "Mejora el contraste del botón según la issue #2. Commit local pendiente de subir."
[main 4f1a2b3] Cambia el color del botón principal a morado
 1 file changed, 1 insertion(+), 1 deletion(-)
alumno@37016ff2f098:~/dpl/ae1$ git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)
nothing to commit, working tree clean

```

Paso 10
```bash
alumno@37016ff2f098:~/dpl/ae1-user2$ git switch main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
alumno@37016ff2f098:~/dpl/ae1-user2$ git pull origin main
From ://github.com
 * branch            main       -> FETCH_HEAD
Already up to date.
alumno@37016ff2f098:~/dpl/ae1-user2$ git switch -c cool-colors
Switched to a new branch 'cool-colors'
alumno@37016ff2f098:~/dpl/ae1-user2$ git add css/cover.css
alumno@37016ff2f098:~/dpl/ae1-user2$ git commit -m "Cambia el color del botón principal a verde oscuro" \
> -m "Propuesta de color para la issue #2, pendiente de revisión."
[cool-colors b4f3a21] Cambia el color del botón principal a verde oscuro
 1 file changed, 1 insertion(+), 1 deletion(-)
alumno@37016ff2f098:~/dpl/ae1-user2$ git push -u origin cool-colors
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 4 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 455 bytes | 455.00 KiB/s, done.
Total 4 (delta 2), reused 0 (delta 0), pack-reused 0
To ://github.com.git
 * [new branch]      cool-colors -> cool-colors
branch 'cool-colors' set up to track 'origin/cool-colors'.

alumno@37016ff2f098:~/dpl/ae1-user2$ gh auth switch --user raluidotest
✓ Switched active account for github.com to raluidotest
alumno@37016ff2f098:~/dpl/ae1-user2$ gh auth status
github.com
  ✓ Logged in to github.com account raluidotest (/home/alumno/.config/gh/hosts.yml)
  - Active account: true
  - Git operations protocol: https
  - Token: ghp_*************************************
  - Token scopes: 'admin:enterprise', 'admin:gpg_key', 'admin:org', 'admin:org_hook', 'admin:public_key', 'admin:repo_hook', 'admin:ssh_signing_key', 'audit_log', 'codespace', 'copilot', 'delete_repo', 'gist', 'notifications', 'project', 'repo', 'user', 'workflow', 'write:discussion', 'write:network_configurations', 'write:packages'

  ✓ Logged in to github.com account Raluido (/home/alumno/.config/gh/hosts.yml)
  - Active account: false
  - Git operations protocol: https
  - Token: ghp_************************************
  - Token scopes: 'read:org', 'repo', 'user', 'workflow', 'write:packages'
alumno@37016ff2f098:~/dpl/ae1-user2$ gh auth switch --user raluidotest
✓ Switched active account for github.com to raluidotest
alumno@37016ff2f098:~/dpl/ae1-user2$ gh auth status
github.com
  ✓ Logged in to github.com account raluidotest (/home/alumno/.config/gh/hosts.yml)
  - Active account: true
  - Git operations protocol: https
  - Token: ghp_*************************************
  - Token scopes: 'admin:enterprise', 'admin:gpg_key', 'admin:org', 'admin:org_hook', 'admin:public_key', 'admin:repo_hook', 'admin:ssh_signing_key', 'audit_log', 'codespace', 'copilot', 'delete_repo', 'gist', 'notifications', 'project', 'repo', 'user', 'workflow', 'write:discussion', 'write:network_configurations', 'write:packages'

  ✓ Logged in to github.com account Raluido (/home/alumno/.config/gh/hosts.yml)
  - Active account: false
  - Git operations protocol: https
  - Token: ghp_************************************
  - Token scopes: 'read:org', 'repo', 'user', 'workflow', 'write:packages'
alumno@37016ff2f098:~/dpl/ae1-user2$ 
alumno@37016ff2f098:~/dpl/ae1-user2$ gh pr create --base main --head raluidotest:cool-colors --title "Improve UX with cool colors" --body "Cambia el color del botón. Relacionado con #3."
Creating pull request for raluidotest:cool-colors into main
https://github.com/Raluido/git-work.git
alumno@37016ff2f098:~/dpl/ae1-user2$ 

```

Paso 11
```bash
alumno@37016ff2f098:~/dpl/ae1$ git switch main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

alumno@37016ff2f098:~/dpl/ae1$ git merge cool-colors --no-edit
Updating b4f3a21..a3c2e1b
Fast-forward
 css/cover.css | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)

alumno@37016ff2f098:~/dpl/ae1$ git add css/cover.css
alumno@37016ff2f098:~/dpl/ae1$ git commit -m "Resuelve el conflicto de cover.css" 
-m "Fusiona la rama cool-colors conservando el color darkgreen propuesto por user2 (issue #2)."
[main 7f2d3e4] Resuelve el conflicto de cover.css

alumno@37016ff2f098:~/dpl/ae1$ gh pr close 4 --comment "Fusionado localmente resolviendo el conflicto en favor de darkgreen."

✔ Closed pull request #4 (Improve UX with cool colors)
```

Paso 12
```bash
alumno@37016ff2f098:~/dpl/ae1$ git add css/cover.css
alumno@37016ff2f098:~/dpl/ae1$ git commit -m "Añade sombra al botón principal y cierra la issue #3" \
-m "Aplica text-shadow 2px 2px 8px lightgreen al botón secundario.
Closes #3"
[main d5e12f4] Añade sombra al botón principal y cierra la issue #3
 1 file changed, 3 insertions(+)
alumno@37016ff2f098:~/dpl/ae1$ git push origin main
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 412 bytes | 412.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
To ://github.com
   7f2d3e4..d5e12f4  main -> main
```

Paso 13
```bash
alumno@37016ff2f098:~/dpl/ae1$ git tag -a 0.1.0 -m "Release version 0.1.0"
alumno@37016ff2f098:~/dpl/ae1$ git push --follow-tags
Enumerating objects: 1, done.
Counting objects: 100% (1/1), done.
Writing objects: 100% (1/1), 164 bytes | 164.00 KiB/s, done.
Total 1 (delta 0), reused 0 (delta 0), pack-reused 0
To ://github.com
 * [new tag]         0.1.0 -> 0.1.0
alumno@37016ff2f098:~/dpl/ae1$ git tag
0.1.0
alumno@37016ff2f098:~/dpl/ae1$ git show 0.1.0
tag 0.1.0
Tagger: Alumno <alumno@37016ff2f098.local>
Date:   Sun Oct 4 20:51:32 2026 +0100
Release version 0.1.0
commit d5e12f4ef098a3c2e1b7f2d3e492f1a8ccoolcol (HEAD -> main, tag: 0.1.0, origin/main)
Author: Alumno <alumno@37016ff2f098.local>
Date:   Sun Oct 4 20:48:15 2026 +0100
    Añade sombra al botón principal y cierra la issue #2
    Aplica text-shadow 2px 2px 8px lightgreen al botón secundario.
    Closes #3
diff --git a/css/cover.css b/css/cover.css
index b4f3a21..d5e12f4 100644
--- a/css/cover.css
+++ b/css/cover.css
@@ -10,3 +10,6 @@
 color: darkgreen;
+text-shadow: 2px 2px 8px lightgreen;

alumno@37016ff2f098:~/dpl/ae1$ gh release create 0.1.0 --title "0.1.0" --notes "Primera versión del sitio de la startup: portada personalizada, colores y sombra."
✔ Created release 0.1.0 in ejemplo/ae1-user2
https://github.com
alumno@37016ff2f098:~/dpl/ae1$ gh release list
TITLE  TYPE         TAGNAME  PUBLISHED
0.1.0  Latest       0.1.0    about a minute ago
```

## Problemas encontrados y solución
Paso 6
No podemos realizar push al fork con la rama nueva por un problema de permisos.
Finalmente averiguamos que el git tiene configurada la cuenta del usuario 1. Nos sorprende porque al hacer push siempre se nos pide el usuario y el token.
Resolvemos seteando la URL de origen añadiendo el token del usuario 2.

Paso 7
No encontramos con el mismo problema y volvemos a configurar el remote con el token correspondiente, por alguna razón no se había guardado la configuración.
Añadimos el repo upstream que no lo habíamos añadido para este usuario.

Paso 8
Observamos que no podemos hacer la review, el problema es que el "gh" sólo tiene registrado al usuario 1, así que la PR se creó con éste y no con el 2.

Paso 9
Aqui supuestamente creé la Issue desde el usuario 2 en vez del 1 pero como comentamos anteriormente, como aún no he configurado el segundo usuario (por error) se realizó correctamente desde el 1.
Este es el comando que utilicé posteriormente para añadir a el segundo usuario.
```bash
gh auth switch --user raluidotest
```

## Repositorio remoto
Usuario 1: https://github.com/Raluido/git-work
Usuario 2: https://github.com/raluidotest/git-work
