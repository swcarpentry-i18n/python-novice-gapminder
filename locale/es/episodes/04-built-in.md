---
title: Funciones integradas y ayuda
teaching: 15
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- Explicar el propósito de las funciones.
- Llamar correctamente a las funciones incorporadas de Python.
- Anidar correctamente las llamadas a funciones integradas.
- Utilice ayuda para mostrar documentación para funciones integradas.
- Describe correctamente las situaciones en las que se producen SyntaxError y NameError.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::::: preguntas

- ¿Cómo puedo utilizar las funciones incorporadas?
- ¿Cómo puedo averiguar qué hacen?
- ¿Qué tipo de errores pueden ocurrir en los programas?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Utilice los comentarios para añadir documentación a los programas.

```python
# Esta oración no es ejecutada por Python.
ajuste = 0.5 # Ninguna es - nada después de '#' es ignorado.
```

## Una función puede tomar cero o más argumentos.

- Ya hemos visto algunas funciones --- ahora veamos más de cerca.
- Un _argumento_ es un valor pasado a una función.
- `len` toma exactamente una.
- `int`, `str`, y `float` crean un nuevo valor a partir de uno existente.
- `print` toma cero o más.
- `print` sin argumentos imprime una línea en blanco.
  - Siempre debe usar paréntesis, incluso si están vacíos,
    para que Python sepa que una función está siendo llamada.

```python
print('before')
print()
print('after')
```

```output
antes de

después
```

## Cada función devuelve algo.

- Cada llamada de función produce algún resultado.
- Si la función no tiene un resultado útil para retornar,
  normalmente devuelve el valor especial `Ningo`. `Ninguno` es un objeto de Python
  que se levanta en cualquier momento no hay valor.

```python
result = print('ejemplo')
print('resultado de la impresión es', resultado)
```

```output
ejemplo
resultado de impresión no es ninguno
```

## Las funciones integradas usadas por Commonly incluyen `max`, `min`, y `round`.

- Usa `max` para encontrar el valor más grande de uno o más valores.
- Usa `min` para encontrar lo más pequeño.
- Ambos funcionan tanto en cadenas de caracteres como en números.
  - "Grande" y "menor" utilizan (0-9, A-Z, a-z) para comparar letras.

```python
print(max(1, 2, 3))
print(min('a', 'A', '0'))
```

```output
3
0
```

## Las funciones sólo pueden funcionar para ciertos (combinaciones de) argumentos.

- `max` y `min` deben recibir al menos un argumento.
  - "Lo más grande del conjunto vacío" es una pregunta sin sentido.
- Y hay que darles cosas que puedan compararse significativamente.

```python
print(max(1, 'a'))
```

```error
TypeError Traceback (la última llamada más reciente)
<ipython-input-52-3f049acf3762> en <module>
----> 1 print(max(1, 'a'))

TipoError: '>' no soportado entre instancias de 'str' y 'int'
```

## Las funciones pueden tener valores por defecto para algunos argumentos.

- `round` redondeará un número de punto flotante.
- Por defecto, redondea a cero decimales.

```python
redondo(3.712)
```

```output
4
```

- Podemos especificar el número de decimales que queremos.

```python
redondo(3.712, 1)
```

```output
3.7
```

## Las funciones adjuntas a los objetos se llaman métodos

- Las funciones toman otra forma que será común en los episodios de las pandas.
- Los métodos tienen paréntesis como funciones, pero vienen después de la variable.
- Algunos métodos se utilizan para operaciones internas de Python, y están marcados con doble subrayado.

```python
my_string = 'Hola mundo! # creación de un objeto de cadena 

print(len(my_string)) # la función len toma una cadena como argumento y devuelve la longitud de la cadena

print(my_string. wapcase()) # llamar al método de intercambio en el objeto my_string

print(my_string.__len__()) # llamar al método interno __len__ en el objeto my_string, usado por len(my_string)

```

```output
12
¡HELLO MUNDO!
12
```

- Puede que incluso los veas encadenados juntos.  Operan de izquierda a derecha.

```python
print(my_string.isupper()) # No todas las letras tienen mayúsculas
print(my_string.upper()) # Esto mayúscula todas las letras

print(my_string.upper().isupper()) # Ahora todas las letras están mayúsculas
```

```output
False
HELLO MUNDO
Verdadero
```

## Usa la función integrada `help` para obtener ayuda para una función.

- Cada función incorporada tiene documentación en línea.

```python
ayuda(ronda)
```

```output
Help on built-in function round in module builtins:

round(number, ndigits=None)
    Round a number to a given precision in decimal digits.
    
    The return value is an integer if ndigits is omitted or None.  Otherwise
    the return value has the same type as the number.  ndigits may be negative.
```

## El Notebook de Jupyter tiene dos maneras de obtener ayuda.

- Opción 1: Coloca el cursor cerca de donde se invoca la función en una celda
  (es decir, el nombre de la función o sus parámetros),
  - Hold down <kbd>Shift</kbd>, and press <kbd>Tab</kbd>.
  - Haga esto varias veces para ampliar la información devuelta.
- Opción 2: Escriba el nombre de la función en una celda con un signo de interrogación después de ella. Luego ejecute la celda.

## Python reporta un error de sintaxis cuando no puede entender el origen de un programa.

- Ni siquiera intentaría ejecutar el programa si no se puede analizar.

```python
# Olvidó cerrar las comillas alrededor de la cadena.
name = 'Feng
```

```error
  Archivo "<ipython-input-56-f42768451d55>", línea 2
    nombre = 'Feng
                ^
SyntaxError: EOL mientras escaneaba cadena literal
```

