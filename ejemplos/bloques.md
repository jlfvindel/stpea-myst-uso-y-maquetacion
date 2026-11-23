---
title: Bloques para organizar el contenido
short_title: Bloques
label: bloques
---

Los bloques se escriben con **directivas**: empiezan con tres dos puntos y el nombre de la directiva entre llaves, y terminan con otros tres dos puntos.

```markdown
:::{nombre} Título opcional
:opcion: valor
Contenido del bloque.
:::
```

## Avisos

Los avisos (*admonitions*) destacan una idea. Cada tipo tiene un color y un icono:

```markdown
:::{note}
Una nota: información complementaria.
:::

:::{tip}
Un consejo práctico.
:::

:::{warning}
Una advertencia: algo que puede salir mal.
:::

:::{important}
Algo que no conviene pasar por alto.
:::
```

Resultado:

:::{note}
Una nota: información complementaria.
:::

:::{tip}
Un consejo práctico.
:::

:::{warning}
Una advertencia: algo que puede salir mal.
:::

:::{important}
Algo que no conviene pasar por alto.
:::

También existen `attention`, `caution`, `danger`, `error`, `hint` y `seealso`.

El título por defecto es el nombre del tipo, en inglés. Para poner uno propio, se escribe a continuación del nombre:

```markdown
:::{tip} Antes de empezar
Ten a mano la guía de MyST.
:::
```

Resultado:

:::{tip} Antes de empezar
Ten a mano la guía de MyST.
:::

Con la opción `:class: dropdown`, el aviso aparece plegado:

```markdown
:::{note} Solución
:class: dropdown
El contenido queda oculto hasta que se pulsa el título.
:::
```

Resultado:

:::{note} Solución
:class: dropdown
El contenido queda oculto hasta que se pulsa el título.
:::

## Desplegables

Para ocultar algo sin darle aspecto de aviso, como una pista o un detalle técnico:

```markdown
:::{dropdown} Ver la respuesta
La respuesta queda oculta hasta que se pulsa el título.
:::
```

Resultado:

:::{dropdown} Ver la respuesta
La respuesta queda oculta hasta que se pulsa el título.
:::

## Pestañas

Útiles para mostrar alternativas, como las instrucciones de cada sistema operativo:

```markdown
::::{tab-set}
:::{tab-item} Windows
Abre **PowerShell** desde el menú Inicio.
:::
:::{tab-item} macOS
Abre la **Terminal** desde Aplicaciones, carpeta Utilidades.
:::
:::{tab-item} Linux
Abre la **Terminal** de tu escritorio.
:::
::::
```

Resultado:

::::{tab-set}
:::{tab-item} Windows
Abre **PowerShell** desde el menú Inicio.
:::
:::{tab-item} macOS
Abre la **Terminal** desde Aplicaciones, carpeta Utilidades.
:::
:::{tab-item} Linux
Abre la **Terminal** de tu escritorio.
:::
::::

Fíjate en que `tab-set` usa **cuatro** dos puntos y cada `tab-item`, tres. Así se anidan las directivas: la de fuera lleva más dos puntos que las de dentro.

## Tarjetas y rejillas

Una tarjeta enmarca un contenido breve, con título y pie opcionales:

```markdown
:::{card} Unidad 1
Introducción a la materia.
+++
Duración: 2 semanas
:::
```

Resultado:

:::{card} Unidad 1
Introducción a la materia.
+++
Duración: 2 semanas
:::

Una rejilla (`grid`) coloca varias tarjetas en columnas. Los cuatro números indican cuántas columnas usar en pantallas muy pequeñas, pequeñas, medianas y grandes:

```markdown
::::{grid} 1 1 3 3
:::{card} Objetivos
Qué se aprende.
:::
:::{card} Contenidos
Qué se trabaja.
:::
:::{card} Evaluación
Cómo se comprueba.
:::
::::
```

Resultado:

::::{grid} 1 1 3 3
:::{card} Objetivos
Qué se aprende.
:::
:::{card} Contenidos
Qué se trabaja.
:::
:::{card} Evaluación
Cómo se comprueba.
:::
::::

## Notas al margen

En pantallas anchas, una nota al margen se coloca a la derecha del texto, fuera de la columna principal:

```markdown
:::{aside}
Esta es una nota al margen.
:::
```

Resultado:

:::{aside}
Esta es una nota al margen.
:::

El texto principal sigue su curso sin interrupción, y la nota queda al lado, en el margen derecho. En pantallas estrechas, como la de un móvil, se coloca dentro del texto.

:::{tip} Para explorar más
- Avisos: <https://mystmd.org/guide/admonitions>.
- Desplegables, pestañas, tarjetas y rejillas: <https://mystmd.org/guide/dropdowns-cards-and-tabs>.
:::
