---
title: Tipos de datos y conversión de tipo
teaching: 10
exercises: 10
---

::::::::::::::::::::::::::::::::::::::::::::::::::: objetivos

- Explicar las diferencias de clave entre enteros y números de punto flotante.
- Explicar las diferencias entre números y cadenas de caracteres.
- Utilice funciones integradas para convertir entre enteros, números de punto flotante y cadenas.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::::: preguntas

- ¿Qué tipo de datos almacenan los programas?
- ¿Cómo puedo convertir un tipo a otro?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Cada valor tiene un tipo.

- Cada valor de un programa tiene un tipo específico.
- Integer (`int`): representa números enteros positivos o negativos como 3 o -512.
- Número de punto flotante (`float`): representa números reales como 3.14159 o -2.5.
- Cadena de caracteres (generalmente llamada "string", `str`): texto.
  - Escrito en comillas simples o comillas dobles (siempre y cuando coincidan).
  - Las comillas no se imprimen cuando se muestra la cadena.

## Usa la función integrada `type` para encontrar el tipo de valor.

- Usa la función integrada `type` para averiguar qué tipo de valor tiene.
- Funciona también en variables.
  - Pero recuerde: el _valor_ tiene el tipo --- la _variable_ es sólo una etiqueta.

```python
print(type(52))
```

```output
<class 'int'>
```

```python
fitness = 'promedio'
print(type(fitness))
```

```output
<class 'str'>
```

## Los tipos controlan qué operaciones (o métodos) se pueden realizar sobre un valor dado.

- El tipo de valor determina lo que el programa puede hacer.

```python
print(5 - 3)
```

```output
2
```

```python
print('hello' - 'h')
```

```error
-------------------------------------------------------------------
TypeError Traceback (última llamada)
<ipython-input-2-67f5626a1e07> en <module>()
----> 1 print('hola' - 'h')

TipoError: tipo de operando(s) no soportado para -: 'str' y 'str'
```

## Puede utilizar los operadores "+" y "\*" en cadenas.

- "Añadir" cadenas de caracteres las concatena.

```python
full_name = 'Ahmed' + ' + 'Walsh'
print(full_name)
```

```output
Marisco Ahmed
```

- Multiplicar una cadena de caracteres por un entero _N_ crea una nueva cadena que consiste en esa cadena de caracteres repetida _N_.
  - Dado que la multiplicación se repite la adición.

```python
separator = '=' * 10
print(separator)
```

```output
==========
```

## Las cadenas tienen una longitud (pero no los números).

- La función integrada `len` cuenta el número de caracteres en una cadena.

```python
print(len(full_name))
```

```output
11
```

- Pero los números no tienen una longitud (no ni siquiera cero).

```python
print(len(52))
```

```error
-------------------------------------------------------------------
TypeError Traceback (última llamada)
<ipython-input-3-f769e8e8097d> en <module>()
----> 1 print(len(52))

Tipo Error: objeto de tipo 'int' no tiene len()
```

## Debe convertir números a cadenas o viceversa cuando opere en ellas. {#convert-numbers-and-strings}

- No se pueden agregar números y cadenas.

```python
print(1 + '2')
```

```error
-------------------------------------------------------------------
TypeError Traceback (la última llamada más reciente)
<ipython-input-4-fe4f54a023c6> en <module>()
----> 1 print(1 + '2')

TipoError: tipo de operando(s) no soportado para +: 'int' y 'str'
```

- No permitido porque es ambiguo: ¿deben `1 + '2'` ser `3` o `'12'`?
- Algunos tipos pueden ser convertidos a otros tipos usando el nombre del tipo como función.

```python
print(1 + int('2'))
print(str(1) + '2')
```

```output
3
12
```

## Puede mezclar enteros y flotantes libremente en las operaciones.

- Enteros y números de punto flotante pueden ser mezclados en aritmética.
  - Python 3 convierte automáticamente los enteros a flotantes según sea necesario.

```python
print('la mitad es', 1 / 2.0)
print('tres cuadrados es', 3.0 ** 2)
```

```output
la mitad es 0.5
tres cuadrados es 9.0
```

