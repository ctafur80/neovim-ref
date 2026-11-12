---
title: "_Diffs_"
level: h2
---

En lo que respecta a los _diffs_, existen varias formas de configurarlos,
pues es algo heredado de Vim y, además, en una TUI no es fácil de programar.
Se tienen, por ejemplo, los complementos `avante.nvim`, `diffview.nvim` y
`mini.diff`. Sin embargo, Neovim en su versión 0.12 trae de serie un
complemento que se puede activar: `nvim.difftool`. Para mí es suficiente con
este último.

Lo primero que debe hacer será activarlo en su configuración. TKTK.

Luego, puede hacer algo de configuración, como lo siguiente:

```lua
vim.opt.diffopt:append("linematch:60") -- Algoritmo inteligente
vim.opt.fillchars:append({ diff = "╱" }) -- Textura visual para huecos
```

aunque tampoco es algo tan necesario.

La parte `linematch:60` lo que hace es intentar alinear líneas que se
parecen en lugar de mostrar bloques gigantes de cambios inconexos. Hace que
los _diffs_ sean mucho más "humanos", muy similar a lo que hace Zed.

Lo que no sé es si, al usar la funcionalidad de serie, no tenemos la
integración de los _diffs_ con los agentes IA de programación.

El modo _diff_ en Neovim es básicamente tener dos (o más) ventanas divididas
(_splits_) donde el editor resalta las diferencias y "conecta" el _scroll_
de ambas.

Para activar el modo _diff_ nativo, podríamos hacerlo desde el _shell_ con
algo como lo siguiente:

```
$ nvim -d archivo_viejo.js archivo_nuevo.js
```

Otra forma más interesante es invocarlo desde dentro de Neovim. Supongamos
que estamos editando con este un archivo _main.py_ y deseamos compararlo con
el archivo _main_v2.py_. Para esto, desde Neovim, con un _buffer_ editando
_main.py_, lanzamos el comando siguiente:

```vim
:vert diffsplit main_v2.py
```

Se abrirá entonces un _diff_ con ventanas a derecha e izquierda cada una con
uno de estos archivos, mostrándose el _diff_ de estos (del primero respecto
al segundo ?? TKTK).

Ahora, deberá saber moverse. Como ya sabrá, moverse de una ventana a otra se
puede hacer con la secuencia `^w ^w`. Estas ventanas vienen con pliegues
(_foldings_) de las partes que no cambian en el _diff_. Puede expandirlas si
lo desea, como se hace de forma nativa en Neovim; por ejemplo, con `zo` y
`zc` para abrirlos y cerrarlos, respectivamente.

Otra cosa que es relevante es que el movimiento en ambas ventanas está
sincronizado, cosa que es muy útil.

Puede usar las secuencias `]c` y `]c` para ir moviéndose entre cambios en el
_diff_; respectivamente, siguiente y previo.

Para aplicar un cambio, colocamos el cursor encima del mismo y, para que esa
parte de código se convierta en como se muestra en la otra ventana, pulsamos
la secuencia `do` (de _diff obtain_). Lo contrario, es decir, pasar a la
parte respectiva en la otra ventana el cambio que aparece bajo nuestro
cursor, es con `dp` (de _diff put_).

A veces, al editar mucho, el algoritmo de coloreado se lía. El comando
`:diffupdate` lo refresca.





### _Diffs_ de Git

El modo _diff_ es solo una forma de visualización. No le importa de dónde
vengan los datos, por lo que se puede usar también para los _diffs_ de Git.

- Para archivos normales: Lo usas manualmente (`:diffsplit`) para comparar
  dos versiones de un fichero que tengas en disco.
- Para Git: Aquí está la gracia. Git no tiene visor propio, delega en otros.
  Puedes configurar a Neovim para que sea tu herramienta oficial de Git.

Cómo convertir Neovim en tu "Git Diff Tool" sin plugins: Ejecuta esto en tu
terminal una sola vez:

```
$ git config --global diff.tool nvimdiff
$ git config --global difftool.prompt false
$ git config --global merge.tool nvimdiff
```

Una vez configurado esto, simplemente, cuando nos encontremos en un
repositorio de Git, con el comando

```
$ git difftool
```

se nos abra Neovim en modo _diff_ comparando TKTK.

Cierras con `:qa` y Git te abre el siguiente archivo modificado. Esto tiene
más miga de lo que parece. TKTK.

Tienes toda la razón y entiendo perfectamente tu confusión. Es
contraintuitivo si lo piensas desde la lógica de "un solo programa abierto",
pero funciona así porque **Git y Neovim son dos procesos distintos**.

Aquí te explico la "magia" de por qué `:qa` no detiene todo el proceso:



### 1. Git actúa como un "Bucle" (Shell Loop)

Cuando ejecutas `git difftool`, Git no le pasa una lista de 20 archivos a
una sola instancia de Neovim. Lo que hace Git internamente es algo parecido
a un bucle `for` en Bash.

La lógica interna de Git es esta:

1. Git detecta 3 archivos modificados: `A.py`, `B.py`, `C.py`.
2. **Iteración 1:** Git lanza el comando

   ```
   $ nvim -d A.py (versión anterior) A.py (versión nueva)
   ```

   - Tú estás dentro de Neovim. Revisas.
   - Escribes **`:qa`**.
   - Esa instancia de Neovim se cierra (el proceso muere).

3. **Git despierta:** Git detecta que el proceso de Neovim ha terminado
   exitosamente.
4. **Iteración 2:** Como ve que aún quedan archivos en la lista, Git lanza
   **una nueva instancia** de Neovim: `nvim -d B.py ...`.
5. Y así sucesivamente.

Por eso, al hacer `:qa`, cierras "la ventana del archivo actual", y Git
inmediatamente te abre la siguiente.


---


### 2. El comando vital: ¿Cómo paro el bucle? (`:cq`)

Ahora te surgirá la pregunta obvia: *"¿Y si tengo 50 archivos, reviso el
primero y me doy cuenta de que quiero cancelar todo? Si hago `:qa` 50 veces
me voy a volver loco."*

Aquí es donde entra un comando de Vim que poca gente conoce pero que es
esencial para este flujo: **`:cq`** (**C**ancel **Q**uit / **Q**uit with
error).

- **`:qa`** (Quit All): Sale devolviendo un "código de éxito" (exit code 0).
  Git piensa: "Genial, ha terminado con este, voy al siguiente".
- **`:cq`** (Cancel Quit): Sale devolviendo un "código de error" (exit code
  1). Git piensa: *"Uy, el editor ha fallado o el usuario ha abortado.
  **Rompo el bucle y paro aquí**"*.



