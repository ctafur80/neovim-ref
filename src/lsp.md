---
title: "LSP"
level: h3
---

La compatibilidad con la tecnología LSP (_language server protocol_), que
otorga cierta "inteligencia" a los editores e IDEs, y que ha alcanzado gran
popularidad en la programación en los últimos años, viene integrada de serie
en Neovim, a partir de su versión 0.5 (de Neovim). Aun así, la integración
bien hecha de la API con las funcionalidades de LSP se obtuvo a partir de la
versión 0.11, y, mejor, a partir de la 0.12.

No obstante, para que la configuración de Neovim sea más cómoda, creo que es
mejor configurar la integración de LSP en Neovim mediante el complemento
<span class="plgin">[`nvim-lspconfig`][]</span>, en lugar de hacerlo de forma directa. El
problema que soluciona este complemento es que, en principio, si configura
en Neovim la "conexión" con los servidores LSP directamente mediante la API,
tendrá que "batallar" con las distintas configuraciones particulares para
los distintos servidores LSP que vaya a usar. Estas configuraciones, como es
evidente, no cuentan con una "interfaz" unificada. Este complemento le
otorga una abstracción en la que sí le otorga una "interfaz" unificada, y,
por tanto, los ajustes para los distintos servidores LSP serán parecidos.
Por ejemplo, gracias a este no tendrá que especificar qué comando se usa
para cada servidor LSP, tampoco es necesario que especifique los _root
markers_ para los distintos lenguajes, etc. En parte, le otorga también unos
ajustes básicos sensatos de partida.

[`nvim-lspconfig`]: https://github.com/neovim/nvim-lspconfig

Lo que no hace <span class="plgin">[`nvim-lspconfig`][]</span> es instalarle o actualizarle los
servidores LSP. Estos los puede instalar mediante algún gestor de _software_
de su sistema, como Homebrew o APT; o incluso instalarlo por usted mismo
desde el código fuente (es decir, sin un paquete precompilado). Si desea que
sea el propio Neovim el que se encargue de esta tarea, puede usar el
complemento <span class="plgin">[Mason][]</span>, que se dedica a eso mismo.

[Mason]: https://github.com/mason-org/mason.nvim

También se puede configurar el autocompletado en Neovim, incluyendo las
funcionalidades de LSP en este, sin necesidad de _plug-ins_. Si prefiere
hacerlo con algún _plug-in_, creo que actualmente el mejor para esto es
<span class="plgin">[`blink.cmp`][]</span>.

[`blink.cmp`]: https://github.com/Saghen/blink.cmp

<!-- Ahora no hago uso de blink.cmp, pues creo que ha mejorado mucho el
autocompletado de serie de Neovim. -->

Puede ver [este tutorial][lsp-moderno-plugins-tuto] sobre cómo se haría una
configuración moderna de LSP en Neovim, aunque sí que usa algunos
_plug-ins_.

[lsp-moderno-plugins-tuto]: https://www.reddit.com/r/neovim/comments/1merz97/hands_down_the_easiest_lsp_setup_for_neovim_012/



---


<!-- Algunos servidores LSP proporcionan _snippets_, pero no todos. -->


Con el comando `:LspInfo` puede consultar los clientes LSP que se encuentran
activos (_active_) en su sesión de Neovim (es decir, en el proceso). Algunos
estarán ligados (_attached_) a algún o algunos _buffers_ y otros no
(_detached_). A este respecto, existen los eventos `LspAttach` y
`LspDetach`.

Por ejemplo, es muy típico crear un autocomando para lanzar el formateado de
código en el evento `LspDetach` (vea `:help LspDetach`).


Popr ejemplo, con

```vim
:lua vim.lsp.buf_attach_client(0, 1)
```

ligaríamos el cliente LSP 1 al _buffer_ en el que nos encontramos. El `id`
del cliente LSP se puede ver con `LspInfo`. De forma análoga se puede hacer
_detach_.






---

Autocompletado de LSP

Se puede consultar en la documentación oficial de Neovim con `:help
lsp-autocompletion`.

En principio, si no se ha modificado nada, el autocompletado se lanza con
<kbd>Ctrl</kbd> + <kbd>x</kbd> <kbd>Ctrl</kbd> + <kbd>o</kbd> en el modo _insert_. Esto
creo que es lo que en Vim llaman _omni completion_.

Además del autocompletado básico, si lo configura, puede tener también
autocompletado del servidor LSP que corresponda con ese _buffer_ en
particular.






Se puede crear un autocomando del evento `LspAttach` para habilitar
(_enable_) el autocompletado LSP.

