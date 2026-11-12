---
title: "1. El Arquitecto (El Parser / `grammar.js`)"
level: h3
---

* **Lo que hace:** Crea la estructura física (el AST).
* **Salida:** **NODOS** (`paragraph`, `link`, `list_item`).
* **¿Es modificable?** **NO**. Es código C compilado. Es inmutable (salvo que seas el desarrollador del plugin).
* **Herramienta para verlo:** `:InspectTree`. (Aquí ves el "esqueleto").

### 2. El Decorador (Las Queries / `highlights.scm`)

* **Lo que hace:** Selecciona nodos y les aplica lógica extra (Regex, predicados).
* **Salida:** **CAPTURAS** (`@markup.note`, `@footnote.definition`, `@pepito`).
* **¿Es modificable?** **SÍ**. Aquí es donde tú tienes el poder total.
* Puedes decir: "Coge el nodo `paragraph`, pásale este filtro regex, y si cumple, etiquétalo como `@mi.captura`".


* **Herramienta para verlo:** `:Inspect` (Aquí ves la etiqueta ganadora).

---

### Tu superpoder actual

Ahora entiendes que **no necesitas esperar a que alguien actualice la gramática de Markdown** para soportar Pandoc.

Tú mismo estás haciendo de "puente":

1. El parser te da un bloque genérico ("Esto es un Párrafo").
2. Tú usas una Regex en tu query ("¿Empieza por `[^...]:`?").
3. Tú creas una semántica nueva ("Entonces es una `@footnote.definition`").

### Propuesta final para graduarte

Ya tienes las **Notas al Pie** (`[^1]`) dominadas.
Para confirmar que dominas el sistema al 100%, ¿te gustaría aplicar esta misma lógica para **las Citas Bibliográficas de Pandoc** (`[@autor, p. 30]`)?

El problema es idéntico: Tree-sitter las ve como texto normal o enlaces rotos, pero con tu nueva técnica podrías detectarlas y colorearlas. ¿Te animas?
