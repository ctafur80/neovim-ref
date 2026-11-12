---
title: "_Surrounds_"
level: h3
---

Un complemento creado por Tim Pope que tiene mucha popularidad es
`vim-surround`. Como Pope ha permanecido en Vim (no ha llegado nunca a dar
el "salto" a Neovim), existen muchas copias para Neovim de este complemento.
Es común encontrarlo dentro de los complementos que agrupan a varios, como
`mini.nvim`. Aun así, Neovim ha procurado siempre seguir manteniendo la
compatibilidad con los complementos de Vim (escritos en Vimscript), y en
concreto los de Pope se pueden usar en Neovim sin problemas.

Este tipo de complementos, que englobo en lo que llamo _surrounds_, consiste
en extender las secuencias del modo normal añadiendo algunas para actuar
cómodamente sobre texto "envuelto" entre algunos símbolos delimitadores como
paréntesis, `( )`, llaves, `{ }`, signos de dólar, `$ $`, etc. Normalmente,
sirven para cualquier delimitador de código o incluso texto.

Evidentemente, se trata de secuencias generativas, es decir, se adaptan a la
gramática de Vim: parte de la secuencia simplemente indica que la actuación
se haga sobre cierto envoltorio. Por ejemplo, en el complemento de Pope se
usaría la secuencia `cs"'` para cambiar dobles comillas por simples. La
parte `cs` sería el nuevo operador añadido a la gramática de Vim mediante
este complemento; el siguiente elemento, `"` sería el objetivo (_target_),
y, el siguiente, `'` con qué se sustituye.

Quizás podría pensar que ya es hora de que el equipo de Neovim integre una
funcionalidad como esta de forma nativa (_built-in_), pero hay razones por
las que no lo han hecho.

- Mantener compatibilidad con Vim. El proyecto Neovim nunca ha pretendido
  transformar completamente la interfaz que supone Vim. Simplemente,
  actualizarla a los tiempos modernos.

- Tree-Sitter permite hacer cosas parecidas. Una excepción a lo anterior sea
  quizás la edición basada en objetos de Tree-Sitter.

- Complejidad de la gramática. Las secuencias de _surround_ suelen ser
  `operador` + `target` + `nuevo_delimitador`, que como ve son algo más
  extensas que las que encuentra en Vim de serie.

- Conflicto con la secuencia `s` en algunos complementos. En muchos de estos
  complementos se usa como operador a `s`, lo cual "choca" con la función
  predeterminada de ese operador en Vim: equivalente a `cl`. Por tanto, se
  rompe la compatibilidad con Vim.

- Se puede hacer algo similar fácilmente desde el modo normal. Por ejemplo,
  si deseo cambiar en un texto `*itálicas*` por `_itálicas_`, puedo ir al
  comienzo de línea y desplazarme, en modo normal, al primer asterisco con
  `f*`. Si no es el primero, iré "saltando" con `;` hasta llegar a este. Una
  vez que estoy sobre el asterisco, con `s_` remplazo ese carácter por el de
  guión bajo (`_`). Luego, sigo "saltando" (`;`) hasta llegar al otro
  asterisco correspondiente. Una vez que estoy sobre este, lo remplazo del
  mismo modo pero me puedo permitir hacerlo simplemente con un punto `.`,
  pues esa sustitución es la última acción de edición que hice (no se tienen
  en cuenta los movimientos del cursor).

- En muchas ocasiones es mejor hacer un remplazo de texto usando expresiones
  regulares. Por ejemplo, `:%s/\*\(.[^*]*\)\*/_\1_/gc`. Esto nos permitirá
  hacer más rápida la sustitución en todo el archivo. Ya que hemos añadido
  `c` al final de la regla de sustitución, nos preguntará lo que deseamos
  hacer para cada uno de los _matches_.

  En lugar de hacer esta sustitución a todo el archivo, se podría aplicar
  únicamente a una parte del mismo. Simplemente se seleccionaría en modo
  visual esa parte y usar `:'<,'>s/\*\(.[^*]*\)\*/_\1_/gc`.

  Quizás habría que aclarar que esta solución no es satisfactoria para
  usuarios no avanzados, pues a simple vista esas regexes parecen
  algarabías. Sin embargo, una vez que se acostumbra a usarlas, le otorgan
  una velocidad de edición increíble además de con una precisión
  "quirúrgica".


