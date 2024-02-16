---
title: Variables y tareas
teaching: 10
exercises: 10
---

::::::::::::::::::::::::::::::::::::::::::::::::::: objetivos

- Escriba programas que asignen valores escalares a variables y realicen cálculos con esos valores.
- Rastrear correctamente los cambios de valor en los programas que usan asignación escalar.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::::: preguntas

- ¿Cómo puedo almacenar datos en programas?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Usar variables para almacenar valores.

- Las **variables** son nombres de valores.

- Nombres variables

  - puede **solo** contener letras, dígitos y guión bajo `_` (normalmente se usa para separar palabras en nombres de variables largas)
  - no puede comenzar con un dígito
  - son **sensibles a mayúsculas** (edad, edad y AGE son tres variables diferentes)

- El nombre también debe tener sentido para que u otro programador sepa lo que es

- Nombres variables que comienzan con guiones bajos como `__alistairs_real_age` tienen un significado especial
  así que no lo haremos hasta que entendamos la convención.

- En Python el símbolo `=` asigna el valor a la derecha al nombre a la izquierda.

- La variable se crea cuando se le asigna un valor.

- Aquí, Python asigna una edad a una variable `edad`
  y un nombre entre comillas a una variable `first_name`.

  ```python
  edad = 42
  primer_name = 'Adicionado'
  ```

## Usa `print` para mostrar valores.

- Python tiene una función integrada llamada `print` que imprime las cosas como texto.
- Llame a la función (i.e., dígale a Python que la ejecute) usando su nombre.
- Proporcionar valores a la función (es decir, las cosas a imprimir) entre paréntesis.
- Para añadir una cadena a la impresión, envuelva la cadena en comillas simples o dobles.
- Los valores pasados a la función se llaman **argumentos**

```python
print(first_name, 'es', edad, 'años viejos')
```

```output
Ahmed tiene 42 años
```

- `print` pone automáticamente un solo espacio entre los elementos para separarlos.
- Y envuelve a una nueva línea al final.

## Las variables deben crearse antes de que se usen.

- Si aún no existe una variable, o si el nombre ha sido mal escrito,
  Python reporta un error. (A diferencia de algunos idiomas, que "adivinan" un valor predeterminado.)

```python
imprimir(apellido)
```

```error
-------------------------------------------------------------------
Tracebo de error de nombre (última llamada)
<ipython-input-1-c1fbb4e96102> en <module>()
----> 1 print(last_name)

NameError: nombre 'last_name' no está definido
```