## Las variables sólo cambian el valor cuando algo se les asigna.

- Si hacemos que una celda en una hoja de cálculo dependa de otra,
  y actualice la segunda,
  las actualizaciones anteriores automáticamente.
- Esto **no** ocurre en los lenguajes de programación.

```python
variable_one = 1
variable_two = 5 * variable_one
variable_one = 2
print('primero es', variable_one, 'y segundo es', variable_dos)
```

```output
el primero es 2 y el segundo es 5
```

- La computadora lee el valor de `variable_one` al realizar la multiplicación,
  crea un nuevo valor y lo asigna a `variable_dos`.
- Después, el valor de `variable_two` se establece al nuevo valor y _no depende de `variable_one`_ por lo que su valor
  no cambia automáticamente cuando `variable_one` cambia.

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Fracciones

¿Qué tipo de valor es 3.4?
¿Cómo se puede averiguar?

::::::::::::::::: solución

## Solución

Es un número de punto flotante (a menudo abreviado "float").
Es posible averiguar usando la función integrada `type()`.

```python
print(type(3.4))
```

```output
<class 'float'>
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Conversión automática de tipo

¿Qué tipo de valor es 3.25 + 4?

::::::::::::::::: solución

## Solución

Es un float:
enteros se convierten automáticamente a floats cuando sea necesario.

```python
resultado = 3.25 + 4
print(resultado, 'is', type(resultado))
```

```output
7,25 es <class 'float'>
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Elija un tipo

¿Qué tipo de valor (entero, número de coma flotante o cadena de caracteres)
se usaría para representar cada uno de los siguientes?  Trata de encontrar más de una buena respuesta para cada problema.  Por ejemplo, en # 1, ¿cuándo se contarían días con una variable de punto flotante tiene más sentido que usar un entero?

1. Número de días desde el comienzo del año.
2. Tiempo transcurrido desde el comienzo del año hasta ahora en días.
3. Número de serie de un equipo de laboratorio.
4. Edad de un ejemplar de laboratorio
5. Población actual de una ciudad.
6. Población media de una ciudad a lo largo del tiempo.

::::::::::::::::: solución

## Solución

Las respuestas a las preguntas son:

1. Entero, ya que el número de días se situaría entre 1 y 365.

2. Punto flotante, ya que se requieren días fraccionales

3. Cadena de caracteres si el número de serie contiene letras y números, de lo contrario entero si el número de serie consiste sólo en números

4. ¡Esto variará! ¿Cómo se define la edad de un ejemplo? días enteros desde la colección (entero)? fecha y hora (cadena)?

5. Elija un punto flotante para representar la población como grandes agregados (por ejemplo, millones), o entero para representar la población en unidades de individuos.

6. Número de punto flotante, ya que es probable que un promedio tenga una parte fraccional.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Tipos de división

En Python 3, el operador `//` realiza la división de pisos enteros (número entero), el operador `/` realiza la división de punto flotante
, y el operador `%` (o _modulo_) calcula y devuelve el resto de la división entera:

```python
print('5 // 3:', 5 // 3)
print('5 / 3:', 5 / 3)
print('5 % 3:', 5 % 3)
```

```output
5 // 3: 1
5 / 3: 1.66666666666666666667
5 % 3: 2
```

Si `num_subjects` es el número de sujetos que participan en un estudio,
y `num_per_survey` es el número que puede participar en una sola encuesta,
escribir una expresión que calcule el número de encuestas necesarias
para llegar a todos una vez.

::::::::::::::::: solución

## Solución

Queremos el número mínimo de encuestas que llega a todos una vez, que es
el valor redondeado de `num_subjects/ num_per_survey`. Esto es
equivalente a realizar una división de suelo con `//` y sumar 1. Before
the division we need to subtract 1 from the number of subjects to deal with
the case where `num_subjects` is evenly divisible by `num_per_survey`.

```python
num_subjects = 600
num_per_survey = 42
num_surveys = (num_subjects - 1) // num_per_survey + 1

print(num_subjects, 'subjects,', num_per_survey, 'per survey:', num_surveys)
```

