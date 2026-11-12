---
title: "Introducción"
level: h2
---

Un editor o IDE que pueda encontrarse en distintos _modos_ (_modes_) de
edición se suele decir que es un _editor modal_ (_modal editor_). En cada
modo, las pulsaciones de teclas, o las combinaciones de estas, producirán
una acción distinta. Muchas de estas no consisten en insertar texto, sino
realizar movimientos del cursor, selecciones, borrar palabras, etc. La
alternativa a los editores modales son los editores no modales (_modeless
editors_[^modeless]), que se caracterizan por encontrarse siempre en un
único modo, sin poder cambiar a otro. Lo normal es que, en los no modales,
las pulsaciones de teclas suelen insertar texto y cualquier otra función se
suele hacer con atajos de teclados (_shortcuts_), es decir, combinaciones de
teclas modificadoras (por ejemplo, <kbd>Alt</kbd> o <kbd>Ctrl</kbd>) con teclas
normales. Un editor no modal, por tanto, está más limitado que uno modal en
cuanto a las posibilidades de edición con el teclado.

[^modeless]: Quizás, esta expresión, que la he leído en la propia
  documentación oficial de Neovim, sea algo desacertada, pues los otros
  editores tienen un modo. Bueno, o quizás no; según se mire.

En cierto modo, usar un editor modal es como usar un lenguaje para editar.
Es un lenguaje que no le muestra en pantalla código, sino que irá viendo en
el editor los efectos de lo que codifica. Quizás su primera impresión sea
que esto es demasiado cargante ---hacer uso de dos lenguajes a distintos
niveles simultáneamente para escribir el código en el editor---, y,
efectivamente, la curva de aprendizaje de los editores modales es algo
escarpada, pero, cuando ha interiorizado ese lenguaje para la edición ---ha
logrado crear la _muscle memory_ que requiere---, será capaz de editar a una
velocidad increíble.

Además, los modos son generativos y flexibles, es decir, a partir de un
conjunto limitado de recursos, se pueden generar una cantidad de acciones
casi ilimitada, ya que se pueden combinar entre sí; al contrario de lo que
sucede con los editores no modales, en los que no tiene sentido generar
atajos de teclado nuevos a partir de la combinación de otros básicos.

El primer editor modal TKTK fue Vi, un editor TUI creado por Bill Joy en
1976, TKTK. No es extraño que en esa época surgiese un editor modal, pues,
aunque la empresa Xerox había presentado ya un computador con
funcionalidades GUI, aún no se vendía ningún computador así. Un editor modal
proporcionaba una gran ergonomía para editar archivos dentro de un terminal
(o emulador de terminal).

En 1991, el programador Bram Moolenaar creó, a partir de una bifurcación de
código (_fork_) de Vi, su editor llamado Vi Improved, más conocido como
[Vim]. Este es el editor que realmente popularizó los editores modales.
Moolenaar realizó un gran trabajo, tanto en su "ergonomía" ---gracias a los
modos--- como en la propia implementación del _software_; llegando incluso a
crear un lenguaje propio, conocido como Vimscript, para la configuración del
mismo, lo cual también terminó haciendo que se pudiesen usar complementos
(_plugins_), algo similar a las extensiones (_extensions_) en otros editores
e IDEs.

[Vim]: https://www.vim.org/

En parte, algo que impulsó muchísimo la popularización de Vi y Vim fue que
gran parte de los servidores tipo Unix (Linux, Solaris, etc.) lo traen
instalado de serie. Por tanto, es muy probable que como administrador de
sistemas encuentre que debe acceder a un servidor que tiene instalado aluno
de estos dos. Y, como quizás sepa, los sistemas tipo Unix suelen seguir la
filosofía de que los ajustes del sistema se hagan manipulando
archivos.[^registro-windows] Por tanto, saber usar estos editores es una
habilidad que se suele valorar en el mundo de la administración de sistemas.

[^registro-windows]: Esto contrasta, por ejemplo, con la filosofía de los
  sistemas Windows, que, en lugar de mediante archivos de configuración, la
  administración se suele hacer mediante el Registro del Sistema.

Existen otros editores que se basan también en los modos de Vim. Algunos son
_forks_ del propio Vim, que surgieron por discrepancias sobre el modo de
gestionar el proyecto por Moolenaar; al parecer, era bastante
dictatorial[^bdfl], aunque esto a veces es bueno en los proyectos de
_software_ con licencias _open source_.

