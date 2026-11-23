---
title: Tablas
short_title: Tablas
label: tablas
---

MyST ofrece tres formas de escribir una tabla, de la más rápida a la más flexible. Como en las páginas anteriores, cada ejemplo muestra primero el código y debajo el resultado. Esta es además la página que la configuración principal exporta a Word.

## Tabla Markdown

Es la forma más rápida. Las columnas se separan con `|` y la segunda línea separa la cabecera del cuerpo:

```markdown
| Unidad | Horas | Evaluación |
|---|---|---|
| Introducción | 6 | Cuestionario |
| Desarrollo | 20 | Proyecto |
| Cierre | 4 | Presentación |
```

Resultado:

| Unidad | Horas | Evaluación |
|---|---|---|
| Introducción | 6 | Cuestionario |
| Desarrollo | 20 | Proyecto |
| Cierre | 4 | Presentación |

No hace falta alinear las barras en el fichero: basta con que cada fila tenga el mismo número de celdas.

### Alineación de columnas

Los dos puntos de la segunda línea indican la alineación: a la izquierda (`:--`), centrada (`:-:`) o a la derecha (`--:`).

```markdown
| Concepto | Peso | Nota |
|:--|:-:|--:|
| Prácticas | 40 % | 7,5 |
| Examen | 60 % | 6,0 |
```

Resultado:

| Concepto | Peso | Nota |
|:--|:-:|--:|
| Prácticas | 40 % | 7,5 |
| Examen | 60 % | 6,0 |

Las celdas admiten formato en línea: **negrita**, *cursiva*, `código`, enlaces…

## Tabla con título

La directiva `table` envuelve una tabla Markdown y le añade un título, que se numera automáticamente:

```markdown
:::{table} Reparto de horas por unidad
:label: tabla-horas
:align: center

| Unidad | Teoría | Práctica |
|---|--:|--:|
| 1 | 4 | 2 |
| 2 | 8 | 12 |
:::
```

Resultado:

:::{table} Reparto de horas por unidad
:label: tabla-horas
:align: center

| Unidad | Teoría | Práctica |
|---|--:|--:|
| 1 | 4 | 2 |
| 2 | 8 | 12 |
:::

La etiqueta (`:label:`) permite citarla desde el texto: [](#tabla-horas) muestra el reparto. Las referencias se tratan en el proyecto 3.

## Tabla como lista

Cuando las celdas tienen mucho texto, o varios párrafos, la tabla Markdown se vuelve ilegible en el fichero. La directiva `list-table` la escribe como una lista de filas, y cada fila como una lista de celdas:

```markdown
:::{list-table} Criterios de una actividad
:header-rows: 1

*   - Criterio
    - Descripción
*   - Claridad
    - El texto se entiende a la primera lectura.

      Usa ejemplos cuando el concepto es abstracto.
*   - Estructura
    - Las ideas siguen un orden y cada sección tiene un propósito.
:::
```

Resultado:

:::{list-table} Criterios de una actividad
:header-rows: 1

*   - Criterio
    - Descripción
*   - Claridad
    - El texto se entiende a la primera lectura.

      Usa ejemplos cuando el concepto es abstracto.
*   - Estructura
    - Las ideas siguen un orden y cada sección tiene un propósito.
:::

`:header-rows: 1` convierte la primera fila en cabecera.

:::{tip} Para explorar más
- Todas las opciones de tablas: <https://mystmd.org/guide/tables>.
- Prueba a exportar esta página a Word con `myst build --docx` y ábrela en tu procesador de textos.
:::
