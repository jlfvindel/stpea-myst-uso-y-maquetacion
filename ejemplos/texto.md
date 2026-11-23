---
title: Dar forma al texto
short_title: Texto
label: texto
---

Esta página reúne los recursos básicos para dar forma a un texto. En el menú es también la cabecera de un grupo, del que cuelgan [](#bloques) y [](#tablas).

Cada ejemplo muestra primero el código, tal como se escribe en el fichero `.md`, y debajo el resultado. Así se ve igual en la web, en el PDF y en Word.

## Párrafos y énfasis

Un párrafo es un bloque de texto separado por una línea en blanco. Un salto de línea simple dentro del fichero no crea un párrafo nuevo.

```markdown
Texto con **negrita**, *cursiva* y `código en línea`.
Esta línea sigue en el mismo párrafo.

Este es otro párrafo.
```

Resultado:

Texto con **negrita**, *cursiva* y `código en línea`.
Esta línea sigue en el mismo párrafo.

Este es otro párrafo.

## Encabezados

Los títulos de sección se marcan con `#`. El título de la página ya lo pone el `title` del frontmatter, así que dentro de la página se empieza con `##`:

```markdown
## Sección
### Subsección
#### Apartado menor
```

Los encabezados `##` y `###` aparecen en el índice de la derecha («Contents»).

## Listas

```markdown
- Una lista sin numerar
- con un elemento
  - y otro anidado (con dos espacios delante)

1. Una lista numerada
2. sigue la numeración
3. aunque escribas `1.` en todas las líneas
```

Resultado:

- Una lista sin numerar
- con un elemento
  - y otro anidado (con dos espacios delante)

1. Una lista numerada
2. sigue la numeración
3. aunque escribas `1.` en todas las líneas

Las **listas de definiciones** son útiles para glosarios breves o para describir opciones:

```markdown
Directiva
: Un bloque con nombre que añade estructura, como un aviso o una tabla.

Rol
: Una marca dentro de una línea, como una tecla o un subíndice.
```

Resultado:

Directiva
: Un bloque con nombre que añade estructura, como un aviso o una tabla.

Rol
: Una marca dentro de una línea, como una tecla o un subíndice.

## Citas

```markdown
> Una cita se marca con `>` al principio de cada línea.
> Puede ocupar varias líneas.
```

Resultado:

> Una cita se marca con `>` al principio de cada línea.
> Puede ocupar varias líneas.

Para una cita destacada, con su autoría:

```markdown
:::{epigraph}
Lo que oigo, lo olvido; lo que veo, lo recuerdo; lo que hago, lo entiendo.

-- Proverbio atribuido a Confucio
:::
```

Resultado:

:::{epigraph}
Lo que oigo, lo olvido; lo que veo, lo recuerdo; lo que hago, lo entiendo.

-- Proverbio atribuido a Confucio
:::

## Código

Un bloque de código va entre tres comillas invertidas, con el nombre del lenguaje para colorearlo:

````markdown
```python
def saludo(nombre):
    return f"Hola, {nombre}"
```
````

Resultado:

```python
def saludo(nombre):
    return f"Hola, {nombre}"
```

Con la directiva `code-block` se le pueden añadir opciones: un título, números de línea y líneas destacadas.

````markdown
```{code-block} python
:caption: Un programa breve
:linenos:
:emphasize-lines: 2

def saludo(nombre):
    return f"Hola, {nombre}"

print(saludo("mundo"))
```
````

Resultado:

```{code-block} python
:caption: Un programa breve
:linenos:
:emphasize-lines: 2

def saludo(nombre):
    return f"Hola, {nombre}"

print(saludo("mundo"))
```

## Marcas dentro de la línea

Algunos recursos se escriben con un **rol**, con la forma `` {nombre}`contenido` ``:

```markdown
- Subíndice y superíndice: H{sub}`2`O, 10{sup}`3`
- Teclas: pulsa {kbd}`Ctrl` + {kbd}`C`
- Abreviaturas con su significado al pasar el ratón: {abbr}`FP (Formación Profesional)`
```

Resultado:

- Subíndice y superíndice: H{sub}`2`O, 10{sup}`3`
- Teclas: pulsa {kbd}`Ctrl` + {kbd}`C`
- Abreviaturas con su significado al pasar el ratón: {abbr}`FP (Formación Profesional)`

## Notas al pie

```markdown
MyST nació en el ecosistema de Jupyter[^origen].

[^origen]: El proyecto Executable Books, que también mantiene Jupyter Book.
```

Resultado:

MyST nació en el ecosistema de Jupyter[^origen].

[^origen]: El proyecto Executable Books, que también mantiene Jupyter Book.

La nota se puede definir en cualquier lugar de la página. MyST las numera y las reúne al final.

:::{tip} Para explorar más
- Todos los recursos de texto: <https://mystmd.org/guide/typography>.
- La lista completa de roles: <https://mystmd.org/guide/roles>.
:::
