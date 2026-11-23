---
title: Exportar a una web, a PDF y a Word
short_title: Exportar
label: exportar
---

`myst start` sirve el sitio solo en tu ordenador. Para compartir el material hay que **exportarlo**: generar ficheros que se puedan copiar a un servidor, subir al aula virtual o enviar. Todas las exportaciones se hacen con `myst build` y dejan el resultado en la carpeta del proyecto.

## Sitio web estático

```bash
myst build --html
```

Genera la carpeta `_build/html`: un sitio web completo, hecho solo de ficheros (HTML, CSS, JavaScript, imágenes). No necesita MyST ni ningún programa especial en el servidor. Basta con un servidor web que entregue ficheros, como Apache.

### Probarlo antes de subirlo

El sitio estático no funciona bien abriendo `index.html` con doble clic: necesita un servidor. Para probarlo en tu ordenador, con Python instalado:

```bash
cd _build/html
python -m http.server 8000
```

y abre <http://localhost:8000>. Se detiene con **Ctrl** + **C**.

### Publicarlo en un servidor Apache

Hay dos casos, según dónde vaya a quedar el sitio:

En la raíz del dominio (`https://servidor.ejemplo/`)
: Construye con `myst build --html` y copia **el contenido** de `_build/html` en la carpeta raíz del sitio Apache (su `DocumentRoot`).

En una subcarpeta (`https://servidor.ejemplo/ruta/del/curso/`)
: Es lo habitual en un servidor institucional. Hay que decirle a MyST la ruta **al construir**, para que los enlaces internos la incluyan:

  ```bash
  BASE_URL=/ruta/del/curso myst build --html
  ```

  y copiar el contenido de `_build/html` en esa carpeta del servidor. En Windows (PowerShell) la variable se define en una línea aparte: `$env:BASE_URL="/ruta/del/curso"` y después `myst build --html`.

:::{warning} El `BASE_URL` tiene que coincidir con la ruta real
Si el sitio se ve sin estilos, o los enlaces del menú llevan a páginas que no existen, casi siempre es porque la ruta usada al construir no coincide con la carpeta donde está publicado. Vuelve a construir con la ruta correcta: empieza por `/` y no termina en `/`.
:::

La copia se puede hacer con el programa que uses habitualmente para subir ficheros a ese servidor (SFTP, una carpeta compartida…), o desde la terminal, por ejemplo con `scp -r _build/html/* usuario@servidor.ejemplo:/ruta/en/el/servidor/`.

## PDF

MyST no genera el PDF directamente: escribe el documento en el lenguaje de un sistema de composición y le pide a ese sistema que lo convierta en PDF. Puede usar dos:

::::{tab-set}
:::{tab-item} Typst (recomendado)
Un único programa, ligero y rápido. Se instala desde <https://github.com/typst/typst> (hay instaladores para Windows, macOS y Linux). Después:

```bash
myst build --typst
```

Genera `exports/proyecto-1-typst.pdf`.
:::
:::{tab-item} LaTeX
El sistema clásico de composición tipográfica. Necesita una distribución de LaTeX (TeX Live, MiKTeX o MacTeX), que ocupa varios gigabytes. Después:

```bash
myst build --pdf
```

Genera `exports/proyecto-1-latex.pdf`. Ojo: `--pdf` construye **todas** las exportaciones a PDF, también la de Typst. Si solo tienes LaTeX, la de Typst dará un error que puedes ignorar.
:::
::::

Las dos exportaciones están declaradas en el bloque `exports` de `myst.yml`:

```yaml
exports:
  - id: pdf-typst
    format: typst
    template: plain_typst_book
    output: exports/proyecto-1-typst.pdf
  - id: pdf-latex
    format: pdf
    template: plain_latex_book
    output: exports/proyecto-1-latex.pdf
```

`template` es la **plantilla**: decide el aspecto del PDF (portada, márgenes, tipos de letra). Las dos usadas aquí son las plantillas sencillas de libro. Sin la opción `articles`, el PDF incluye todas las páginas del índice, en su orden. La primera vez, MyST descarga la plantilla (y Typst, sus propios complementos), así que necesita conexión a internet.

### Qué cambia en el PDF

Un PDF es papel: no tiene botones ni nada que se despliegue. Al exportar, MyST adapta los elementos pensados para la web o, si no sabe convertirlos, los descarta. Con MyST 1.13 y las plantillas de este proyecto ocurre esto:

| En la web | PDF con Typst | PDF con LaTeX |
|---|---|---|
| Avisos plegados (`:class: dropdown`) | Se muestran abiertos | Se muestran abiertos |
| Desplegables (`dropdown`) | Se pierden | Se pierden |
| Pestañas | Una debajo de otra | Se pierden |
| Tarjeta suelta | Se conserva, sin el pie | Se pierde |
| Rejillas de tarjetas | Se pierden | Se pierden |
| Notas al margen | Se pierden | Se pierden |
| Teclas (`{kbd}`) | Se pierden | Se pierden |

«Se pierden» significa que el contenido desaparece del PDF: «pulsa Ctrl + C» escrito con `{kbd}` queda en «pulsa +».

La terminal avisa de cada elemento que no sabe convertir (`Unhandled LaTeX conversion…` o `Unhandled Typst conversion…`). Compruébalo exportando este proyecto y buscando en el PDF la página [](#bloques). Por eso, en el texto de las páginas de uso, las teclas se escriben en negrita y no con `{kbd}`.

Si un material se va a imprimir, conviene escribirlo pensando en el PDF desde el principio y revisar el resultado.

## Word

```bash
myst build --docx
```

No necesita ningún programa adicional. Un documento Word recoge **una sola página**, que se indica con `articles`:

```yaml
  - id: word
    format: docx
    articles: ejemplos/tablas.md
    output: exports/tablas.docx
```

Es útil para entregar una página concreta a quien prefiera editarla en un procesador de textos.

## Todo de una vez

```bash
myst build --all
```

construye todas las exportaciones declaradas.

:::{tip} Para explorar más
- Plantillas disponibles para PDF: `myst templates list --pdf` y `myst templates list --typst`.
- Guía de exportación: <https://mystmd.org/guide/documents-exports>.
- Para publicar en GitHub Pages en lugar de un servidor propio: `myst init --gh-pages`.
:::
