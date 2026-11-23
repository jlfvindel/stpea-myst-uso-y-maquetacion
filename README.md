# Usar MyST y maquetar

Este proyecto es un ejemplo guiado de producción de materiales docentes con [MyST](https://mystmd.org): qué es MyST, cómo se instala, se ejecuta y se exporta a web, PDF y Word, con ejemplos de tipografía, bloques y tablas.

Forma parte de una serie de cuatro proyectos independientes, pensados para recorrerse en este orden:

1. **Usar MyST y maquetar** (éste)
2. Recursos multimedia
3. Reutilizar y enlazar
4. Libros ejecutables

Aparte de tratar sobre el uso de Myst, cada proyecto es en sí mismo un paquete Myst  descargable y compilable directamente. Produce un conjunto de páginas html enlazadas o bien  opcionalmente un documento pdf o word con esos  contenidos.

## Para compilar este ejemplo localmente

1. Instala [Node.js](https://nodejs.org) (versión 22 o superior) y MyST: `npm install -g mystmd` (o `pip install mystmd`).
2. En una terminal, desde esta carpeta: `myst start`.
3. Abre <http://localhost:3000> (o el puerto que se te indique finalmente en la terminal).

Para producir el PDF hace falta además [Typst](https://typst.app) o una distribución de LaTeX.

## Diversas configuraciones en un mismo proyecto

Sobre el mismo directorio de ficheros, opcionalmente distribuidos en subdirectorios, se pueden producir distintas vistas finales. Cada una de ellas escoge qué ficheros se procesan y cómo se ubican en su particular tabla de contenidos.

Cada una de estas 'vistas' se define en un fichero de configuración yaml. Por defecto, si no se declara ninguno, se asume que existe myst.yml. Opcionalmente se pueden utilizar otros ficheros de configuración, con el nombre que se escoja, pero deben citarse explícitamente a la hora de construir esa vista específica. Este proyecto en concreto considera 2 selecciones y secuenciaciones distintas de los ficheros del directorio de trabajo.

| Fichero | Se usa con | Qué produce |
|---|---|---|
| `myst.yml` | `myst start` | El proyecto completo |
| `myst-alt1.yml` | `myst --config myst-alt1.yml start` | Edición breve para una sesión de clase |

## Entorno de edición local
La edición local de los ficheros markdown de contenido se puede realizar con cualquier editor de texto plano, como SublimeText.

Con la opción `myst start` dentro del directorio del proyecto se escogen los ficheros declarados en el toc: del fichero de configuración y se procesan. El sistema arranca directamente un servidor local en localhost en un determinado puerto, usualmente 3000. En esa dirección local del navegador se visualiza todo el sitio web ensamblado. Cuando se modifica la fuente de un fichero y se salva, automáticamente se refrescan los cambios en esta visualización local del sitio. 


## Un parche para añadir un fichero descargable
Este ejemplo prevé que en sus páginas html publicadas aparezca un enlace desde el que se puede descargar un zip con la fuente de todo el proyecto. 

El zip de todo el proyecto no se encuentra dentro del propio proyecto en github. Se produce localmente y se añade al sitio web que se remite al servidor de publicación.

Así, la preparación local del paquete publicable requiere (1) la descarga de un zip con las fuentes en github del proyecto, (2) la especificación de una BASE_URL de acuerdo a la del servidor donde se alojará y (3) el ensamblaje de las páginas del proyecto y su exportación como sitio web estático. Todo este proceso se esquematiza como:

```bash
./preparar-descarga.sh                     # zip de la fuente, para el botón de descarga
BASE_URL=/ruta/del/sitio myst build --html
```

Si no se ejecuta `preparar-descarga.sh`, MyST avisa de que falta el fichero de descarga; el resto del sitio funciona igual.

## Licencia y elaboración

José Luis Fernández Vindel. Contenido bajo licencia [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.es).

Este es un mero ejemplo motivador del uso de Myst, facilitado como un paquete que se puede procesar localmente de forma directa. Forma parte de un conjunto de ejemplos similares.

Se han realizado en colaboración con un asistente de inteligencia artificial (Claude, de Anthropic). El autor ha decidido la gradación entre los diversos ejemplos, el enfoque de cada uno, y ha revisado el resultado. Comprobado con MyST 1.13.0.