```python
# Un '=' extra en la asignación.
edad = = 52
```

```error
  Archivo "<ipython-input-57-ccc3df3cf902>", línea 2
    edad = 52
          ^
SyntaxError: sintaxis no válida
```

- Mira más de cerca el mensaje de error:

```python
impres("Hola mundo"
```

```error
  Archivo "<ipython-input-6-d1cc229bf815>", línea 1
    imprimir ("hola mundo"
                        ^
SyntaxError: EOF inesperado mientras se analiza
```

- El mensaje indica un problema en la primera línea de la entrada ("línea 1").
  - In this case the "ipython-input" section of the file name tells us that
    we are working with input into IPython,
    the Python interpreter used by the Jupyter Notebook.
- The `-6-` part of the filename indicates that
  the error occurred in cell 6 of our Notebook.
- A continuación está la línea problemática del código,
  indicando el problema con un puntero `^`.

## Python reporta un error en tiempo de ejecución cuando algo sale mal mientras un programa se está ejecutando. {#runtime-error}

```python
edad = 53
restante = 100 - aege # mal escrito 'edad'
```

```error
NameError Traceback (última llamada reciente)
<ipython-input-59-1214fb6c55fc> en <module>
      1 edad = 53
----> 2 restantes = 100 - aege # mal escrito 'age'

NameError: el nombre 'aege' no está definido
```

- Corregir errores de sintaxis leyendo los errores de código fuente y tiempo de ejecución rastreando la ejecución.

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Qué pasa cuando

1. Explica en términos simples el orden de las operaciones en el siguiente programa:
   cuando ocurre la adición, cuando ocurre la sustracción,
   cuando se llama a cada función, etc.
2. ¿Cuál es el valor final de la radianza?

```python
radiance = 1.0
radiance = max(2.1, 2.0 + min(radiance, 1.1 * radiancia - 0.5))
```

::::::::::::::::: solución

## Solución

1. Orden de las operaciones:

2. `1.1 * brillo = 1.1`

3. `1.1 - 0.5 = 0.6`

4. `min(radiance, 0.6) = 0.6`

5. `2.0 + 0.6 = 2.6`

6. `max(2.1, 2.6) = 2.6`

7. Al final, `resplandor = 2.6`

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Define la Diferencia

1. Predecir lo que imprimirá cada una de las sentencias `print` en el programa de abajo.
2. ¿Ejecuta `max(len(rich), pobre)` o produce un mensaje de error?
   Si se ejecuta, ¿tiene algún sentido su resultado?

```python
easy_string = "abc"
print(max(easy_string))
rico = "gold"
pobre = "tin"
print(max(rich, poor))
print(max(len(rich), len(poor)))
```

::::::::::::::::: solución

## Solución

```python
print(max(easy_string))
```

```output
c
```

```python
print(max(rico, pobre))
```

```output
lata
```

```python
print(max(len(rich), len(poor)))
```

```output
4
```

`max(len(rich), pobre)` lanza un TypeError. Esto se convierte en `max(4, 'tin')` y
como discutimos anteriormente una cadena y el entero no puede compararse significativamente.

```error
TypeError Traceback (la última llamada más reciente)
<ipython-input-65-bc82ad05177a> en <module>
----> 1 max(len(rich), pobre)

TipoError: '>' no soportado entre instancias de 'str' e 'int'
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## ¿Por qué no?

¿Por qué es que `max` y `min` no devuelven `Ninguno` cuando se les llama sin argumentos?

::::::::::::::::: solución

## Solución

`max` y `min` devuelven TypeErrors en este caso porque no se proporcionó el número correcto de parámetros
. If it just returned `None`, the error would be much harder to trace as it
would likely be stored into a variable and used later in the program, only to likely throw
a runtime error.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Último carácter de una cadena

Si Python empieza a contar desde cero,
y `len` devuelve el número de caracteres en una cadena,
¿qué expresión de índice obtendrá el último carácter en la cadena `name`?
(Nota: veremos una forma más sencilla de hacer esto en un episodio posterior.)

::::::::::::::::: solución

## Solución

`name[len(name) - 1]`

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## ¡Explora los documentos de Python!

La [documentación oficial de Python](https://docs.python.org/3/) es probablemente la fuente
más completa de información sobre el idioma. Está disponible en diferentes idiomas y contiene muchos recursos útiles
. La [página de funciones incorporadas](https://docs.python.org/3/library/functions.html) contiene un catálogo de
todas estas funciones, incluidas las que hemos cubierto en esta lección. Algunos de estos son más avanzados y
innecesarios en este momento, pero otros son muy simples y útiles.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Utilice los comentarios para añadir documentación a los programas.
- Una función puede tomar cero o más argumentos.
- Las funciones integradas usadas por Commonly incluyen `max`, `min`, y `round`.
- Las funciones sólo pueden funcionar para ciertos (combinaciones de) argumentos.
- Las funciones pueden tener valores por defecto para algunos argumentos.
- Usa la función integrada `help` para obtener ayuda para una función.
- El Notebook de Jupyter tiene dos maneras de obtener ayuda.
- Cada función devuelve algo.
- Python reporta un error de sintaxis cuando no puede entender el origen de un programa.
- Python reporta un error en tiempo de ejecución cuando algo sale mal mientras un programa se está ejecutando.
- Corregir errores de sintaxis leyendo el código fuente y errores de ejecución rastreando la ejecución del programa.

::::::::::::::::::::::::::::::::::::::::::::::::::
