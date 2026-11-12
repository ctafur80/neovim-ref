---
title: "Neovim"
level: h3
---

Neovim es un _fork_ de Vim que parece que le ha superado en ciertos
aspectos. Se trata de un proyecto con un ritmo de desarrollo muy bueno.
También, tras la muerte de Moolenaar, en agosto de 2023, el proyecto Vim
parece que [ha tenido que readaptarse][vim-tras-moolenaar], pues, tal y como
he explicado antes, el desarrollo del proyecto era básicamente hecho por
Moolenaar, que en todo caso aceptaba sugerencias; es decir, era muy poco
distribuido.

[vim-tras-moolenaar]: https://www.youtube.com/watch?v=bopbmRyHQog

Parece que el desarrollo de Neovim tiene actualmente un ritmo muy superior
al de Vim. Una diferencia importante entre estos está en el lenguaje de
_scripting_ de la configuración. Vim cuenta con un lenguaje propio, llamado
Vimscript, mientras que en Neovim se optó por delegar esto a un lenguaje de
_scripting_ ya existente llamado Lua. Se trata de un lenguaje con algunas
peculiaridades. Lua se suele usar como lenguaje dinámico que se incrista
(_embed_) en algún proyecto de otro lenguaje más estático y "pesado".
Alcanzó en su día bastante popularidad en el ámbito del desarrollo de
videojuegos, para programar algunas partes en Lua en lugar de en C++, lo que
hacía que fuese más cómodo.

En el caso de Neovim, este cuenta con una API para usar Lua para la
configuración del mismo, que se corresponde con todas las posibilidades que
da Vimscript y los ajustes del propio Vim.

Lua y Neovim comparten la filosofía de "navegar la ola", como ha dicho en
varias ocasiones Justin Keyes, el que se podría decir que es quien dirige el
desarrollo de Neovim. (En realidad, creo que Neovin lo ha copiado de Lua.)
Esto se refleja, por ejemplo, en la elección de Lua como sustituto de
Vimscript; así, no tienen que mantener el desarrollo de un lenguaje
paralelamente al de un editor. También se refleja en otras decisiones de
Neovim, como en el uso de ciertas bibliotecas (_libraries_) de _software_ de
tipo _open source_ que existe de forma independiente para sistemas, en lugar
de implementarlas por sí mismo, como sucede en Vim; al menos, sucedía en la
época de Moolenaar. Quizás ahora hayan hecho una refactorización como Neovim
a este respecto. A decir verdad, esto quizás se deba a que ni siquiera
existían esas bibliotecas cuando Moolenaar las implementó. Otra ventaja de
Neovim respecto a Vim está en que se han deshecho del soporte a muchas
arquitecturas _legacy_, como la de los computadores Amiga, por ejemplo. Esta
liberación de "lastre" supone una gran ventaja.

Por cierto, el proyecto Neovim ha dedicado bastante esfuerzo en que este
siga siendo compatible con los complementos de Vim, incluso los modernos
(versión 9 de Vimscript), lo cual es un ejemplo más de esa filosofía.

Por cierto, en lo que respecta a los complementos, algo que debe tener en
cuenta es que lo que sería aconsejable es no abusar de su poder. Es decir,
existen muchos complementos que trastocan completamente el uso del propio
Vim o Neovim. Esto va en contra de la filosofía de TKTK. Además, si, por
cualquier cosa, tiene que volver a usar temporalmente un Vim puro, TKTK.

Esto es algo de lo que se han dado cuenta los principales desarrolladores de
Vim y Neovim, como Tim Pope y TKTK. Mi impresión es que debido a eso no
suelen usar muchos complementos.

Aunque Vim y Neovim cuenten con una curva de aprendizaje algo elevada, con
cierto nivel de manejo de estos ya se es capaz de apreciar por qué son tan
elogiados por mucha gente, en lo que respecta a la usabilidad; o, si lo
prefiere, a la ergonomía.

Una muy buena introducción a Vim y Neovim es [_Learn Vim For the Last Time:
A Tutorial and Primer_][learn-vim-for-the-last-time], de Daniel Miessler.

[learn-vim-for-the-last-time]: https://danielmiessler.com/p/vim/



