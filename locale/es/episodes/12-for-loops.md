---
title: Bucles Para
teaching: 10
exercises: 15
---

::::::::::::::::::::::::::::::::::::::: objectives

- Explicar para qué bucles se utilizan normalmente.
- Traza la ejecución de un bucle simple (sin anidado) y indica correctamente los valores de las variables en cada iteración.
- Escribe para bucles que utilicen el patrón de Acumulador para añadir valores.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::::: preguntas

- ¿Cómo puedo hacer que un programa haga muchas cosas?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Un bucle _for loop_ ejecuta comandos una vez por cada valor en una colección.

- Hacer cálculos en los valores en una lista una por una
  es tan doloroso como trabajar con `pressure_001`, `pressure_002`, etc.
- Un \*bucle for \* le dice a Python que ejecute algunas sentencias una vez por cada valor en una lista,
  una cadena de caracteres,
  u otra colección.
- "para cada cosa en este grupo, hacer estas operaciones"

```python
for number in [2, 3, 5]:
    print(number)
```

- Este bucle `for` es equivalente a:

```python
print(2)
print(3)
print(5)
```

- Y la salida del bucle `for` es:

```output
2
3
5
```

## Un bucle `para` se compone de una colección, una variable de bucle y un cuerpo.

```python
for number in [2, 3, 5]:
    print(number)
```

- La colección, `[2, 3, 5]`, es en lo que se está ejecutando el bucle.
- El cuerpo, `print(number)`, especifica qué hacer por cada valor en la colección.
- La variable de bucle, `number`, es lo que cambia para cada _iteración_ del bucle.
  - La "cosa actual".

## La primera línea del ciclo `for` debe terminar con dos puntos y el cuerpo debe ser sangrado.

- El coma al final de la primera línea indica el inicio de un _block_ de declaraciones.
- Python usa sangría en lugar de `{}` o `begin`/`end` para mostrar _anidación_.
  - Cualquier sangría consistente es legal, pero casi todo el mundo utiliza cuatro espacios.

```python
for number in [2, 3, 5]:
print(number)
```

```error
Error de sangre: se esperaba un bloque sangrado
```

- La sangría siempre tiene sentido en Python.

```python
firstName = "Jon"
  apellido = "Smith"
```

```error
  Archivo "<ipython-input-7-f65f2962bf9c>", línea 2
    apellido = "Smith"
    ^
IndentationError: sangría inesperada
```

- Este error se puede arreglar removiendo los espacios adicionales
  al comienzo de la segunda línea.

## Las variables Loop pueden llamarse cualquier cosa.

- Como con todas las variables, las variables de bucle son:
  - Creado bajo demanda.
  - Desgraciadamente, sus nombres pueden ser cualquier cosa.

```python
for kitten in [2, 3, 5]:
    print(kitten)
```

## El cuerpo de un bucle puede contener muchas declaraciones.

- Pero ningún bucle debe ser más que unas pocas líneas de largo.
- Difícil para los seres humanos tener en mente pedazos de código más grandes.

```python
primes = [2, 3, 5]
para p en primos:
    cuadrado = p ** 2
    cubo = p ** 3
    impresión(p, cuadrado, cuba)
```

```output
2 4 8
3 9 27
5 25 125
```

## Usa `range` para iterar sobre una secuencia de números.

