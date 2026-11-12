---
title: "Estilo de código"
level: h2
---

Entender la diferencia entre las distintas formas de "dar formato" en Neovim
es una de las dudas más comunes, ya que históricamente Vim ha manejado el
texto y el código de maneras separadas. Por su parte, en Neovim actualmente
se están comenzando a usar funcionalidades sobre el formateado o estilo de
código más modernas que las que tradicionalmente ha incorporado Vim.



### Reajuste de texto (`gq`) {#reajuste-texto}

El comando `gq` es una herramienta clásica heredada de Vim diseñada
principalmente **para prosa y comentarios**. A esta acción de edición se la
conoce como _reajuste de texto_ (_text reflow_).

Lo que hace es tomar un bloque de texto y lo "rompe" o une para que encaje
en un ancho de línea específico, determinado por la opción `textwidth`; por
ejemplo, 80 caracteres. Si una línea es muy larga, la divide; si son muy
cortas, las agrupa.

Advierta que, por tanto, esta funcionalidad se aplica cuando tiene activo el
_hard wrapping_. No tendría efecto para un archivo con _soft wrapping_.

Se usa normalmente al escribir documentación; no código. Es decir, está
pensada para archivos Markdown, correos electrónicos, o bloques de
comentarios largos en código.

Internamente usa las reglas predefinidas de Neovim, especificadas en el
parámetro `formatoptions`, aunque también se puede especificar un _script_
externo con las reglas. Esto último se configuraría en el parámetro
`formatprg`.

