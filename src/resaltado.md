---
title: "Resaltado de código"
level: h3
---

Puede acceder a la ayuda de Vim sobre esta cuestión con `:help syntax`.

Si usa Neovim en un terminal (es decir, no GUI), quizás se vea limitado a
este respecto por el emulador de terminal (_terminal emulator_) que esté
empleando, pues los hay que no tienen compatibilidad con los esquemas de
colores (_color schemes_) con _truecolor_, como sucede, por ejemplo, con la
aplicación Terminal incluida de serie en macOS. En el código de los esquemas
de colores de Vim, a los colores para _truecolor_ los llaman `gui`, mientras
que a los esquemas más limitados los llaman `cli`. Para especificar a Vim a
que ponga _truecolors_, se hace con

```vim
set termguicolor
```

No he encontrado la forma de hacerlo con la API de Lua.

Lo cierto es que, por la superposición de tres tecnologías que confluyen
actualmente en Neovim a este respecto (el resaltado de código), tenemos tres
componentes a tener en cuenta a este respecto:

- Las gramáticas nativas de Vim, basadas en _regexes_.
- La integración de la tecnología Tree-Sitter, que viene de serie
  actualmente en Neovim, aunque deberá instalar las gramáticas
  individualmente (o gestionar estas instalaciones mediante un complemento).
- El resaltado semántico otorgado por LSP, en caso de que lo esté usando.

En cualquier caso, conviene explicar también los ajustes de Neovim para las
gramáticas tradicionales, basadas en expresiones regulares, pues a día de
hoy estas conviven con las de Tree-Sitter.

<!--
También está la cuestión de las gramáticas que se emplean, es decir, las
reglas que se siguen para aplicar distintos resaltados a distintas partes
del código.

Aunque pueda parecer algo muy rudimentario, la mayoría de los editores e
IDEs crean esas gramáticas mediante expresiones regulares. Es el caso, por
ejemplo, de VSCode o Sublime Text. También, Vim y Emacs traen de serie
implementada esa funcionalidad mediante expresiones regulares.

Se podría decir que actualmente el estándar _de facto_ en cuanto a las
gramáticas de resaltado de código son las de TextMate, un IDE creado por
Apple.
-->