- La función integrada [`range`](https://docs.python.org/3/library/stdtypes.html#range) produce una secuencia de números.
  - _No_ una lista: los números se producen bajo demanda
    para hacer que el bucle en grandes rangos sea más eficiente.
- `range(N)` es los números 0..N-1
  - Exactamente los índices legales de una lista o cadena de caracteres de longitud N

```python
print('un rango no es una lista: rango(0, 3)')
para el número en rango(0, 3): impresión
    (número)
```

```output
un rango no es una lista: rango(0, 3)
0
1
2
```

## El patrón de Acumulador convierte muchos valores en uno.

- Un patrón común en los programas es:
  1. Inicializa una variable _acumulador_ a cero, la cadena vacía o la lista vacía.
  2. Actualizar la variable con valores de una colección.

```python
# Suma los primeros 10 enteros.
total = 0
para el número en rango(10):
   total = total + (número + 1)
print(total)
```

```output
55
```

- Leer `total = total + (número + 1)` como:
  - Agrega 1 al valor actual de la variable de bucle `number`.
  - Añade eso al valor actual de la variable acumuladora `total`.
  - Asigna eso a `total`, reemplazando el valor actual.
- Tenemos que añadir `number + 1` porque `range` produce 0..9, no 1..10.

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Clasificando errores

¿Es un error de sangría un error de sintaxis o un error de ejecución?

::::::::::::::::: solución

## Solución

Un IndentationError es un error de sintaxis. Los programas con errores de sintaxis no se pueden iniciar.
Un programa con un error de ejecución se iniciará pero se producirá un error bajo ciertas condiciones.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Ejecutar seguimiento

Crear una tabla que muestre los números de las líneas que se ejecutan cuando se ejecuta este programa,
y los valores de las variables después de cada línea es ejecutada.

```python
total = 0
para caracteres en "tin":
    total = total + 1
```

::::::::::::::::: solución

## Solución

| Nº de línea | Variables                  |
| ----------- | -------------------------- |
| 1           | total = 0                  |
| 2           | total = 0 caracteres = 't' |
| 3           | total = 1 carácter = 't'   |
| 2           | total = 1 carácter = 'i'   |
| 3           | total = 2 caracteres = 'i' |
| 2           | total = 2 caracteres = 'n' |
| 3           | total = 3 caracteres = 'n' |

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Reversing a String

Rellena los espacios en blanco en el programa de abajo para que imprime "nit"
(la inversa de la cadena de caracteres original "tin").

```python
original = "tin"
resultado = ____
para carácter original:
    resultado = ____
print(resultado)
```

::::::::::::::::: solución

## Solución

```python
original = "tin"
resultado = ""
para caracteres originales:
    resultado = caracteres + resultado
impresión (resultado)
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Práctica acumulando

Rellena los espacios en blanco en cada uno de los programas abajo
para producir el resultado indicado.

```python
# Longitud total de las cadenas en la lista: ["rojo", "verde", "azul"] => 12
total = 0
por palabra en ["rojo", "verde", "azul"]:
    ____ = ____ + len(palabra)
print(total)
```

::::::::::::::::: solución

## Solución

```python
total = 0
para la palabra en ["rojo", "verde", "azul"]:
    total = total + len(palabra)
print(total)
```

:::::::::::::::::::::::::

```python
# Lista de longitudes de palabra: ["rojo", "verde", "azul"] => [3, 5, 4]
longitudes = ____
por palabra en ["rojo", "verde", "azul"]:
    longitud. ___(____)
impresión(longitud)
```

::::::::::::::::: solución

## Solución

```python
longitudes = []
para la palabra en ["rojo", "verde", "azul"]:
    lengths.append(len(palabra))
print(lengths)
```

:::::::::::::::::::::::::

```python
# Concatena todas las palabras: ["rojo", "verde", "blue"] => "redgreenblue"
palabras = ["rojo", "verde", "blue"]
resultado = ____
para ____ en ____:
    ____
print(resultado)
```

::::::::::::::::: solución

## Solución

```python
palabras = ["rojo", "verde", "azul"]
resultado = ""
para palabras en palabras:
    resultado = resultado + palabra
print(resultado)
```

:::::::::::::::::::::::::

**Crea un acronimo:** A partir de la lista `["rojo", "verde", "blue"]`, crea el acrónimo `"RGB"` usando
un bucle for .

**Pista:** Es posible que necesites usar un método de cadena para formatear correctamente el acrónimo.

::::::::::::::::: solución

## Solución

```python
acrónimo = ""
para la palabra en ["rojo", "verde", "azul"]:
    acrónimo = acrónimo + palabra[0].upper()
print(acrónimo)
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Suma acumulativa

Reordenar y sangrar correctamente las líneas de código debajo de
para que impriman una lista con la suma acumulada de datos.
El resultado debe ser `[1, 3, 5, 10]`.

```python
acumulativo. ppend(total)
para el número en los datos:
acumulativo = []
total = total + número
total = 0
print(acumulativo)
datos = [1, ,2,5]
```

::::::::::::::::: solución

## Solución

```python
total = 0
datos = [1,2,2, 2, ]
acumulativo = []
para el número en los datos:
    total = total + número
    acumulativo. ppend(total)
print(acumulativo)
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Identificar errores de nombre variable

1. Lee el siguiente código e intenta identificar cuáles son los errores
   _sin_ ejecutarlo.
2. Ejecute el código y lea el mensaje de error.
   ¿Qué tipo de `NameError` cree que esto es?
   ¿Es una cadena sin comillas, una variable mal escrita o una variable
   que debería haber sido definida pero no lo era?
3. Corregir el error.
4. Repita los pasos 2 y 3, hasta que haya corregido todos los errores.

```python
for number in range(10):
    # use a if the number is a multiple of 3, de lo contrario use b
    if (Número % 3) == 0:
        mensaje = mensaje + un
    else:
        mensaje = mensaje + "b"
print(mensaje)
```

::::::::::::::::: solución

## Solución

- Los nombres de las variables Python son sensibles a mayúsculas y minúsculas: `number` y `Number` se refieren a diferentes variables.
- La variable `message` necesita ser inicializada como una cadena vacía.
- Queremos añadir la cadena `"a"` a `message`, no la variable indefinida `a`.

```python
mensaje = ""
para el número en el rango (10):
    # use un si el número es un múltiplo de 3, de lo contrario use b
    if (número % 3) == 0:
        message = message + "a"
    else:
        message = message + "b"
print(message)
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Identificando errores del artículo

1. Lee el siguiente código e intenta identificar cuáles son los errores
   _sin_ ejecutarlo.
2. Ejecute el código y lea el mensaje de error. ¿Qué tipo de error es?
3. Corregir el error.

```python
temporadas = ['Primavera', 'Verano', 'Fall', 'Invierno']
print('Mi temporada favorita es ', estaciones[4])
```

::::::::::::::::: solución

## Solución

Esta lista tiene 4 elementos y el índice para acceder al último elemento de la lista es `3`.

```python
temporadas = ['Primavera', 'Verano', 'Fall', 'Invierno']
print('Mi temporada favorita es ', estaciones[3])
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Un bucle _for loop_ ejecuta comandos una vez por cada valor en una colección.
- Un bucle `para` se compone de una colección, una variable de bucle y un cuerpo.
- La primera línea del ciclo `for` debe terminar con dos puntos y el cuerpo debe ser sangrado.
- La sangría siempre tiene sentido en Python.
- Las variables Loop pueden llamarse cualquier cosa (pero se recomienda encarecidamente tener un nombre significativo a la variable de bucle).
- El cuerpo de un bucle puede contener muchas declaraciones.
- Usa `range` para iterar sobre una secuencia de números.
- El patrón de Acumulador convierte muchos valores en uno.

::::::::::::::::::::::::::::::::::::::::::::::::::
