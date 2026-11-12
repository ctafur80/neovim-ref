---
title: "Remapeo de teclas"
level: h3
---

Es común entre la gente que usa Vim o Neovim configurar un remapeado (o
remapeo, _remap_) de algunas teclas, principalmente, de teclas modificadoras
o de <kbd>Esc</kbd>, que es la tecla que más se usa en Vim y se encuentra en un
lugar algo inaccesible; algo alejada de la línea de reposo del teclado.

Entre las opciones de remapeo de <kbd>Esc</kbd>, las más populares son
asignarla a <kbd>Bloq May</kbd>, pues es una función que para mucha gente está
ya obsoleta; no para mí. Otra opción es, en modo insertar, la secuencia
<kbd>j</kbd> <kbd>k</kbd>, porque son teclas que están en la _home row_ y, tanto
en español como en inglés, casi no hay palabras que contengan el dígrafo
_jk_. Esta última opción tiene un inconveniente: tiene que usarla en modo
insertar, tal y como hemos dicho, por lo que no sirve para salir del modo
visual. En ese caso, tendría que emplear [otras
alternativas](https://vi.stackexchange.com/a/22751/22600), como, por
ejemplo, con la combinación <kbd>Ctrl</kbd> + <kbd>c</kbd> o pulsando otra vez
<kbd>v</kbd> o <kbd>V</kbd>. En caso de querer remapear <kbd>Esc</kbd> por <kbd>j</kbd>
<kbd>k</kbd>, tendrá que poner en el archivo de configuración lo siguiente:

```vim
inoremap jk <esc>
" jk as <Esc> in insert mode; jk as TODO TKTK in terminal
" tnoremap jk <C-\><C-n>
```

También, hay quien hace que la secuencia al revés haga de <kbd>Esc</kbd>, es
decir, <kbd>k</kbd> <kbd>j</kbd>.

Otros prefieren remapear la tecla <kbd>Bloq May</kbd> para que tenga la función
de <kbd>Ctrl</kbd>. Por ejemplo, es cómodo para quienes usan el multiplexor de
terminal Tmux cuando hacen que la combinación básica de este sea
<kbd>Ctrl</kbd> + <kbd>a</kbd>. Aun así, esto no me convence. Hacer que <kbd>Bloq
May</kbd> sea una tecla modificadora creo que no tiene mucho sentido, pues
está en un lugar que no es ergonómico, pues, al acceder a esta, me descoloca
la posición de los demás dedos de la mano izquierda.

También, está la cuestión de la ergonomía. Lo primero que me gustaría decir
es que la disposición qwerty no es nada ergonómica. De hecho, se ideó para
evitar que las TKTK de las máquinas de escribir quedasen atascadas. Por
tanto, por estadística, con la lengua inglesa, lo normal es que con este
tipo de teclados se encuentre continuamente alterando las teclas TKTK.

Existen otras disposiciones que están alcanzando cierta popularidad, como la
dvorak o la colemak. TKTK. El problema es que, en estas disposiciones, ya no
se tienen juntas las teclas para moverse: <kbd>h</kbd> <kbd>j</kbd> <kbd>k</kbd>
<kbd>l</kbd>. Hay quien no ve en esto un inconveniente. Dicen que puedes
interiorizar rápidamente las nuevas posiciones de esas teclas. Quizás sea
cierto y no haya ninguna razón por la que esas cuatro teclas tengan que
estar juntas. Una disposición más natural sería con una disposición
triangular, como la de las teclas de flecha del teclado.

También, está la cuestión de los teclados ergonómicos TKTK.

Todo esto, al igual que sucede con el uso de Vim y Neovim, me hace
plantearme si merece la pena configurar algo a mi gusto o, si por el
contrario, debería seguir el lema de "_convention over configuration_".


