---
title: "Historial de comandos"
level: h2
---

Con la secuencia `q:` se puede acceder al historial de comandos. Aparece
abajo en forma de ventana _quickfix_ (la posición la podemos cambiar en la
configuración, evidentemente).

Entramos directamente en el modo _normal_, con lo que nos podemos mover como
siempre en este. Para salir, podemos cerrar la ventana introduciendo en modo
_insert_ `:q`, es decir, como se cierra cualquier ventana, pues al fin y al
cabo se trata de eso mismo. Alternativamente, se puede salir se lo prefiere
con <kbd>Ctrl</kbd> + <kbd>c</kbd> <kbd>Ctrl</kbd> + <kbd>c</kbd>.

También, se puede acceder al historial de búsquedas, con `q/`.

Para abrir la ventana _quickfix_, se hace con `:copen`. En esta se muestran
la lista de errores de compilación, los resultados de `grep` y los errores y
advertencias (_warnings_) de los _linters_. No guarda comandos.