[^bdfl]: Una forma de calificar al desarrollador principal de un proyecto de
  _software_ con licencia _open source_ (incluyendo aquí también a las de
  _software_ libre, _free software_) que lo maneja con "mano de hierro",
  sobretodo cuando él (o ella) ha sido el creador inicial del mismo, es
  decir que se trata de un _dictador benevolente de por vida_ (_benevolent
  dictator for life_), o por sus siglas: BDFL.

  En cierto modo, tiene bastante sentido que el desarrollador que más
  dedicación ha puesto en un proyecto sea muy selectivo a la hora de aceptar
  las contribuciones de otros. Me viene a la mente, por ejemplo, una
  entrevista que escuché a Brendan Eich, el creador de JavaScript, en la que
  explicaba que muchas de las partes muy criticadas de dicho lenguaje se
  deben a que fue demasiado permisivo, en los comienzos de dicho lenguaje,
  al aceptar la solicitudes que le hacían.

  Existen varios proyectos de gran éxito en las ciencias de la computación
  que se podría decir que son dirigidos por algún BDFL. Es el caso, por
  ejemplo, del lenguaje Python, por parte de Guido Van Rossum. Creo que
  actualmente la mayoría de los creadores de algún _software_ _open source_
  han aprendido de la experiencia y tienen bastante cuidado con lo que
  aceptan incluir. Parece que todo tiene que tener bastante sentido para ser
  incluido. Creo que esto es parte del éxito de Vim y algunos de sus
  sucesores.

El _fork_ más popular de Vim es [Neovim][web-de-neovim], que es al que se
dedica este documento. Neovim, como proyecto de _software_, es dirigido de
un modo más acorde a los tiempos modernos, haciendo uso de herramientas como
GitHub, etc. También, cuenta con integración con tecnologías modernas para
una edición más "inteligente" (_smarter_), como LSP y Tree-Sitter, que lo
hacen acercarse algo más a un IDE, aunque dista mucho de ser tan "pesado"
como un IDE.

[web-de-neovim]: https://neovim.io/

De todos modos, debe tener en cuenta que Neovim trata de no "separarse" en
exceso de Vim en su uso básico. Se podría decir que sus principales
desarrolladores se lo piensan mucho antes de añadirle alguna funcionalidad.
Siempre puede añadir cualquier funcionalidad que desee mediante algún
complemento y, si no existe, construyendo usted uno. Es decir, el principio
el uso de Neovim no dista tanto del de Vim, y esto es algo que se busca
deliberadamente por parte de sus creadores. Así, si usa Neovim en su sistema
habitual y Vi o Vim en servidores a los que debe acceder, no será tan
distinta la forma de uso. Pero, por otro lado, sí que han modernizado muchas
partes de Vim que estaban muy anticuadas.

Otras herramientas que hacen uso de los modos Vim son simplemente
extensiones de otros editores o IDEs. En realidad tal y como explica el
desarrollador Gary Bernhardt, [se dejan muchas funcionalidades sin
implementar][bernhardt-modos-vim], pues la lógica de Vim para la edición (y,
por tanto, también la de Neovim) cuenta con muchísimas funcionalidades, como
comprobará por usted mismo a lo largo de la lectura de este documento.

[bernhardt-modos-vim]: https://twitter.com/garybernhardt/status/902956444596617216

Un ejemplo de extensiones de modo Vim en un IDE es la de VSCode, que no
suele gustar a los que la han usado. Existe también la integración del modo
Vim en VSCode por medio del propio Neovim. TKTK. En cuanto a la extensión
del modo Vim de Zed, parece que es mucho mejor que la de VSCode.

Otro aspecto importante de Vim está en que su configuración es _scriptable_,
es decir, uno mismo puede ampliar las funcionalidades del propio editor si
toca la configuración. Esto hay a quien le gusta y a quien no. TKTK.

Que sea _scriptable_ o _hackeable_ no quiere decir que se creen complementos
enormes que trastocan profundamente el uso de Vim o Neovim. De hecho, algo
que se puede percibir en los complementos para Vim de Tim Pope, así como en
las charlas de Justin Keyes, es que se promueve seguir una filosofía de
"**navegar la ola**". TKTK.

Los modos de Vim han "saltado" de los editores e IDEs y ya se encuentran
también en otro tipo de _software_, como por ejemplo en navegadores web
TKTK.

Hay que mencionar también que han salido propuestas alternativas a Vi
siguiendo una misma filosofía. Es decir, existen editores con modos de
edición con una filosofía similar a la de Vi solo que con unas reglas
distintas, que según ellos tienen más sentido. El ejemplo más popular es el
de los modos del editor Kakoune, que luego han implementado otros editores
que han alcanzado cierta popularidad ---aunque no comparable con Vim y
Neovim--- como Helix. Seguramente no han alcanzado gran popularidad por dos
motivos principales: (1) la inercia de los modos de Vi, y (2) que, aun si se
admite que supone una mejora respecto a los modos de Vi, esta no es tan
sustancial como para impulsar a los usuarios de Vi y sus descendientes a
cambiar de editor.




