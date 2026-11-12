---
title: "Git"
level: h3
---

A día de hoy, los sistemas de control de versiones, y más concretamente Git,
se han convertido en una herramienta indispensable para la informática a
nivel profesional. Neovim cuenta con ciertas integraciones con Git que hacen
que sea bastante cómodo.





#### Git desde la línea de comandos

<!-- TODO Quizás, mover esta sección a la del tutorial de Git. -->

Primero, explicaremos el uso básico del _software_ de líena de comandos
`git`. Para hacer que se muestre en el terminal un _diff_ de un archivo en
concreto, sería

```
$ git diff archivo
```

donde `archivo` será ese que desea consultar. Por ejemplo,

```
$ git diff main.typ
diff --git a/main.typ b/main.typ
index 5990b43..fa579f4 100755
--- a/main.typ
+++ b/main.typ
@@ -47,9 +47,6 @@
 }


-// Notación alternativa de la función sucesor de un número natural.
-#let suc(n) = n + "++"
-
```

Si no se le pasa ningún archivo como argumento, mostrará los _diffs_ de
todos los del repositorio; bueno, de todos a los que se hace _tracking_. Por
ejemplo:

```
$ git diff
diff --git a/main.typ b/main.typ
index 5990b43..fa579f4 100755
--- a/main.typ
+++ b/main.typ
@@ -47,9 +47,6 @@
 }


-// Notación alternativa de la función sucesor de un número natural.
-#let suc(n) = n + "++"
-
```

Algo que debe saber es que, de forma predeterminada, se mostrarán los
_diffs_ si los archivos se encuentran en la _staging area_ (_unstaged_).
Para indicar que se tenga en cuenta a los archivos de la _staging area_
(_staged_), se usa la bandera `--staged`. Tenga en cuenta que esta mostrará
únicamente los que están en la staging area.

```
$ git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   main.typ

no changes added to commit (use "git add" and/or "git commit -a")

$ git add  main.typ

$ git status
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   main.typ

$ git diff

$ git diff --staged
diff --git a/main.typ b/main.typ
index 5990b43..fa579f4 100755
--- a/main.typ
+++ b/main.typ
@@ -47,9 +47,6 @@
 }


-// Notación alternativa de la función sucesor de un número natural.
-#let suc(n) = n + "++"
-
```





#### Mostrar _diffs_ en Neovim

Existe una herramienta dentro del _software_ de línea de comandos `git` que
sirve para que este último invoque al editor predeterminado de su sistema y
así mostrar desde este los _diffs_ del repositorio. Para configurarlo en
Neovim, tiene que introducir desde su terminal el ajuste siguiente de la
configuración de Git:

```
$ git config --global diff.tool nvimdiff
```

Como quizás sepa, alternativamente se podría configurar en el archivo con su
configuración TKTK.

Además, debe tener especificado en la configuración de su _shell_ que su
editor predeterminado sea Neovim; por ejemplo, con lo siguiente en su
archivo _\~/.bashrc_:

```bash
editor="nvim"
```

Ahora, para que se abra un _diff_ de su repositorio de Git en el editor
especificado, basta con usar

```
$ git difftool main.typ
```

De forma predeterminada, esto lo mostrará para los archivos que no se
encuentren en la _staging area_ (_unstaged_). Si desea hacerlo sobre un
archivo que ya se encuentre en la _staging area_ (_staged_), sería haciendo
uso de la bandera `--staged`:

```
$ git difftool --staged main.typ
```

Advierta que cada una de estas dos formas mostrará la parte correspondiente,
es decir, no podrá ver de golpe tanto los _diffs_ de los archivos _unstaged_
y _staged_.