```output
600 temas, 42 por encuesta: 15
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Cadenas a números

Donde razonable, `float()` convertirá una cadena a un número de punto flotante,
y `int()` convertirán un número de punto decimal en un entero:

```python
print("string to float:", float("3.4"))
print("float to int:", int(3.4))
```

```output
string a float: 3.4
decimal a int: 3
```

Sin embargo, si la conversión no tiene sentido, se producirá un mensaje de error.

```python
print("string to float:", float("Hola mundo!"))
```

```error
-------------------------------------------------------------------
Traceback de errores de valor (la última llamada)
<ipython-input-5-df3b790bf0a2> en <module>
----> 1 print("string to float:", float("Hola mundo! ))

ValueError: no se pudo convertir la cadena a float: '¡Hola mundo!'
```

Dada esta información, ¿qué esperas que haga el siguiente programa?

¿Qué hace realmente?

¿Por qué cree usted que es así?

```python
print("fractional string to int:", int("3.4"))
```

::::::::::::::::: solución

## Solución

¿Qué esperas que haga este programa? No sería tan poco razonable esperar que el comando `int` de Python 3 a
convierta la cadena "3. " a 3.4 y una conversión adicional de tipo a 3. Después de todo, Python 3 realiza un montón de otra magia* ¿No es esa parte de su encantamiento?

```python
int("3.4")
```

```output
-------------------------------------------------------------------
Traceback de errores de valor (la última llamada)
<ipython-input-2-ec6729dfccdc> en <module>
----> 1 int("3. ")
ValueError: literal inválido para int() con base 10: '3.4'
```

Sin embargo, Python 3 lanza un error. ¿Por qué? Ser coherente, posiblemente. Si le preguntas a Python que realice dos typecasts
consecutivos, debe convertirlo explícitamente en código.

```python
int(float("3.4"))
```

```output
3
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Aritmética con diferentes tipos

¿Cuál de las siguientes opciones devolverá el número de coma flotante `2.0`?
Nota: puede haber más de una respuesta correcta.

```python
primero = 1.0
segundo = "1"
tercero = "1.1"
```

1. `primero + float(segundo)`
2. `float(segundo) + float(tercero)`
3. `primero + int(tercero)`
4. `primero + int(float(tercero)`
5. `int(primero) + int(float(tercero)`
6. `2.0 * segundo`

::::::::::::::::: solución

## Solución

Respuesta: 1 y 4

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Números complejos

Python proporciona números complejos,
que están escritos como `1.0+2.0j`.
Si `val` es un número complejo,
sus partes reales e imaginarias pueden ser accedidas usando _notación de puntos_
como `val.real` y `val.imag`.

```python
a_complex_number = 6 + 2j
print(a_complex_number.real)
print(a_complex_number.imag)
```

```output
6.0
2.0
```

1. ¿Por qué crees que Python usa `j` en lugar de `i` para la parte imaginaria?
2. ¿Qué esperas que produzca `1 + 2j + 3`?
3. ¿Qué esperas que sea `4j`?  ¿Qué hay de `4 j` o `4 + j`?

::::::::::::::::: solución

## Solución

1. Los tratamientos matemáticos estándar típicamente usan `i` para denotar un número imaginario. Sin embargo, de los informes de los medios de comunicación,
   fue una convención establecida desde la ingeniería eléctrica que ahora presenta un área técnicamente costosa para un cambio
   . Stack Overflow proporciona una explicación adicional y una discusión
   .

2. `(4+2j)`

3. `4j` y `Syntax Error: sintaxis no válida`. En estos últimos casos, `j` se considera una variable y la proposición
   depende de si `j` está definido y si es así, su valor asignado.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Cada valor tiene un tipo.
- Usa la función integrada `type` para encontrar el tipo de valor.
- Los tipos controlan qué operaciones se pueden hacer en valores.
- Las cadenas pueden ser añadidas y multiplicadas.
- Las cadenas tienen una longitud (pero no los números).
- Debe convertir números a cadenas o viceversa cuando opere en ellas.
- Puede mezclar enteros y flotantes libremente en las operaciones.
- Las variables sólo cambian el valor cuando algo se les asigna.

::::::::::::::::::::::::::::::::::::::::::::::::::