- La última línea de un mensaje de error suele ser la más informativa.
- Examinaremos los mensajes de error en detalle [later](17-scope.md#reading-error-messages).

:::::::::::::::::::::::::::::::::::::::::  callout

## Variables Persistir entre celdas

Tenga en cuenta que es la _orden_ de ejecución de celdas lo que es importante en un cuaderno de Jupyter, no el orden
en el que aparecen. Python recordará _todos_ el código que se ejecutó anteriormente, incluyendo cualquier variable que tengas
definida, independientemente del orden en el cuaderno. Por lo tanto, si defines variables más abajo del cuaderno y luego
(re)ejecuta las celdas más arriba, las definidas más abajo seguirán presentes. Como ejemplo, cree dos celdas con el
siguiente contenido, en este orden:

```python
print(myval)
```

```python
mival = 1
```

Si ejecutas esto en orden, la primera celda te dará un error. Sin embargo, si corres la primera célula _después_ de la segunda célula
imprimirá `1`. Para prevenir la confusión, puede ser útil usar la opción `Kernel` -> `Reiniciar y ejecutar todo` que
borra el intérprete y ejecuta todo, desde una pizarra limpia que va de arriba hacia abajo.

::::::::::::::::::::::::::::::::::::::::::::::::::

## Las variables se pueden utilizar en cálculos.

- Podemos usar variables en cálculos como si fueran valores.
  - Recuerda, asignamos el valor `42` a `age` hace unas pocas líneas.

```python
edad = edad + 3
print('Edad en tres años:', edad)
```

```output
Edad en tres años: 45
```

## Usa un índice para obtener un solo carácter de una cadena.

- Los caracteres (letras individuales, números, etc.) en una cadena son
  ordenados. Por ejemplo, la cadena `'AB'` no es la misma que `'BA'`. Debido a
  esta orden, podemos tratar la cadena como una lista de caracteres.
- Cada posición en la cadena (primero, segundo, etc.) se le da un número. Este número
  se llama un **índice** o a veces un suscripto.
- Los índices están numerados desde 0.
- Usa el índice de la posición entre corchetes cuadrados para obtener el carácter en esa posición

![Una línea de código Python, imprimir(atom_name[0]), demuestra que usar el índice cero sólo mostrará la letra inicial, en este caso 'h' para el helio. (figura/2_indexing.svg)

```python
atom_name = 'helium'
print(atom_name[0])
```

```output
h
```

## Usa una rebanada para obtener una subcadena.

- Una parte de una cadena se llama **subcadena**. A substring can be as short as a
  single character.
- Un elemento en una lista se llama un elemento. Whenever we treat a string as if it
  were a list, the string's elements are its individual characters.
- Una rebanada es una parte de una cadena (o, más generalmente, una parte de cualquier cosa similar a la lista).
- Tomamos una rebanada con la notación `[start:stop]`, donde `start` es el índice
  entero del primer elemento que queremos y `stop` es el índice entero de
  el elemento _justo después_ del último elemento que queremos.
- La diferencia entre `stop` y `start` es la longitud del corte.
- Tomar una rebanada no cambia el contenido de la cadena original. En cambio,
  tomar una rebanada devuelve una copia de parte de la cadena original.

```python
atom_name = 'sodio'
print(atom_name[0:3])
```

```output
sod
```

## Usa la función integrada `len` para encontrar la longitud de una cadena.

```python
print(len('helium'))
```

```output
6
```

- Las funciones anidadas se evalúan desde adentro,
  como en las matemáticas.

## Python es sensible a mayúsculas y minúsculas.

- Python piensa que las letras mayúsculas y minúsculas son diferentes,
  así que `Nombre` y `Nombre` son variables diferentes.
- Hay convenciones para usar letras mayúsculas al inicio de nombres de variables, así que por ahora usaremos letras minúsculas.

## Usar nombres significativos de variables.

- Python no importa lo que llamas variables siempre y cuando obedezcan las reglas
  (caracteres alfanuméricos y el guión bajo).

```python
flabadab = 42
ewr_422_yY = 'Ahmed'
print(ewr_422_yY, 'is', flabadab, 'años viejos')
```

- Utilice nombres significativos de variables para ayudar a otras personas a entender lo que hace el programa.
- La "otra persona" más importante es su futuro mismo.

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Intercambiar valores

Rellena la tabla que muestra los valores de las variables en este programa
_después_ de cada proposición es ejecutada.

```python
# Comando # Valor de x # Valor de y # Valor del intercambio #
x = 1. # # # #
y = 3. # # # #
swap = x # # # #
x = y # # # # #
y = swap # # # # # # # #
```

::::::::::::::::: solución

## Solución

```output
# Comando # Valor de x # Valor de y # Valor del intercambio #
x = 1. # 1. # # no definido # no definido
y = 3. # 1. # 3. # no definido #
intercambio = x # 1. # 3.0 # 1. #
x = y # 3. # 3.0 # 1. #
y = intercambio # 3. # 1.0 # 1. #
```

Estas tres líneas cambian los valores en `x` y `y` usando la variable `swap`
para almacenamiento temporal. Esto es un lenguaje de programación bastante común.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Predecir valores

¿Cuál es el valor final de `position` en el programa de abajo?
(Intenta predecir el valor sin ejecutar el programa,
luego revisa tu predicción.)

```python
inicial = 'izquierda'
posición = inicial
inicial = 'derecha'
```

::::::::::::::::: solución

## Solución

```python
impresión(posición)
```

```output
restante
```

La variable `initial` tiene asignado el valor `'left'`.
En la segunda línea, la variable `position` también recibe
el valor de cadena `'left'`. En tercera línea, la variable `initial` recibe el valor
`'right'`, pero la variable `position` mantiene su valor de cadena
de `'left'`.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Desafío

Si asignas `a = 123`,
¿qué sucede si intentas obtener el segundo dígito de `a` a través de `a[1]`?

::::::::::::::::: solución

## Solución

Los números no son cadenas o secuencias y Python generará un error si intentas realizar una operación de índice en un número
. En la [siguiente lección sobre tipos y conversión de tipos](03-types-conversion.md)
aprenderemos más sobre tipos y cómo convertir entre diferentes tipos. Si quieres el Nth dígito de un número que
puede convertirlo en una cadena usando la función integrada `str` y luego realizar una operación de índice en esa cadena.

```python
a = 123
print(a[1])
```

```error
TipoError: el objeto 'int' no está suscrito
```

```python
a = str(123)
print(a[1])
```

```output
2
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Elegir un nombre

¿Cuál es un mejor nombre de variable, `m`, `min`, o `minutes`?
¿Por qué?
Pista: piensa en qué código prefieres heredar
de alguien que está abandonando el laboratorio:

1. `ts = m * 60 + s`
2. `tot_seg = min * 60 + seg`
3. `total_seconds = minutos * 60 + segundos`

::::::::::::::::: solución

## Solución

`minutes` es mejor porque `min` podría significar algo como "mínimo"
(y en realidad es una función integrada en Python que cubriremos más adelante).

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Práctica de corte

¿Qué imprime el siguiente programa?

```python
atom_name = 'carbon'
print('atom_name[1:3] es:', atom_name[1:3])
```

::::::::::::::::: solución

## Solución

```output
atom_name[1:3] es: ar
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Conceptos de corte

Dado la siguiente cadena:

```python
species_name = "Acacia buxifolia"
```

¿Qué volverían estas expresiones?

1. `species_name[2:8]`
2. `species_name[11:]` (sin un valor después del coma)
3. `species_name[:4]` (sin un valor antes del coma)
4. `species_name[:]` (solo un coma)
5. `species_name[11:-3]`
6. `species_name[-5:-3]`
7. ¿Qué sucede cuando eliges un valor de 'stop' que está fuera de rango? (i.e., prueba `species_name[0:20]` o `species_name[:103]`)

::::::::::::::::: solución

## Soluciones

1. `species_name[2:8]` devuelve la subcadena `'acia b'`

2. `species_name[11:]` devuelve la subcadena `'folia'`, desde la posición 11 hasta el final

3. `species_name[:4]` devuelve la subcadena `'Acac'`, desde el inicio hasta pero no incluyendo la posición 4

4. `species_name[:]` devuelve la cadena completa `'Acacia buxifolia'`

5. `species_name[11:-3]` devuelve la subcadena `'fo'`, desde la posición 11 a la tercera última posición

6. `species_name[-5:-3]` también devuelve la subcadena `'fo'`, de la quinta última posición a la tercera última

7. Si una parte de la porción está fuera de rango, la operación no falla. `species_name[0:20]` da el mismo resultado que `species_name[0:]`, y `species_name[:103]` da el mismo resultado que `species_name[:]`

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Usar variables para almacenar valores.
- Usa `print` para mostrar valores.
- Las variables persisten entre las células.
- Las variables deben crearse antes de que se usen.
- Las variables se pueden utilizar en cálculos.
- Usa un índice para obtener un solo carácter de una cadena.
- Usa una rebanada para obtener una subcadena.
- Usa la función integrada `len` para encontrar la longitud de una cadena.
- Python es sensible a mayúsculas y minúsculas.
- Usar nombres significativos de variables.

::::::::::::::::::::::::::::::::::::::::::::::::::
