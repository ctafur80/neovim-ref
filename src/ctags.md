---
title: "Ctags"
level: h3
---

En realidad, gracias a la aparición y el gran desarrollo que han
experimentado los servidores LSP, las _ctags_ a día de hoy ya no son algo
relevante en los editores, pero en su día fueron una funcionalidad que
ayudaba bastante al desarrollo.

Las _ctags_ son unas etiquetas que pueden usarse en un proyecto de
_software_ que esté editando. Lo que le permiten es moverse por el código
fácilmente, por ejemplo, si se encuentra en una llamada a una clase, puede
moverse fácilmente a la definición de esa clase, aunque se encuentre en otro
archivo del proyecto.

Deberá tener instalado el paquete de _software_ `ctags`. Por ejemplo, para
macOS, está en Homebrew:

```
$ brew install ctags
```

Una vez que lo tenga instalado, para ir a la definición de un token sobre el
que tenga el cursor, deberá usar la combinación <kbd>Ctrl</kbd> + <kbd>]</kbd>
(control más cierre de corchete). Luego, puede moverse por la lista dando
saltos con <kbd>Ctrl</kbd> + <kbd>o</kbd> y <kbd>Ctrl</kbd> + <kbd>i</kbd> para ir atrás
y adelante.

Puede ver también aquí [una explicación de las
ctags](https://andrew.stwrt.ca/posts/vim-ctags/).



