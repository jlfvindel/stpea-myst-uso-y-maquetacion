---
title: Qué es MyST y cómo se instala
short_title: Qué es MyST
label: que-es-myst
---

**MyST** (*Markedly Structured Text*) es una forma de escribir documentos técnicos y docentes en texto plano. Parte de Markdown, el formato de marcas ligero que muchas plataformas ya usan, y le añade lo que un material docente necesita: avisos, figuras numeradas, ecuaciones, referencias cruzadas, ejercicios, glosarios…

Con esos ficheros de texto, el programa `myst` produce:

- un **sitio web** navegable, con menú, buscador y vistas previas de los enlaces;
- documentos **PDF** (a través de LaTeX o de Typst) y documentos **Word**.

Todo sale de los mismos ficheros. Se escribe una vez y se publica en varios formatos.

:::{seealso} Documentación oficial
La guía de MyST está en <https://mystmd.org/guide>. Para dudas concretas, lo más útil suele ser su índice de directivas (<https://mystmd.org/guide/directives>).
:::

## Instalación

MyST funciona sobre **Node.js**. MyST 1.13 necesita la versión 22 o superior. Si no lo tienes, descárgalo de <https://nodejs.org> (la versión LTS). Este proyecto se ha probado con Node.js 22 y MyST 1.13.0.

Después, en una terminal, instala MyST de una de estas dos formas:

::::{tab-set}
:::{tab-item} Con npm (Node.js)
```bash
npm install -g mystmd
```
:::
:::{tab-item} Con pip (Python)
```bash
pip install mystmd
```
Esta vía instala MyST desde Python, pero sigue necesitando Node.js.
:::
::::

Comprueba que funciona:

```bash
myst --version
```

## Uso en la línea de comandos

Todo se hace con el programa `myst`, seguido de una orden. Siempre se ejecuta **desde la carpeta del proyecto**, la que contiene `myst.yml`.

| Orden | Qué hace |
|---|---|
| `myst init` | Convierte la carpeta actual en un proyecto MyST: crea un `myst.yml` inicial |
| `myst start` | Construye el sitio y lo sirve en <http://localhost:3000>; se actualiza al guardar |
| `myst build --html` | Genera el sitio web estático en `_build/html` |
| `myst build --pdf` / `--typst` / `--docx` | Genera las exportaciones declaradas en `myst.yml` |
| `myst clean` | Borra los resultados generados (`_build`) |
| `myst --help` | Muestra todas las órdenes y opciones |

Cada orden tiene su propia ayuda, por ejemplo `myst start --help`.

## Las piezas de un proyecto

Un proyecto MyST es una carpeta con:

`myst.yml`
: La configuración: título, autoría, licencia, índice de páginas y aspecto del sitio. La página [](#ejecutar) muestra la de este proyecto.

Ficheros `.md`
: Las páginas. Cada una empieza con un bloque de configuración propio, el *frontmatter*, entre dos líneas `---`.

Por ejemplo, el frontmatter de esta página es:

```yaml
---
title: Qué es MyST y cómo se instala
short_title: Qué es MyST
label: que-es-myst
---
```

`title` es el título grande de la página. `short_title` es el texto que aparece en el menú lateral y en los botones de anterior y siguiente. `label` es un nombre que permite enlazar la página desde otras (se tratará en el proyecto 3).

:::{tip} Para explorar más
- La guía de inicio rápido de MyST: <https://mystmd.org/guide/quickstart>.
- La lista de campos del frontmatter: <https://mystmd.org/guide/frontmatter>.
:::