<https://www.youtube.com/watch?v=tnlgQFQi2s4>

```lua
-- Enables LSP completion <https://www.youtube.com/watch?v=tnlgQFQi2s4>
vim.api.nvim_create_autocmd("LspAttach", {
    group = vim.api.nvim_create_augroup("my.lsp", {}),
    callback = function(args)
        local client = assert(vim.lsp.get_client_by_id(args.data.client_id))

        if client:supports_method("textDocument/completion") then
            vim.lsp.completion.enable(true, client.id, args.buf, {autotrigger = true})
        end
    end
})

vim.cmd("set completeopt+=noselect")
```

El ajuste que aparece al final hace que no se seleccione automáticamente,
cosa que opino que nos entorpece bastante al editar. Para moverse por el
menú desplegable con las distintas posibilidades de autocompletado puede
usar <kbd>Ctrl</kbd> + <kbd>n</kbd> y <kbd>Ctrl</kbd> + <kbd>p</kbd>, o con las flechar
arriba y abajo, si lo prefiere.

Al moverse por estas, sí se seleccionará en la que se encuentre, aunque no
de forma acumulativa. Otra forma de que se añada al _buffer_ uno de estos
posibles autocompletados del menú desplegable es con la combinación
<kbd>Ctrl</kbd> + <kbd>y</kbd>.




---

_inlay hints_





---





La buena noticia es que esto está comenzando ya a cambiar; sobretodo, desde
la versión 0.11. Ahora resulta más cómodo hacer la gestión de LSP por uno
mismo en Neovim. Una explicación bastante buena está en [un
artículo][anders-configurar-lsp] del blog de Gregory Anders.

[anders-configurar-lsp]: https://gpanders.com/blog/whats-new-in-neovim-0-11/

He visto que en YouTube también hay algunos tutoriales a este respecto, como
[el de TJ DeVries][devries-tuto-lsp], que no está mal.

[devries-tuto-lsp]: https://www.youtube.com/watch?v=bTWWFQZqzyI

Veamos lo básico sobre cómo se configuraría sin _plug-ins_. El _framework_
de Lua para la gestión de LSP es `vim.lsp`. Por ejemplo, para configurar de
forma directa la comunicación de Neovim con el servidor LSP de Python
`ruff`, se podría añadir lo siguiente a la configuración:

```lua
vim.lsp.start({
    name = "python-ruff",
    cmd = { "ruff", "server" },
    root_dir = vim.fs.dirname(
        vim.fs.find({ "setup.py", "pyproject.toml", ".git" }, { upward = true })[1]
    ),
```

Puede consultar `:help vim.lsp.start` para aprender el comportamiento de
dicha función.

Tiene que averiguar cuál es el comando con el que se arranca ese servidor
LSP en concreto. En este ejemplo, es `ruff server`. Para cada servidor LSP
puede ser diferente.

Por cierto, como es evidente, al contrario de lo que sucede con los
_plug-ins_ de LSP, al hacer la gestión de forma directa (es decir, sin uso
de _plug-ins_), deberá instalar por usted mismo el servidor LSP en su
sistema. Es fácil: se suele encontrar en los principales gestores de
instalación, como Homebrew, APT, Nix, etc.

Lo normal es introducir esa orden de inicio del servidor LSP en un
autocomando, para que se lance únicamente cuando sea necesario. Así, mejor
que lo anterior, sería

```lua
vim.api.nvim_create_autocmd("FileType", {
    pattern = "python",
    callback = function()
        vim.lsp.start({
            name = "python-ruff",
            cmd = { "ruff", "server" },
            root_dir = vim.fs.dirname(
                vim.fs.find({ "setup.py", "pyproject.toml", ".git" }, { upward = true })[1]
            ),
        })
    end
})
```

**Nota sobre Neovim 0.12**: En la versión 0.12 se introducirá la función `vim.lsp.server()`,
que simplificará aún más la configuración de servidores LSP. Esta función estará
diseñada para reducir la cantidad de código repetitivo y ofrecer una forma más
declarativa y sencilla de registrar configuraciones de servidores, basándose en
las configuraciones ya conocidas por la comunidad (similar a como lo hace `nvim-lspconfig`,
pero de forma nativa).

Para comprobar si está todo configurado correctamente, use el comando
`:checkhealth lsp`.













---


`:K` muestra la documentación sobre el token en el que se encuentra el
cursor.




<kbd>Ctrl</kbd> + <kbd>o</kbd> salta hacia atrás en el historial de posiciones del
cursor.













