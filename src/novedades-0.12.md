---
title: "Novedades en Neovim 0.12"
level: h3
---

La versión 0.12 de Neovim, aunque todavía en desarrollo, se perfila como un
lanzamiento fundamental bajo el lema "El año de Nvim fuera de la caja" (_out
of the box_, OOTB). El objetivo es mejorar significativamente la experiencia
de usuario desde el primer momento, preparando el terreno para la futura
versión 1.0.

A continuación, se describen algunas de las características y mejoras más
esperadas.

- **Gestor de complementos nativo**. Una de las adiciones más anticipadas es
  un gestor de complementos (_plugins_) integrado en el propio Neovim. Esto
  podría simplificar enormemente la instalación y gestión de complementos,
  eliminando la necesidad de gestores de terceros, como `lazy.nvim`, para
  configuraciones sencillas.

- **Mejoras en la asincronía: `vim.async`**. Se introducirá una nueva
  abstracción para tareas asíncronas con `vim.async`. Esto proporcionará una
  base más sólida y estructurada para la concurrencia, permitiendo que los
  complementos y la propia configuración manejen operaciones en segundo
  plano de forma más eficiente y robusta.

- **Mejoras en la interfaz de usuario (UI)**. Se planean varias mejoras en
  la interacción con la interfaz de usuario:

  + **Comando `:restart`**: Permitirá reiniciar el servidor de Neovim sin
    necesidad de cerrar y reabrir el cliente. Esto facilitará la aplicación
    de cambios en la configuración de manera casi instantánea.

  + **Eliminación del mensaje "Press ENTER"**: Se buscará reducir las
    interrupciones que pausan el flujo de trabajo y requieren que el usuario
    presione la tecla <kbd>Enter</kbd> para continuar.

- **API para imágenes**. Se está desarrollando una nueva API estándar para
  manejar y mostrar imágenes directamente en los _buffers_ de Neovim,
  abriendo la puerta a nuevas funcionalidades en visores de archivos,
  previsualizaciones y otros complementos.

- **Multicursor y supermacros**. Se esperan mejoras en la funcionalidad de
  multicursor nativa y en el sistema de macros, permitiendo ediciones
  complejas de manera más fluida e intuitiva. Finalmente, los multicursores
  no se han llegado a presentar en la versión 0.12, pero tampoco me parece
  algo tan relevante. Por lo que dice Justin Keyes, saldrá en la versión
  siguiente.

Otra cosa muy interesante que trae de serie Neovim 0.12 son tres paquetes
que se pueden activar: `undotree`, `tohtml` y `difftool`. Puede ver [este
tutorial](https://www.youtube.com/watch?v=DvyPGFL3EU0).

También, está bastante bien la [selección
incremental](https://www.youtube.com/watch?v=97F0f2MyXyY) que han añadido.
Esta sí que supone un cambio respecto al modo normal en Vim, pero siguiendo
su misma filosofía.

Está bien [esta _playlist_][neovim-0-12-playlist] en YouTube.

[neovim-0-12-playlist]: https://www.youtube.com/watch?v=na0Z6SZ94CM&list=PLkblEmO-k3FfYvM9bRrhC13hd0vt-gvo4


