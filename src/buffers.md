---
title: "Los _buffers_"
level: h3
---

En el canal de YouTube de Systematician hay un buen [tutorial
actualizado][tuto-buf-win-tag] sobre los _buffers_. También, puede leer
[este artículo][articulo-buffers-ventanas-1] o [este otro
vídeo][tuto-buffers-tabs-2].

[tuto-buf-win-tag]: https://www.youtube.com/watch?v=mhwFafnqO_g
[articulo-buffers-ventanas-1]: https://medium.com/@paulodiovani/vim-buffers-windows-and-tabs-an-overview-8e2a57c57afa
[tuto-buffers-tabs-2]: https://www.youtube.com/watch?v=sK6HR9lzgU0&pp=ugUEEgJlbg%3D%3D

Los _buffers_ tienen mucha relación con los conceptos de _ventana_
(_window_) y _tab_, pero debe tener cuidado con estos ya que no significan
lo mismo que en otro _software_, incluyendo a otros editores e IDEs como
VSCode. Personalmente, los que no uso son los _tabs_, ya que prefiero
limitarme a los otros dos.

La base de la edición en Vim y sus derivados son los _buffers_. Tal y como
explican en la entrada `buffer` en la documentación oficial de Neovim (`:h
buffer`), **un _buffer_ es el texto en memoria de un archivo**, aunque no
tiene por qué estar mostrándose en el editor. Por tanto, en una sesión de su
uso de Neovim se pueden tener varios archivos abiertos en _buffers_, aunque
solo se esté mostrando uno. Se mostrarán en una ventana. Se podría decir que
**una ventana es un _viewport_ de un _buffer_**.

Al editar cualquier archivo en Neovim, en el momento en el que esté viendo
desde el mismo algún archivo, ya tendrá al menos un _buffer_ en esa sesión
del editor. Con el comando `:buffers` o `:ls` se muestran los _buffers_ en
dicha sesión del editor. Se muestra como un mensaje emergente que se cierra
al pulsar cualquier tecla.

En la lista de los que muestra, se ve en la primera columna un número
identificativo del _buffer_. En la tercera, aparece entrecomillada la ruta
del archivo de dicho _buffer_, relativa a la raíz, es decir, desde donde
abrió el editor.

También se muestran en algunos _buffers_, pegadas a los datos de la primera
columna, algunas marcas. Por ejemplo, la marca `a` indica que se trata del
_buffer_ activo (_active buffer_), cosa que quiere decir que es el que se
está mostrando en esa ventana. La marca `#` indica que se trata del _buffer_
alternativo (_alternate buffer_), que quiere decir que es el último _buffer_
abierto en esa misma ventana, antes del que actualmente es el activo.

Para moverse entre _buffers_, con `:buffer next` o, mejor, `:bn`, se moverá
al siguiente _buffer_ en la lista de estos. Con `:buffer previous`, o,
mejor, `:bp`, al anterior. Es decir, se moverá a los _buffers_ adyacentes en
la lista. Pero quizás le interese más alternar entre el _buffer_ actual y el
activo. Esto se hace simplemente con `:buffer #` o abreviadamente con `:b#`.
Esto último es algo que uso mucho. Concretamente, accedo a este de forma
rápida y cómoda desde el histórico de comandos del editor, como con `:` y
luego <kbd>Ctrl</kbd> + <kbd>p</kbd> hasta llegar a dicho comando, y luego
pulsando <kbd>Enter</kbd>.

También, puede acceder a cualquier _buffer_ de un modo bastante cómodo
usando el comando `:buffer`, o, mejor, `:b`, pero usando como argumento
parte del nombre del archivo de un _buffer_ tal y como se listan al
consultarlos. Así, por ejemplo, si tiene en un _buffer_ un archivo
_makefile_, con `:b mak` lo abriría rápidamente en la ventana. También
podría usar _tab-completion_ si lo prefiere.

Respecto al _tab-completion_ en Vim, puede usar comodines (_wildcards_),
como, por ejemplo, asteriscos, `*`.

Para cerrar un _buffer_, debe abrirlo en una ventana y, desde ahí, uso el
comando `:bde` (o su forma larga: `:bdelete`), o incluso sin llegar a
abrirlo: simplemente, introduce su nombre de archivo como argumento del
comando `:bd`.

<!-- Buffers no listados. Se muestran con `:ls!` -->


División de ventanas

En realidad, puede ver simultáneamente más de un _buffer_, es decir, no hay
por qué tener una sola ventana abierta en un momento dado. Así, por ejemplo,
puede dividir la interfaz de Neovim en dos ventanas verticales que muestren
un mismo _buffer_, o que muestren _buffers_ distintos; lo que usted
prefiera. Aunque lo segundo quizás haya visto hacerlo, lo primero también
puede ser muy útil cuando se trata de un _buffer_ bastante extenso o con una
especie de índice en su interior.

Cuando entra a Neovim, tendrá abierta una ventana. Si prefiere tener dos
ventanas verticales, tendrá que usar el comando `:vsplit`. Si prefiere que
se abra una ventana en horizontal, sería con `:hsplit`. Para moverse por las
ventanas, se usan atajos de teclados compuestos que usan como prefijo
<kbd>Ctrl</kbd> + <kbd>w</kbd>. Así, por ejemplo, para pasar a la ventana de la
derecha, puede usar <kbd>Ctrl</kbd> + <kbd>w</kbd> <kbd>l</kbd>. Recuerde que la
tecla <kbd>l</kbd> se usa normalmente para moverse a la derecha, así que estos
atajos de teclado tratan de mantener la coherencia con las otras funciones
asociadas a teclas en Neovim. Otro atajo de ventanas que uso bastante es
<kbd>Ctrl</kbd> + <kbd>w</kbd> <kbd>Ctrl</kbd> + <kbd>w</kbd>, que va cambiando a otra
ventana, hasta llegar a la última y, entonces, volver a la primera. Como el
máximo número de ventanas que uso son 2, este comando me resulta cómodo y
fácil de usar sin pensar.

Para cerrar una ventana, se hace con `:q` (o su forma larga: `:quit`). Debe
tener cuidado de que, si solo tiene abierta una ventana, al usar `:q` se
cerrará el propio Neovim.

Algo que suelo usar, cuando estoy editando un archivo con bastantes líneas,
es abrir una ventana para algún _buffer_. Uso el comando `:vsplit`. Luego,
con <kbd>Ctrl</kbd> + <kbd>w</kbd> <kbd>Ctrl</kbd> + <kbd>w</kbd> me muevo entre
ventanas. Así, puedo ir "saltando" entre dos partes bastante separadas de un
mismo archivo, cosa que me hace más cómoda la edición. Otra opción sería el
uso de [marcas], pero sería algo más incómoda.

Además, en relación a esto, también existe el concepto de _pestaña_ (_tab_).
Hace alusión simplemente a la forma de agrupar las ventanas. Es decir, una
pestaña es una agrupación de ventanas. Como ve, el concepto es algo distinto
al de las pestañas de las aplicaciones de tipo GUI.

Personalmente, no le doy uso a las pestañas del editor. Lo que hago es usar
instancias distintas del editor.

Existen los comandos `:tabnew`, `:tabnext`, `:tabprevious`, `:tabclose`,
etc., asociados a las acciones que imagina. El comando `:tabnext` se puede
lanzar también con la secuencia <kbd>g</kbd> <kbd>t</kbd> en el modo normal.





<!-- Hacer que desaparezcan las demás ventanas de la vista: `:only`. -->


<!-- También tiene relación con esto los comandos sobre los argumentos, como
`:args`. -->




