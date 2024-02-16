---
title: Bibliotecas
teaching: 10
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- Explique qué son las bibliotecas de software y por qué los programadores las crean y las utilizan.
- Escribe programas que importan y usan módulos de la biblioteca estándar de Python.
- Encuentre y lea documentación para la biblioteca estándar de forma interactiva (en el intérprete) y en línea.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::::: preguntas

- ¿Cómo puedo usar software que otras personas han escrito?
- ¿Cómo puedo averiguar qué hace ese software?

::::::::::::::::::::::::::::::::::::::::::::::::::

## La mayor parte del poder de un lenguaje de programación está en sus bibliotecas.

- A _library_ is a collection of files (called _modules_) that contains
  functions for use by other programs.
  - También puede contener valores de datos (por ejemplo, constantes numéricas) y otras cosas.
  - Se supone que el contenido de la biblioteca está relacionado, pero no hay forma de hacer cumplir eso.
- La [biblioteca estándar][stdlib] de Python es un conjunto extenso de módulos que viene
  con Python mismo.
- Hay muchas bibliotecas adicionales disponibles en [PyPI][pypi] (el Índice del Paquete Python).
- Más adelante veremos cómo escribir nuevas bibliotecas.

:::::::::::::::::::::::::::::::::::::::::  callout

## Bibliotecas y módulos

Una biblioteca es una colección de módulos, pero los términos a menudo se utilizan
intercambiablemente, especialmente porque muchas bibliotecas sólo consisten en un único módulo
, así que no te preocupes si las mezclas.

::::::::::::::::::::::::::::::::::::::::::::::::::

## Un programa debe importar un módulo de biblioteca antes de usarlo.

- Usa `import` para cargar un módulo de biblioteca en la memoria de un programa.
- Luego refiérase a cosas del módulo como `module_name.thing_name`.
  - Python usa `.` para significar "parte de".
- Usando `math`, uno de los módulos de la biblioteca estándar:

```python
import matemáticas

print('pi es', math.pi)
print('cos(pi) is', math.cos(math.pi))
```

```output
pi es 3.141592653589793
cos(pi) es -1.0
```

- Tiene que referirse a cada elemento con el nombre del módulo.
  - `math.cos(pi)` no funcionará: la referencia a `pi`
    de alguna manera "hereda" la referencia de la función a `math`.

## Usa `help` para aprender sobre el contenido de un módulo de biblioteca.

- Funciona como ayuda para una función.

```python
ayuda(matemáticas)
```

```output
Ayuda sobre las matemáticas del módulo:

NOMBRE
    math

REFERENCIA MODULE
    http://docs.python. rg/3/library/math

    La siguiente documentación se genera automáticamente a partir de los archivos fuente Python
    . Puede ser incompleto, incorrecto o incluir características que
    se consideran detalles de la implementación y pueden variar entre implementaciones de Python
    . En caso de duda, consulte la referencia del módulo en la ubicación
    indicada anteriormente.

DESCRIPTION
    Este módulo está siempre disponible. Proporciona acceso a las funciones matemáticas
    definidas por el estándar C.

FUNCIONES
    acos(x, /)
        Devuelve el coseno arco (medido en radianes) de x.

```

## Importar elementos específicos de un módulo de biblioteca para acortar programas.

- Usar `de... importar ...` para cargar sólo elementos específicos de un módulo de biblioteca.
- A continuación, refiérase a ellos directamente sin nombre de biblioteca como prefijo.

```python
from matemáticas import cos, pi

print('cos(pi) es', cos(pi))
```

```output
cos(pi) es -1.0
```

## Crear un alias para un módulo de biblioteca al importarlo para acortar programas.

- Usar `importar ... como ...` para dar a una biblioteca un _alias_ corto mientras se importa.
- Luego refiérase a los elementos de la biblioteca usando ese nombre acortado.

```python
importar matemáticas como m

print('cos(pi) es', m.cos(m.pi))
```

```output
cos(pi) es -1.0
```

- Comúnmente usado para bibliotecas que se utilizan frecuentemente o tienen nombres largos.
  - Por ejemplo, la librería `matplotlib` de plotación a menudo es alias como `mpl`.
- Pero puede hacer que los programas sean más difíciles de entender,
  ya que los lectores deben aprender los alias de tu programa.

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Explorando el módulo matemático

1. ¿Qué función del módulo `math` puedes usar para calcular una raíz cuadrada
   _sin_ usar `sqrt`?
