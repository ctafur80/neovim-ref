---
title: "Historia"
level: h2
---

Tal y como hemos dicho, Neovim surgió como bifurcación de Vim (Vi Improved),
creado por Bram Moolenaar, en 1991, que es a su vez una bifurcación de Vi,
creado en 1976 por Bill Joy, una persona muy relevante en la historia de las
ciencias de la computación.[^bill-joy] Aun así, Vi era un editor bastante
simple que surgió de forma natural debido a las limitaciones del _hardware_
de la época: no se habían inventado el ratón ni la interfaz gráfica de
usuario. Vim sí supuso un salto grande en cuanto a la cantidad de
funcionalidades y lo cierto es que la interfaz de uso mediante modos
(_modes_) de Vim son una auténtica genialidad como experiencia de usuario
(UX).

[^bill-joy]: Por ejemplo, creó el sistema operativo BSD, de los que existen
  muchos descendientes a día de hoy, como FreeBSD o el propio macOS (de los
  computadores de Apple).

Aun así, llegó un punto en el que Vim se quedó bastante obsoleto en
comparación con otros editores modernos como Sublime Text y Visual Studio
Code (VSCode), además de que el modo en que Moolenaar dirigía el proyecto
era bastante "dictatorial" y ponía muchas pegas a las propuestas para
modernizarlo. Por ejemplo, modernizar la base del código, pues había partes
que podrían sustituirse por bibliotecas de C, en lugar de ser implementadas
por el propio editor. También, eliminar el soporte para ciertas
arquitecturas obsoletas como, por ejemplo, Amiga. Estas fueron las
principales motivaciones para la creación de Neovim.

Tras esta adaptación inicial, Neovim pasó a centrarse más en adoptar LSP y
Tree-Sitter, unas tecnologías modernas de editores e IDEs que básicamente
hacen que el editor sea más "inteligente". Por ejemplo, antes, para
renombrar una variable, tenía que tener en cuenta que lo que estaba
renombrando en realidad era esa coincidencia (_match_) de texto, como mucho,
usando una expresión regular; ahora, gracias a esa "inteligencia", puedo
ordenar que se renombre a un objeto en particular, sin el problema de que
haya coincidencias parciales con otros identificativos en el código o con
partes de cadenas, pues se hace en base a un nodo (_node_) de un árbol de
sintaxis abstracta (_abstract-sintax tree_ o AST).

Las cosas interesantes que podría consultar sobre Neovim a partir de sus
propias fuentes de información, son `:help msgpack-rpc`, `:help
nvim-features`. Es interesante también una herramienta de diagnóstico que
trae de serie: `:checkhealth`.

Las versiones de Neovim anteriores a la 0.5 se centraron en refactorizar el
código de Vim para adaptarlo a los nuevos tiempos, así como la integración
de Lua como lenguaje de apoyo, sustituyendo así a Vimscript donde se pueda.
A partir de la versión 0.5, los proyectos comenzaron a diverger. Por tanto,
se puede decir que Neovim en sus comienzos avanzaba de forma muy lenta por
culpa de evolucionar partiendo de algo que tenía que refactorizar.

También, la gente que dirigía el proyecto ha ido cambiando y en esto se nota
la evolución del mismo. El creador original de Neovim fue Thiago de Arruda,
en 2014, que parece que no se lo tomó muy en serio durante algún tiempo.
Incluso terminó por desligarse del proyecto y este pasó a estar en manos de
varios desarrolladores, entre los que se encontraba Justin Keyes, que se
puede decir que es actualmente quien dirige el proyecto. La filosofía de
Keyes es la de "navegar la ola" TKTK.

Bajo el "mandato" de Keyes, se han implementado muchas cosas en Neovim, como
la configuración mediante código Lua, en lugar de Vimscript, etc. TKTK.

Hay que mencionar también que, en Agosto de 2023, falleció Bram Moolenaar.
El desarrollo de Vim continúa, en manos de otro desarrollador principal,
pero creo que Neovim cuenta con bastante más aceptación a día de hoy.