En Neovim moderno, se puede modificar el funcionamiento de esta secuencia
`gq` para que, en lugar de hacer uso de las funcionalidades de serie de
Neovim o un _script_ "casero", use un formateador externo integrado en un
servidor LSP, cosa bastante común hoy en día. Estos formateadores suelen ser
más "ambiciosos" que estos _scripts_ de Vim y Neovim (Vea la [sección sobre
formateadores de código](#format).)




### Sangría (`=`)

El comando `=` es otra funcionalidad clásica de Vim, que existía antes del
nacimiento de Neovim. Su propósito es exclusivamente corregir la sangría, es
decir, los espacios o tabulaciones al principio de la línea. A la sangría a
veces la llaman _indentación_, al copiar del inglés _indentation_.

Al contrario que el [reajuste de texto](#reajuste-texto), el comando de
sangría se suele usar para código; no para documentación. Es decir, no está
pensado para formatos como Markdown o para comentarios dentro del código.

Las únicas reglas de estilo que tiene en cuenta esta funcionalidad son sobre
la sangría. No va a hacer cosas como añadir o quitar saltos de línea, ni
cambiará comillas simples por dobles; solo mueve el código a la izquierda o
a la derecha.

Es típico usarlo cuando pegamos un bloque de código que se ha desalineado y
queremos arreglar rápidamente sus márgenes izquierdos.

En versiones recientes como Neovim 0.12, el comando `=` se apoya enormemente
en Tree-Sitter para calcular la sangría perfecta de forma nativa e
instantánea, reemplazando a los antiguos _scripts_ basados en expresiones
regulares, como los que se especificaban en la opción `indentexpr`.

El equivalente a la opción `formatprg` para el sangrado es `equalprg`.




### Formateo de código (`:Format`) {#format}

Esta herramienta es más moderna que las otras dos. En Neovim puro (sin
configurar), **el comando `:Format` no existe por defecto**. Es un comando
que típicamente añaden los usuarios o los complementos. El estándar a este
respecto podría decirse que es el complemento `conform.nvim`, que es común
que se encuentre integrado en distribuciones como LazyVim o Kickstart.

Lo que hace es modificar la **estructura completa** de un archivo de código
mediante el uso de una herramienta externa profesional, como Prettier para
código JavaScript o TypeScript, Black para Python o Stylua para Lua. Es más
ambicioso que el reajuste de texto y la modificación del sangrado, aunque
también suelen incluir reglas sobre estos dos ámbitos. Debido a esto, es
lógico pensar que sirven tanto para formatos de documentación (Markdown,
etc.) como para código (JavaScript, etc.).

Entre las reglas de estilo de estos formateadores se encuentran cambiar
comillas, añadir o quitar punto y coma, reorganizar importaciones, ajustar
espacios alrededor de operadores matemáticos, romper parámetros largos en
varias líneas y, por supuesto, también arreglar la sangría.

Tradicionalmente, el problema de las herramientas externas puras era que
obligaban a aplicarlas sobre todo el archivo que estamos editando: es decir,
no podemos ordenarle actuar únicamente sobre una parte que seleccionemos en
modo visual. Sin embargo, hoy en día los servidores LSP modernos soportan el
**formateado de rangos** (_range formatting_).

En realidad, no tenemos que "irnos" a formateadores propiamente dichos, sino
que es bastante común hoy en día que servidores LSP integren de serie un
formateador. Es lo que sucede, por ejemplo, con `ruff`, que es un _linter_
(analizador de código estático) para Python que además cuenta con un
formateador, o `gopls` para Go.

Hoy en día, esto llama a la API nativa de Neovim `vim.lsp.buf.format()` o a
un formateador asíncrono. Lo que hacen es leer las reglas estrictas del
proyecto en cuestión y reescribir el _buffer_ para que cumpla lo que se ha
especificado; es decir, con las reglas de estilo especificadas en algún
archivo compatible con el formateador en concreto.

Para formatear el archivo actual sin _plugins_, solo se tiene que ejecutar
este comando de Lua:

```vim
:lua vim.lsp.buf.format()
```

Tal y como decimos, este comando aplicaría las reglas de estilo
especificadas al _buffer_ actual, es decir, a todo un archivo. Es bastante
común actualmente que, si lo deseamos, podamos aplicar el formateado
únicamente sobre una selección visual. Para esto, el formateador (quizás
integrado dentro de un servidor LSP) debe tener la funcionalidad de
formateado de rangos. Para ordenar el formateado
sobre una selección visual, se haría con:

```vim
:'<,'>lua vim.lsp.buf.format()
```

En este caso, Neovim enviará al formateador únicamente el rango de líneas
seleccionado.

Tal y como dijimos, los formateadores (como Prettier, Black o Clang-format)
son binarios externos. Neovim tiene un puente "clásico" para usarlos sin Lua
y sin complementos mediante la opción `equalprg`, es decir, el parámetro que
indica qué _software_ gobierna el sangrado, que se "lanza" con `=` en el
modo normal. De forma predeterminada, este _software_ es muy básico.
Podríamos especificar que use un formateador externo.

Por ejemplo, si nos encontramos editando un archivo de C++, podemos
ejecutar:

```vim
:set local equalprg=clang-format
```

Ahora, al pulsar `gg=G` en modo normal, Neovim pasará todo el archivo por el
formateador `clang-format` y sustituirá el texto por el resultado.
Alternativamente, si el formateador lo soporta, se podría seleccionar en
modo visual parte del código y con `=` se formatearía solo esa parte.

Si no quieres escribir el comando de Lua cada vez, puedes añadir esta línea
a tu _init.lua_. Esto no es un complemento, sino simplemente una
configuración personal:

```lua
-- Crear el comando :Format manualmente
vim.api.nvim_create_user_command('Format', function()
    vim.lsp.buf.format { async = true }
end, {})
```

Ahora ya tenemos nuestro comando `:Format` disponible de forma "nativa".

También, podríamos asignarle una secuencia en el modo normal; por ejemplo,
usando la _leader key_.



#### Automatizar el formateo al guardar (_format on save_) {#format-on-save}

Una vez que entendemos que `vim.lsp.buf.format()` es la función clave en el
Neovim moderno para dar estilo al código, el paso natural para muchos
usuarios es automatizar este proceso. En lugar de ejecutar el comando
`:Format` o usar una _leader key_ manualmente, podemos instruir a Neovim
para que formatee el código justo una fracción de segundo antes de guardar
el archivo en el disco.

Esto se logra en Neovim creando un autocomando (_autocmd_) que escuche el
evento `BufWritePre` (que se dispara justo antes de escribir el _buffer_).

Añadiendo el siguiente fragmento a su `init.lua`, conseguirá este
comportamiento sin necesidad de instalar ningún complemento externo:

```lua
-- Formatear automáticamente antes de guardar
vim.api.nvim_create_autocmd("BufWritePre", {
    pattern = "*",
    callback = function(args)
        vim.lsp.buf.format({ bufnr = args.buf, async = false })
    end,
})
```

Aun así, no todo el mundo quiere delegar tanto el formateado de código, pues
las reglas de estilo que tiene en su cabeza no se corresponden de forma
fidedigna con las especificadas o las que puede usar ese formateador. El
estilo para código, al igual que sucede con el de la literatura, en muchas
ocasiones es algo bastante personal. Es decir, aunque hay cosas básicas en
las que se puede decidir sobre el estilo de forma sencilla, muchos creadores
tienen en su cabeza reglas bastante complejas pero que para ellos son
totalmente coherentes.



