# Usar MyST y maquetar

Ejemplo guiado de producción de materiales docentes con [MyST](https://mystmd.org): qué es MyST, cómo se instala, se ejecuta y se exporta a web, PDF y Word, con ejemplos de tipografía, bloques y tablas.

Forma parte de una serie de cuatro proyectos independientes, pensados para recorrerse en este orden:

1. **Usar MyST y maquetar** (éste)
2. Recursos multimedia
3. Reutilizar y enlazar
4. Libros ejecutables

Aparte de tratar sobre el uso de Myst, cada proyecto es un paquete descargable y compilable directamente usando Myst. Produce un conjunto de páginas html enlazadas y opcionalmente un documento pdf o word con ese contenidos.

## Para compilar este ejemplo localmente usando Myst

1. Instala [Node.js](https://nodejs.org) (versión 22 o superior) y MyST: `npm install -g mystmd` (o `pip install mystmd`).
2. En una terminal, desde esta carpeta: `myst start`.
3. Abre <http://localhost:3000> (o el puerto que se te indique finalmente en la terminal).

Para el PDF hace falta además [Typst](https://typst.app) o una distribución de LaTeX.

## Diversas configuraciones posibles

Sobre el mismo directorio de ficheros, opcionalmente distribuidos en subdirectorios, se pueden producir distintas vistas finales. Cada una de ellas escoge qué ficheros se procesan y cómo se ubican en su particular tabla de contenidos.

Cada una de estas 'vistas' se define en un fichero de configuración yaml. Por defecto, si no se declara ninguno, se debe denominar myst.yml. Opcionalmente se pueden utilizar otros ficheros de configuración, con el nombre que es escoja, pero deben citarse explícitamente a la hora de construir esa vista específica. Este proyecto considera 2 selecciones y secuenciaciones distintas, de entre los ficheros del directorio de trabajo.

| Fichero | Se usa con | Qué produce |
|---|---|---|
| `myst.yml` | `myst start` | El proyecto completo |
| `myst-alt1.yml` | `myst --config myst-alt1.yml start` | Edición breve para una sesión de clase |

## Un parche para añadir un fichero descargable
Este ejemplo prevé que en sus páginas html publicadas aparezca un enlace desde el que se puede descargar un zip con la fuente de todo el proyecto. Este zip se facilita directamente desde el servidor de publicación, sin remitir a github.

Como ese zip (con el estado actual del proyecto) no forma parte del repositorio de este ejemplo se facilita un script para generarlo.

```bash
./preparar-descarga.sh                     # zip de la fuente, para el botón de descarga
BASE_URL=/ruta/del/sitio myst build --html
```

y se copia el contenido de `_build/html` al servidor. Si no se ejecuta `preparar-descarga.sh`, MyST avisa de que falta el fichero de descarga; el resto del sitio funciona igual.

## Licencia y elaboración

José Luis Fernández Vindel. Contenido bajo licencia [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.es).

Preparado en colaboración con un asistente de inteligencia artificial (Claude, de Anthropic); el autor ha decidido el enfoque, ha revisado el resultado y responde de su contenido. Comprobado con MyST 1.13.0.
