---
title: "Introducción"
level: h2
---

Los editores basados en modos otorgan, a quien tiene la paciencia de
practicar y desarrollar cierta destreza en su manejo, una velocidad de
edición increíble. Quizás, no tanto como la estenografía (_stenography_),
pero no creo que esta sea una buena herramienta para programar; solo es útil
para texto corrido; no para ediciones saltando entre partes distintas.



Un inconveniente que tienen tanto Vim como Neovim es que se trata de
editores que de serie tienen muchas carencias, desde el punto de vista
actual. Es decir, muchas de las funcionalidades que se dan por sentadas a
día de hoy en los IDEs, en Vim y Neovim deberá añadirlas mediante algún
_plug-in_ o configurándolas por usted mismo. Esto se debe a que siguen una
filosofía más de tipo bazar, en oposición a los proyectos de tipo catedral,
según la dicotomía presentada en los 90 por TKTK.

Para poder ser tan versátil, su configuración se tiene que hacer, en parte,
mediante _scripting_, cosa que a mucha gente no le gusta. TKTK.

A este respecto, tengo sentimientos enfrentados y no tengo una opinión bien
formada. En Vim y Neovim, al final, en cierto modo, terminará
transformándolo y personalizándolo en parte. Por un lado, a mucha gente le
gusta que se les dé una herramienta con sus usos ya establecidos; no una que
tenga un componente considerable de configuración y
personalización.[^convention-over-conf] Es decir, eso de "_convention over
configuration_".

[^convention-over-conf]: Esto lo menciona la profesora de diseño web en el
  MIT Lua Verou. TKTK. También, es de destacar que esta es la filosofía que
  suele seguir la empresa Apple con sus productos. TKTK.

Por otro lado, se puede considerar que con lo que trae el editor Vim o
Neovim de serie es suficiente. Que todo lo demás es accesorio y no aporta
gran cosa. Por ejemplo, quien dirige actualmente el proyecto Neovim, el
programador Justin Keyes, hace, por lo que veo, un uso bastante minimalista
de este. Otra persona relevante en el mundo de la programación que hace un
uso bastante minimalista de Vim es Mitchell Hashimoto.

También, existen muchos grandes programadores, como George Hotz o John
Carmack, que casi no le dan importancia a las herramientas que usan. TKTK.
Es cierto que no han llegado a usar Vim o Neovim durante mucho tiempo y que
actualmente usan IDEs, pero TKTK.

Esto demuestra que no es necesario ser un "mago" o un _power-user_" de las
herramientas que usa uno para ser un programador de primer nivel.

Sí que es cierto que muchos _plug-ins_ de Vim y Neovim han roto en parte con
la filosofía de estos, y esto no es deseable.[^7] Es decir, lo ideal es que
los _plug-ins_ se adapten a Vim y Neovim y no modifiquen ciertos principios
de usabilidad de dichos editores. Buen ejemplo de _plug-ins_ que respetan al
editor son los creados por el desarrollador Tim Pope, bastante popular en el
ecosistema de los _plug-ins_ de Vim.

[^7]: De hecho, en Vim, al principio no era posible la creación de
  _plug-ins_. Es algo que añadió Moolenaar TKTK.

Dicho esto, la mayoría de la gente usa, en mayor o menor medida, _plug-ins_
en su uso de Vim y Neovim. La ventaja de Neovim, con respecto a Vim, está en
que los _plug-ins_ se hacen en el lenguaje Lua, que es bastante más maduro
que Vimscript.[^8] Además, así no se duplican esfuerzos en el proyecto, al
no tener que estar desarrollando, en paralelo al propio editor, un lenguaje.
Tal y como mencioné antes, esto es coherente con la filosofía de Neovim, que
el propio Keyes ha mencionado en alguna conferencia. A veces lo sintetiza
diciendo la frase "navegar la ola". Es decir, aprovechar el _software_ que
ya existe, sin tener que reimplementarlo. Simplemente, integrándose con
este. Por ejemplo, integrándose con algunos IDEs como VSCode, con algunos
navegadores web, etc.


---


En realidad, Neovim no dista mucho de Vim. De hecho, es muy recomendable
obtener un conocimiento algo avanzado de Vim, antes de pasarse a usar
Neovim. Sobretodo, de su configuración.