2. Dado que la biblioteca contiene esta función, ¿por qué existe `sqrt`?

::::::::::::::::: solución

## Solución

1. Utilizando `help(math)` vemos que tenemos `power(x,y)` además de `sqrt(x)`,
   así que podríamos usar `power (x, 0.5)` para encontrar una raíz cuadrada.

2. La función `sqrt(x)` es razonablemente más legible que `power (x, 0.5)` cuando
   implementa ecuaciones. La capacidad de lectura es una piedra angular de la buena programación, por lo que
   tiene sentido proporcionar una función especial para este caso común específico.

Además, el diseño de la biblioteca `math` de Python tiene su origen en el estándar C,
que incluye tanto `sqrt(x)` como `power (x, )`, así que un poco de la historia
de programación se muestra en los nombres de las funciones de Python.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Ubicando el módulo derecho

Quieres seleccionar un carácter aleatorio de una cadena:

```python
bases = 'ACTTGCTTGAC'
```

1. ¿Cuál [biblioteca estándar][stdlib] módulo puede ayudarte?
2. ¿Qué función seleccionaría de ese módulo? ¿Hay alternativas?
3. Trate de escribir un programa que utilice la función.

::::::::::::::::: solución

## Solución

El [módulo aleatorio][randommod] parece que podría ayudar.

