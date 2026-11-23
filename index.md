---
title: 'Proyecto 1: usar MyST y maquetar'
short_title: Inicio
---

Este es el primero de cuatro proyectos de ejemplo para producir materiales docentes con MyST. Está construido con MyST, así que es a la vez la explicación y el ejemplo: lo que ves en el navegador sale de los ficheros `.md` de esta carpeta, y puedes abrir cualquiera para ver cómo está escrito.

:::{note} Sobre la elaboración de este material
:class: dropdown
Este proyecto lo ha preparado José Luis Fernández Vindel en colaboración con un asistente de inteligencia artificial (Claude, de Anthropic). La estructura, los textos y los ejemplos se han elaborado en diálogo con el asistente; el autor ha decidido el enfoque, ha revisado el resultado y responde de su contenido. Los ejemplos se han comprobado con MyST 1.13.0.
:::

Puedes {download}`descargar la fuente completa del proyecto <descargas/uso-y-maquetacion.zip>` para ejecutarlo y modificarlo en tu ordenador. También está en el botón de descarga, arriba a la derecha de cada página.

## Qué contiene

Usar MyST
: Qué es MyST, cómo se instala, cómo se ha ejecutado este proyecto y cómo se exporta a una web, a PDF o a Word.

Ejemplos de maquetación
: Tres páginas con los recursos básicos para dar forma a un texto: [texto](#texto), [bloques](#bloques) y [tablas](#tablas). Cada ejemplo muestra el código y el resultado.

## Dos configuraciones

La carpeta tiene dos ficheros de configuración. Cada uno produce un sitio distinto a partir de las mismas páginas:

| Fichero | Se usa con | Qué produce |
|---|---|---|
| `myst.yml` | `myst start` | El proyecto completo, con el menú en grupos |
| `myst-alt1.yml` | `myst --config myst-alt1.yml start` | Una edición breve para una sesión de clase: ejemplos primero, sin la página de exportación y con el menú plano |

Fíjate en el título que encabeza el menú lateral: indica qué configuración está activa. La página [](#ejecutar) explica los dos ficheros con detalle.

## Cómo verlo

En una terminal, desde la carpeta del proyecto (la que contiene `myst.yml`):

```bash
myst start
```

Luego abre <http://localhost:3000> en el navegador. Si aún no tienes MyST instalado, empieza por [](#que-es-myst).

:::{note} Los cuatro proyectos
1. **Usar MyST y maquetar** (este).
2. Insertar recursos: imágenes, vídeos, diagramas, ecuaciones.
3. Reestructurar, reutilizar y enlazar.
4. Documentos ejecutables con cuadernos Jupyter.
:::