El mejor tutorial que he encontrado sobre la configuración avanzada de Vim
es [este](https://www.youtube.com/watch?v=JFr28K65-5E).


---


George Hotz hablando de por qué prefiere a VSCode.

<https://www.youtube.com/watch?v=bf8E8zSZTtE&t=5006s>

La cuestión de fondo quizás está, en su caso, en que es preferible que los
creadores de la herramienta sean quienes te impongan su forma de uso, en
lugar de usar un montón de _plug-ins_. Algo así explicaba Lea Verou. Es
también un poco la filosofía que sigue la empresa Apple con sus productos. A
esto lo suelen llamar "convention over configuration".

Por ejemplo, Hotz lo explica también en una entrevista con Lex Fridman.

<https://www.reddit.com/r/ThePrimeagenReact/comments/14mpdke/george_hotz_lex_fridman_discussing_copilot_code/>


---


Pero ¿por qué Neovim? La gente que suele elegir Vim o Neovim para programar
suelen hacer un uso bastante minimalista y con control de TKTK. Por ejemplo,
[es el caso de Mitchell
Hashimoto](https://www.youtube.com/watch?v=rysgxl35EGc), el creador de
Terraform.

[^1]: También hay quien los llama _acordes_ (_chords_), como suelen
  llamarlos en la documentación de Emacs; otro editor.

[^2]: A este respecto, por ejemplo, puede ingestigar sobre el _context
  switching_. TKTK.

[^3]: Aunque Vim es un proyecto _open source_, tenía que pasar absolutamente
  todo por la aprobación de Bram; es decir, era un proyecto muy del estilo
  _benevolent dictator for life_ (BDFL). Con lo cual, quizás el proyecto no
  siga adelante tras la muerte de su creador y los que lo seguían usando
  terminen por pasarse a Neovim, que es la bifurcación de este con mayor éxito
  y cuenta con un desarrollo muy activo.

[^4]: Hay que aclarar que Vim y Neovim también cuentan con atajos de teclado
  (_shortcuts_), pero no se usan tanto como los modos (_modes_).

[^5]: TKTK.



[^8]: En realidad, en Neovim se pueden crear _plug-ins_ tanto en Vimscript
  como en Lua, aunque lo usual suele ser en Lua. En Vim, sin embargo, solo
  en Vimscript.


---


Quizás, el mejor tutorial sobre una configuración sea actualmente el
titulado [_My Entire Neovim Setup From Scratch After 8
Years_][devops-toolbox-config-tuto] del canal de YouTube DevOps Toolbox. En
realidad, este hace referencia a varios tutoriales sobre las distintas
partes.

[devops-toolbox-config-tuto]: https://www.youtube.com/watch?v=x__SZUuLOxw

En cualquier caso, yo actualmente suelo usar una configuración muy
minimalista de Neovim.



---


Cuando se adentra en Neovim, lo normal es que le abrume la enorme cantidad
de _plug-ins_ y configuraciones que realizan muchos usuarios. Esto se junta
con la sensación que solemos tener todos inicialmente de que a Neovim le
faltan muchas cosas con las que cuentan de serie otros editores e IDEs.
Llegado un punto, si aprende lo básico de Vim o Neovim, se dará cuenta de
que puede hacer un uso muy eficiente del mismo sin necesidad de muchas
configuraciones y _plug-ins_. Yo actualmente hago un uso muy minimalista de
Neovim.



---


Tal y como dice Bram Moolenaar.

> Software development is much more of a craft. A craftsman uses whatever
> tools he thinks will get the best result, no matter if they are what
> everybody else is using or something different. And a good craftsman makes
> his own tools when needed.



---


Referencia sobre la historia de Vim: <https://www.youtube.com/watch?v=_2y6vZna6fU>


---


Algo que quizás pueda llegar a ser el futuro sería que Neovim terminara
separándose en algo como [KindaVim][] y el propio editor Neovim que funcione
sobre este.

[KindaVim]: https://kindavim.app/


---


Opinión de Gary Bernhardt sobre Vim: <https://www.youtube.com/watch?v=32VpMG0hVL8>