La cadena tiene 11 caracteres, cada uno con un índice posicional de 0 a 10.
Podrías usar [`random.randrange`](https://docs.python.org/3/library/random.html#random.randrange)
o [`random.randint`](https\://docs.python. rg/3/library/random.html#random.randint) funciones
para obtener un entero aleatorio entre 0 y 10, y luego seleccionar el carácter `bases` en ese índice:

```python
from random import randrange

random_index = randrange(len(bases))
print(bases[random_index])
```

o más contundentemente:

```python
from random import randrange

print(bases[randrange(len(bases))])
```

¿Tal vez hayas encontrado la función [`random.sample`](https://docs.python.org/3/library/random.html#random.sample)?
Permite un poco menos de escritura pero puede ser un poco más difícil de entender sólo leyendo:

```python
from random import sample

print(sample(bases, 1)[0])
```

Tenga en cuenta que esta función devuelve una lista de valores. We will learn about
lists in [episode 11](11-lists.md).

La solución más simple y más corta es la función [`random.choice`](https://docs.python.org/3/library/random.html#random.choice)
que hace exactamente lo que queremos:

```python
de la opción de importación aleatoria

print(choice(bases))
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Ejemplo de programación Jigsaw Puzzle (Problema de Parson)

Reorganice las siguientes sentencias para que se imprima una base de ADN
aleatoria y su índice en la cadena.
No todas las sentencias pueden ser necesarias.  Feel free to use/add
intermediate variables.

```python
bases="ACTTGCTGAC"
importar matemáticas
importar al azar
___ = random.randrange(n_bases)
___ = len(bases)
print("base aleatoria ", bases[___], "índice de base", ___)
```

::::::::::::::::: solución

## Solución

```python
import matemáticas 
import random
bases = "ACTTGCTTGAC" 
n_bases = len(bases)
idx = random. andrange(n_bases)
print("base aleatoria", bases[idx], "índice base", idx)
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## ¿Cuándo está disponible la ayuda?

Cuando un colega suyo escribe `help(math)`,
Python reporta un error:

```error
NameError: el nombre 'math' no está definido
```

¿Qué ha olvidado su colega?

::::::::::::::::: solución

## Solución

Importando el módulo matemático (`importar matemática`)

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Importación con Alias

1. Rellena los espacios en blanco para que el programa de abajo imprima `90.0`.
2. Reescribe el programa para que use `import` _sin_ `as`.
3. ¿Qué forma le resulta más fácil de leer?

```python
importar matemáticas como m
ángulo = ____.degrees(____.pi / 2)
print(____)
```

::::::::::::::::: solución

## Solución

```python
importar matemáticas como m
ángulo = m.degrees(m.pi / 2)
print(ángulo)
```

puede ser escrito como

```python
import matemáticas
ángulo = math.degrees(math.pi / 2)
print(ángulo)
```

Since you just wrote the code and are familiar with it, you might actually
find the first version easier to read. Pero al intentar leer una enorme pieza
de código escrita por otra persona, o cuando vuelvas a tu propia pieza enorme
de código después de varios meses, los nombres no abreviados son a menudo más fáciles, excepto
donde hay convenciones de abreviación claras.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## ¡Hay muchas maneras de importar bibliotecas!

Coincide las siguientes sentencias de impresión con las llamadas bibliotecarias apropiadas.

Comandos de impresión:

1. `print("sin(pi/2) =", sin(pi/2))`
2. `print("sin(pi/2) =", m.sin(m.pi/2))`
3. `print("sin(pi/2) =", math.sin(math.pi/2))`

Llamadas de biblioteca:

1. `de importación de matemáticas sin, pi`
2. `importar matemática`
3. `importar matemáticas como m`
4. `de importación matemática *`

::::::::::::::::: solución

## Solución

1. Llama a la biblioteca 1 y 4. Para referirse directamente a `sin` y `pi` sin
   el nombre de la librería como prefijo, necesita utilizar el `de... importar ...` Composición
   . Donías llamada de biblioteca 1 específicamente importa las dos funciones
   `sin` y `pi`, la llamada de biblioteca 4 importa todas las funciones en el módulo `math`.
2. Llamada a la biblioteca 3. Aquí `sin` y `pi` son referidos con una librería acortada
   nombre `m` en lugar de `math`. La llamada a la biblioteca 3 hace exactamente eso usando la
   `importación ... como sintaxis ...` - crea un alias para `math` en forma de
   el nombre abreviado `m`.
3. Llamada a la biblioteca 2. Aquí `sin` y `pi` son referidos con la librería regular
   nombre `math`, así que la llamada regular `import ...` sufre la llamada.

**Nota:** aunque funciona la llamada a la biblioteca 4 importar todos los nombres de un módulo utilizando un comodín
importar es [no recomendado][pep8-imports] ya que deja poco claro qué nombres del módulo
se utilizan en el código. En general, es mejor hacer que tus importaciones sean lo más específicas posible y para
importar solo lo que tu código utiliza. En la llamada de biblioteca 1, la declaración `import` nos dice explícitamente
que la función `sin` es importada del módulo `math`, pero la llamada a la biblioteca 4 no es
transmitir esta información.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Importación de artículos específicos

1. Rellena los espacios en blanco para que el programa de abajo imprima `90.0`.
2. ¿Encuentras esta versión más fácil de leer que las anteriores?
3. ¿Por qué _no_ los programadores siempre usarían esta forma de `import`?

```python
____ importación matemáticas ____, ____ ángulo
= grados(pi / 2) Impresión
(ángulo)
```

::::::::::::::::: solución

## Solución

```python
desde grados de importación matemáticas, pi
ángulo = grados(pi / 2)
impresión (ángulo)
```

Lo más probable es que encuentre esta versión más fácil de leer ya que es menos dense.
La razón principal para no usar esta forma de importación es evitar choques de nombres.
Por ejemplo, no importarías `grados` de esta manera si también querías
usar el nombre `grados` para una variable o función propia. O si usted
también importaba una función llamada `degrees` desde otra biblioteca.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Leyendo mensajes de error

1. Lee el código de abajo e intenta identificar cuáles son los errores sin ejecutarlo.
2. Ejecute el código y lea el mensaje de error. ¿Qué tipo de error es?

```python
de registro de importación matemáticas
log(0)
```

::::::::::::::::: solución

## Solución

```output
-------------------------------------------------------------------
Traceback de errores de valor (la última llamada)
<ipython-input-1-d72e1d780bab> en <module>
      1 de registro de importación de matemáticas
----> 2 log(0)

Valor: error de dominio matemático
```

1. El logaritmo de `x` solo está definido para `x > 0`, así que 0 está fuera del dominio
   de la función.

2. Obtienes un error de tipo `ValueError`, indicando que la función
   recibió un valor de argumento inapropiado. El mensaje adicional
   "error de dominio matemático" deja más claro cuál es el problema.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

[stdlib]: https://docs.python.org/3/library/

[pypi]: https://pypi.python.org/pypi/

[randommod]: https://docs.python.org/3/library/random.html

[pep8-imports]: https://pep8.org/#importa

:::::::::::::::::::::::::::::::::::::::: keypoints

- La mayor parte del poder de un lenguaje de programación está en sus bibliotecas.
- Un programa debe importar un módulo de biblioteca para poder usarlo.
- Usa `help` para aprender sobre el contenido de un módulo de biblioteca.
- Importar elementos específicos de una biblioteca para acortar programas.
- Crear un alias para una biblioteca al importarla para acortar programas.

::::::::::::::::::::::::::::::::::::::::::::::::::
