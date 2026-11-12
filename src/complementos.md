---
title: "Complementos"
level: h2
---

En el mundo de Neovim (y Vim), llaman _complementos_ (_plug-ins_) a lo que
en otros editores llaman _extensiones_ (_extensions_). En cierto modo, son
algo distintos, pues la filosofía de Vim es ser _scriptable_, por lo que en
principio un complemento no debería hacer muchas cosas, al contrario que las
extensiones.

También, es bastante común que los usuarios hagan por sí mismos algunos de
los complementos que usan.

Aunque existen muchos complementos que tratan de imitar funcionalidades de
IDEs, la filosofía de Vim no va por ahí. TKTK.

A partir de la ersión 0.12 de Neovim, este trae de serie un gestor de
complementos (_plug-in manager_), con lo que ya no necesita tener que
instalar _software_ externo para esto. De momento es bastante básico, pero
TKTK. Los comandos a este respecto son del tipo `vim.pack` TKTK.

Encontré un [tutorial][tutorial-vim-pack] bastante bueno de Evgeni
Chasnovski.

[tutorial-vim-pack]: https://www.youtube.com/watch?v=J1r0vrqOMJo&t=278s


<!--
Además, Neovim no suele adoptar muchas de las funcionalidades modernas de
los IDEs, como indicaciones visuales sobre los cambios en el repositorio
Git. Neovim suele centrarse más bien en las funcionalidades de edición en el
espíritu de las que tenía Vim en la época de Moolenaar.

Debido a esto, casi con toda seguridad tendrá que usar algunos _plug-ins_.
Personalmente, trato de usar pocos, pues no me gusta sobrecargarlo demasiado
y, además, creo que tampoco suelo necesitar tantas cosas. Para quien le
gusta usar muchos _plug-ins_, por ejemplo, porque desee que su editor sea
más parecido a un _full-blown_ IDE, existen ciertas configuraciones que se
pueden instalar y en las que TKTK. El problema de estas es que quizás en
algún momento desee tratar de hacer algún ajuste muy específico. TKTK.

Debe saber también que existen algunos _plug-ins_ que en realidad son
_packs_ de _plug-ins_, como <span class="plgin">[`mini.nvim`][]</span>, que ha alcanzado
bastante popularidad. Este cuenta con una serie de _plug-ins_ que
implementan de forma básica (pero suficiente para la mayoría) muchos de los
_plug-ins_ más populares.

[`mini.nvim`]: https://github.com/echasnovski/mini.nvim

Los gestores de _plug-ins_ en Neovim han sido tradicionalmente herramientas
externas al propio editor. Sin embargo, Neovim (al igual que Vim) incluye
desde hace tiempo un sistema nativo de gestión de paquetes (`:help
packages`), a menudo llamado "packpath" o simplemente `pack`. Este sistema
es funcional pero muy básico, y no gestiona automáticamente la descarga o
actualización de repositorios, lo que ha llevado a la popularidad de
gestores de _plug-ins_ externos.

Para la versión 0.12 y futuras, se está desarrollando un gestor de plugins
nativo mucho más completo y avanzado. El objetivo es que este nuevo gestor
pueda manejar la instalación, actualización y carga de plugins de forma
automática, similar a como lo hacen herramientas como `lazy.nvim` o
`packer.nvim`, pero integrado directamente en el núcleo de Neovim. Esto
representa un paso importante para mejorar la experiencia de serie del
editor.

Puede obtener información sobre este en la ayuda oficial de Neovim con el
comando `:help vim.pack`. También, conviene que consulte `:help packages`.

Por lo que se explica ahí, los _plug-ins_ se instalan bajo el directorio
_`$XDG_DATA_HOME`/share/nvim/site/pack_, siendo, por ejemplo, en macOS, ese
`$XDG_DATA_HOME` el directorio _\~/.local/share_. Los hay de dos tipos: tipo
_start_ y tipo _opt_. Los primeros se cargan siempre al iniciar Neovim; los
otros, cuando se necesiten. Se incluyen en directorios distintos, dentro de
la ruta anterior. Normalmente, los _plug-ins_ suelen ser de este último
tipo.

La forma de implementar los comandos a este respecto es mediante la API
`vim.pack` de Lua.

Básicamente, un _plug-in_, dentro del sistema de archivos no es más que un
repositorio de Git. Son bastante "crudos" a este respecto.

Para actualizar los _plug-ins_ instalados, se usa el comando `:lua
vim.pack.update()`. Se abrirá una pestaña con la información sobre los
cambios, pero no se habrá actualizado aún. Para que se realicen estas
actualizaciones, debe escribir el archivo; como cualquier otro archivo, con
`:write`. Luego puede cerrar la pestaña con `:quit`.

Para eliminar _plug-ins_, se usa la función `vim.pack.del()` de la API de
Lua. Dentro debe incluir una lista de cadenas con los nombres de los
_plug-ins_ que desea eliminar. En cualquier caso, creo que no termina de
eliminarlos del directorio, por lo que termino comprobándolo por mí mismo y
eliminando esos repositorios en caso necesario.


---


Algo que se incorporó a Neovim hace poco es que es muy sencillo transformar
a Lua un _plug-in_ hecho en Vimscript. Gracias a esto, podemos tener
fácilmente los _plug-ins_ de Vim. Por ejemplo, son muy buenos los que crea
el desarrollador [Tim Pope][]. No obstante, muchos de los _plug-ins_ de Pope
se han copiado en _packs_ de _plug-ins_, como <span class="plgin">[`mini.nvim`][]</span>, por
ejemplo

[Tim Pope]: https://github.com/tpope


---


¿Por qué prefiero usar pocos _plug-ins_, al contrario de lo que hacen
muchos? Soy más partidario de la filosofía de Tim Pope, es decir, no tratar
de reimplementar nada de Vim o Neovim. Simplemente, adaptarme a este.

Hay gente que, al usar tantos _plug-ins_, termina haciendo un uso muy
diferente del editor TKTK.

Además, si usa muchos _plug-ins_ y no llega a aprender realmente a
configurar Vim o Neovim, seguramente llegue el momento en el que desee hacer
un ajuste muy específico sobre algo y TKTK. En lugar de aprender realmente a
usar Vim o Neovim, se encontrará siempre copiando y pegando cosas hechas por
otros TKTK.



---


Por qué usar Vim o Neovim a estas alturas, cuando existen muchas
herramientas gráficas con un montón de cosas TKTK.

Hay quien prefiere hacer un uso minimalista de la edición y desarrollo. Por
ejemplo, puede ver [este vídeo de Gary
Bernhardt](https://www.youtube.com/watch?v=iF4RvQq6yU0).


---


Otra cosa que conviene hacer es comprobar con `checkhealth lazy` TKTK.
-->


