---
title: Cómo se ejecuta este proyecto
short_title: Ejecutar
label: ejecutar
---

Esta página cuenta cómo se ha producido el sitio que estás viendo, con cada una de sus dos configuraciones.

## Arrancar el sitio en local

Desde la carpeta del proyecto:

```bash
myst start
```

La primera vez, MyST descarga el tema del sitio, así que necesita conexión a internet y tarda un poco más. Cuando termina, la terminal muestra, entre algunos emojis, estas líneas:

```text
Starting Book Theme
Server started on port 3000!
http://localhost:3000
```

Abre esa dirección en el navegador. Mientras `myst start` siga en marcha, cada vez que guardes un fichero `.md` la página se actualiza sola. La terminal queda ocupada: ahí aparecen los avisos si algo no está bien escrito.

:::{note} Qué significa `localhost`
`localhost` es tu propio ordenador. El sitio solo lo ves tú, mientras la orden esté en marcha. Para publicarlo hay que exportarlo (lo explica la página «Exportar» de la configuración principal).
:::

## La configuración principal: `myst.yml`

`myst start` lee por defecto el fichero `myst.yml`. Este es el de este proyecto:

:::{literalinclude} ../myst.yml
:language: yaml
:::

Lo importante es el índice (`toc`). Fíjate en las dos formas de agrupar páginas y búscalas en el menú lateral:

- **«Usar MyST»** es un `title` con `children`: un grupo que se despliega, pero que no tiene página propia.
- **«Texto»** es un `file` con `children`: también se despliega, pero además es una página que se puede visitar.

El bloque `exports` se usa solo al exportar a PDF o a Word, y no afecta al sitio.

## La configuración alternativa: `myst-alt1.yml`

:::{literalinclude} ../myst-alt1.yml
:language: yaml
:::

Usa las mismas páginas con otro propósito: una edición breve para trabajar en una sesión de clase. Selecciona otros ficheros (deja fuera la exportación), los reordena (los ejemplos van primero) y aplana el menú.

## Cambiar de una configuración a otra

1. En la terminal donde corre `myst start`, pulsa **Ctrl** + **C** para detenerlo. En macOS también es **Ctrl** + **C**, no **Cmd**.
2. Arranca con la configuración alternativa:

   ```bash
   myst --config myst-alt1.yml start
   ```

3. Recarga el navegador. El título ha cambiado a «Proyecto 1 · Edición breve» y el menú es otro.

Para volver, detén de nuevo con **Ctrl** + **C** y ejecuta `myst start` sin opciones.

`--config` es una opción del programa `myst`, no de la orden `start`. Por eso va antes de `start`, y sirve igual para las demás órdenes, por ejemplo `myst --config myst-alt1.yml build --html`.

## Si algo no va bien

El puerto 3000 está ocupado
: Hay otro `myst start` abierto en otra terminal, o algún otro programa usa ese puerto. Ciérralo o usa otro puerto: `myst start --port 3001`.

La página muestra contenido antiguo
: Detén el servidor, borra lo generado con `myst clean` y vuelve a arrancar.

`myst: command not found` (o «no se reconoce como un comando»)
: MyST no está instalado, o la terminal se abrió antes de instalarlo. Cierra la terminal, abre otra y prueba `myst --version`.

:::{tip} Para explorar más
- `myst start --help` muestra todas las opciones de arranque.
- Prueba a crear un tercer fichero, `myst-alt2.yml`, con otra selección de páginas, y arráncalo con `--config`.
:::
