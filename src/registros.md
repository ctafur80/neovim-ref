---
title: "Registros"
level: h3
---

Creo que el mejor tutorial sobre el uso de registros es
[este](https://www.youtube.com/watch?v=I5QGlfbuCfs).

Lo primero que debe conocer es el comando para consultar todos los registros
que tiene en ese instante. Dicho comando es `:registers` o, de forma
abreviada, `:reg`.

Al lanzarlo, le aparecerá una ventana emergente con una lista con todos los
registros que tiene. Los nombres de los registros comienzan siempre por un
signo de comillas dobles (`"`). Tras dicho signo, el nombre será un número,
una letra o algún otro signo. Según el tipo de carácter que acompañe a las
comillas dobles, el registro tendrá un significado, que explicamos más
adelante.

Para acceder a un registro, la forma de hacerlo dependerá del modo en el que
se encuentre. Si está en modo normal, tendrá que poner el nombre del
registro seguido de la acción que desee realizar sobre este. Por ejemplo,
para pegar en el texto el registro con nombre `"1`, será tan sencillo como
introducir <kbd>”</kbd> <kbd>1</kbd> <kbd>p</kbd> (es decir, `"1p`).

Otro ejemplo, para copiar en el registro `a` la palabra en la que se
encuentra el cursor en modo normal, sería <kbd>”</kbd> <kbd>a</kbd> <kbd>y</kbd>
<kbd>i</kbd> <kbd>w</kbd> (o sea, `"ayiw`).

Para pegar el contenido de registro, cuando nos encontramos en modo insert,
se debe anteponer al designador del registro la combinación <kbd>Ctrl</kbd> +
<kbd>r</kbd>. Por ejemplo, para pegar el contenido del registro 1, <kbd>Ctrl</kbd>
+ <kbd>r</kbd> <kbd>1</kbd> (`^r1`).


* * * *


Debe saber también que el registro `""` es el registro sin nombre (_unnamed
register_). Cuando copia algo con <kbd>y</kbd> <kbd>y</kbd> (`yy`), el texto que
ha copiado aparecerá en el registro sin nombre.

En realidad, son más acciones las que almacenan datos en el registro sin
nombre. Todo lo que se haga con `d`, `c`, `s`, `x`, `y`; y sus versiones en
mayúsculas. Por su parte, `p` y `P` pegan lo que hay en el registro sin
nombre; no es necesario especificar el designador del registro.

Según la acción de estas que realice, además del registro sin nombre, se
almacenará esa información en otro registro. Por ejemplo, si hace `dd` sobre
una línea de texto, también se almacenará en el registro 1. Si hace `yy`, en
el 0.

Conforme vaya borrando más cosas, estas irán apareciendo en el
registro 1 y, la que estaba antes en dicho registro, se pasa al 2. Luego, en
el siguiente borrado, se pone en el 1 y lo que había en el 1 se pasa al 2 y
lo que había en el 2 al 3. Y así sucesivamente hasta el 9.

Lo único que tiene que tener en cuenta con esto es que hay ciertos
movimientos que hacen que no cuente como una operación de borrado. Por
ejemplo, `%`, `( )`, etc.


* * * *


En lo que respecta a los registros que se identifican con una letra (en
total, se tienen 26), ahí se almacenan automáticamente, por ejemplo, los
\[macros\] que creamos. El identificativo del macro en realidad se refiere
al del registro donde se almacenará. Sabiendo esto, podremos editar un macro
si nos equivocamos al construirlo, sin necesidad de reconstruirlo por
completo desde el principio.

Un macro se editaría haciendo lo siguiente. Suponga que nos referimos al
macro en el registro `a`. Entonces, tendríamos que hacer

```vim
let @a=''
```

y poner entre esas comillas lo que deseemos introducir. Pero si el macro ya
lo había creado, puede poner su cursor entre las comillas e insertar el
contenido como ya hemos dicho cuando está en modo insert (<kbd>Ctrl</kbd> +
<kbd>r</kbd> <kbd>a</kbd>). Luego, sobre eso, hará las modificaciones que desee.
Debe tener también en cuenta que ahí aparecerá la orden de la tecla
<kbd>Esc</kbd> como ``, que, aunque se parezca a un gorro seguido de apertura
de corchetes, `^[`, no lo es. El símbolo que queremos se introduce, en modo
insert, con <kbd>Crtl</kbd> + <kbd>v</kbd> <kbd>Esc</kbd>.

Registros de solo lectura.



