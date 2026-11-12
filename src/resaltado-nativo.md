---
title: "Resaltado de código nativo de Vim"
level: h4
---

Seguramente, [el resaltado de sintaxis de TextMate sea más completo que el
de Vim](https://news.ycombinator.com/item?id=13601763). Aun así, en algunos
casos es mejor el de Vim, por ejemplo, mediante la extensión
<span class="plgin">VimTeX</span> se tiene una gramática muy buena para el resaltado de
código TeX o LaTeX. También, me pareció mejor el resaltado de código de los
_makefiles_ (los archivos de la herramienta `make`).

Tal y como se explica [aquí][proceso-resaltado-1] y
[aquí][proceso-resaltado-2], el proceso consiste en dos pasos. Primero,
asignar tokens según las reglas de las expresiones regulares. Tras la
asignación de los tokens, se especifican las reglas de resaltado en función
de los diversos tokens.

[proceso-resaltado-1]: https://vim.fandom.com/wiki/Creating_your_own_syntax_files
[proceso-resaltado-2]: https://superuser.com/a/844060

En lo que respecta a los archivos de resaltado de código, la explicación la
puede encontrar con `:help syn-files`.

En principio, los archivos de resaltado de código en Neovim se encuentran en
la ruta donde están los archivos de instalación de Neovim. Por ejemplo, para
el sistema operativo macOS, si la instalación de Neovim se hizo mediante el
gestor de _software_ Homebrew, se encontrarán bajo la carpeta
_/usr/local/Cellar/neovim/<span class="ph">nvim_vers</span>/share/nvim/runtime/syntax_. Por
ejemplo, el archivo
_/usr/local/Cellar/neovim/<span class="ph">nvim_vers</span>/share/nvim/runtime/syntax/cpp.vim_
es el que se usa para el resaltado de código C++.

En una instalación mediante el gestor de paquetes Nix, estos se encontrarían
bajo la carpeta
_/nix/store/<span class="ph">hash_neovim_vers</span>/share/nvim/runtime/syntax_. Ese
<span class="ph">hash_neovim_vers</span> podría ser, por ejemplo, algo así como
`h5pc2ffyvacsg4qhw66gkgpjln24jhvr-neovim-0.8.0`. En cualquier caso, esas son
carpetas que van cambiando, según la versión. Lo mejor sería consultar el
vínculo simbólico _\~/.nix-profile/bin/nvim_ y, una vez en la carpeta a la
que apunta este, entrar en _share/nvim/runtime/syntax_ (me refiero a la ruta
relativa). Ahí se encuentran todos los archivos de gramáticas tradicionales
de Neovim.

Algunas de estas son también sobrescritas por algún _plug-in_. Por ejemplo,
`vimtex` usa un archivo de resaltado de código distinto al que viene de
forma predeterminada con Vim. Aun así, creo que el que trae Vim de serie es
muy bueno. Incluso permite extenderlo para ciertas sintaxis particulares.
Vea `:help mysyntaxfile-add`.

Los archivos anteriores se deben dejar tal y como vienen, pues irán
actualizándose con las distintas versiones de Neovim. Los ajustes finos que
desee realizar sobre estos, puede hacerlos tanto en archivos de
configuración bajo _/etc_, si es para una configuración global del sistema,
o bajo _\~/.config/nvim_, si es para un usuario en concreto. Así, si crea el
archivo _\~/.config/nvim/syntax.vim_ o _\~/.config/nvim/syntax.lua_, TKTK.

<https://news.ycombinator.com/item?id=18349013>

Para ver cómo se encuentran configurados los parámetros del resaltado
léxico, basta con usar el comando `:highlights` sin argumentos.

```vim
:highlights
```

Así, se muestran todos los parámetros tal y como están actualmente.

Algo de lo que debe ser consciente es de que no todos los esquemas de
colores están pensados para usar Tree-Sitter. TKTK.


---


Puede ver una buena [explicación de los archivos de
sintaxis][tuto-sintaxis-vim], con ejemplos.

[tuto-sintaxis-vim]: http://vim.wikia.com/wiki/Creating_your_own_syntax_files

Los archivos de sintaxis para Vim se encuentran bajo el directorio
_<span class="ph">vimruntime</span>/syntax/_, donde el valor de <span class="ph">vimruntime</span> dependerá
de cómo lo instaló. Por ejemplo, si lo instaló mediante el gestor de
paquetes Homebrew, será
_/usr/local/Cellar/neovim/<span class="ph">nvim_vers</span>/share/nvim/runtime_.

Por ejemplo, el archivo _rst.vim_ será el que especifique la sintaxis para
los archivos de reStructuredText. Al igual que suele pasar en los sistemas
Unix, existe una jerarquía, normalmente, de 3 niveles, para los archivos de
configuración. Creo que en este caso es como casi siempre:
_\~/.config/nvim/_ tiene prevalencia sobre los demás, a nivel del usuario.
Luego, hay uno de configuración para el sistema, en _/etc/_, y, finalmente,
está el que dije antes, es decir, el del runtime, que no debe tocarse, pues
se modifica con las actualizaciones de Neovim.

Esto debería cambiar con Tree-sitter TKTK.

Los archivos de indentación, se encuentran bajo _<span class="ph">vimruntime</span>/intent/_.





