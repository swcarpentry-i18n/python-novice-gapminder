---
title: Listas
teaching: 10
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- Explicar por qué los programas necesitan colecciones de valores.
- Escribe programas que crean listas planas, los indizan, los rebanan y los modifican mediante llamadas de asignación y métodos.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::::: preguntas

- ¿Cómo puedo almacenar múltiples valores?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Una lista almacena muchos valores en una sola estructura.

- Hacer cálculos con un centenar de variables llamadas `pressure_001`, `pressure_002`, etc.,
  sería al menos tan lento como hacerlo a mano.
- Utilice una _lista_ para almacenar muchos valores juntos.
  - Contenidos dentro de corchetes `[...]`.
  - Valores separados por comas `,`.
- Usa `len` para averiguar cuántos valores hay en una lista.

```python
pressures = [0.273, 0.275, 0.277, 0.275, 0.276]
print('presures:', pressures)
print('longitud:', len(pressures))
```

```output
pressures: [0.273, 0.275, 0.277, 0.275, 0.276]
length: 5
```

## Utilice el índice de un elemento para obtenerlo de una lista.

- Al igual que las cadenas.

```python
print('Elemento zeroth de presiones:', presiona[0])
print('cuarto elemento de presiones:', presiona[4])
```

```output
Objeto de presiones cero: 0.273
cuarto objeto de presiones: 0.276
```

## Los valores de las listas se pueden reemplazar asignándolas.

- Utilice una expresión de índice a la izquierda de la asignación para reemplazar un valor.

```python
presiones[0] = 0.265
print('presiones es ahora:', presiones)
```

```output
pressures es ahora: [0.265, 0.275, 0.277, 0.275, 0.276]
```

## Añadir elementos a una lista lo alarga.

- Usa `list_name.append` para añadir elementos al final de una lista.

```python
primes = [2, 3, 5]
print('primes es inicialmente:', primes)
primes.append(7)
print('primes se ha convertido:', primes)
```

```output
primes es inicialmente: [2, 3, 5]
primos se han convertido: [2, 3, 5, 7]
```

- `append` es un _método_ de listas.
  - Como una función, pero atada a un objeto en particular.
- Usa `object_name.method_name` para llamar a métodos.
  - Deliberamente se asemeja a la forma en que nos referimos a las cosas en una biblioteca.
- Nos encontraremos con otros métodos de listas a medida que vayamos.
  - Use `help(list)` para una vista previa.
- `extend` es similar a `append`, pero te permite combinar dos listas.  Por ejemplo:

```python
teen_primes = [11, 13, 17, 19]
middle_aged_primes = [37, 41, 43, 47]
print('primes es actualmente:', primes)
primes. xtend(teen_primes)
print('primes se ha convertido:', primes)
primes.append(middle_aged_primes)
print('primes se ha convertido por fin:', primes)
```

```output
los primes se están convirtiendo actualmente: [2, 3, 5, 7]
los primos se han convertido: [2, 3, 5, 7, 11, 13, 17, 19]
los primos finalmente se han convertido: [2, 3, 5, 7, 11, 13, 17, 19, [37, 41, 43, 47]]
```

Ten en cuenta que mientras que `extend` mantiene la estructura "plana" de la lista, añadir una lista a una lista significa que
el último elemento en `primes` será una lista, no un entero. Las listas pueden contener valores de cualquier tipo
; por lo tanto, las listas de listas son posibles.

## Usa `del` para eliminar elementos de una lista por completo.

- Utilizamos `del list_name[index]` para eliminar un elemento de una lista (en el ejemplo, 9 no es un número primo) y así acortarlo.
- `del` no es una función o un método, sino una sentencia en el idioma.

```python
primes = [2, 3, 5, 7, 9]
print('primes antes de eliminar el último artículo:', primes)
del primes[4]
print('primes después de eliminar el último artículo:', primes)
```

```output
primes antes de eliminar el último artículo: [2, 3, 5, 7, 9]
primes después de eliminar el último artículo: [2, 3, 5, 7]
```

## La lista vacía no contiene valores.

- Use `[]` por sí solo para representar una lista que no contiene ningún valor.
  - "El cero de listas".
- Ayuda como punto de partida para recolectar valores
  (que veremos en el [próximo episodio](12-for-loops.md)).

## Las listas pueden contener valores de diferentes tipos.

- Una sola lista puede contener números, cadenas y cualquier otra cosa.

```python
goals = [1, 'Crear listas', 2, 'Extraer elementos de listas', 3, 'Modificar listas']
```

## Las cadenas de caracteres pueden ser indexadas como listas.

- Obtiene caracteres individuales de una cadena de caracteres usando índices entre corchetes.

```python
element = 'carbon'
print('zeroth character:', element[0])
print('third character:', element[3])
```

```output
personaje de cero: c
tercer personaje: b
```

## Las cuerdas de caracteres son inmutables.

- No se pueden cambiar los caracteres de una cadena después de haber sido creados.
  - _Inmutable_: no se puede cambiar después de la creación.
  - En contraste, las listas son _mutables_: pueden ser modificadas en su lugar.
- Python considera que la cadena es un valor único con partes,
  no una colección de valores.

```python
elemento[0] = 'C'
```

```error
TipoError: el objeto 'str' no soporta la asignación de elementos
```

- Las listas y las cadenas de caracteres son ambas _colecciones_.

## Indexar más allá del final de la colección es un error.

- Python reporta un `IndexError` si intentamos acceder a un valor que no existe.
  - Esto es una especie de [error de runtime](04-built-in.md).
  - No se puede detectar porque el código es analizado
    porque el índice podría calcularse basándose en los datos.

```python
print('99 elemento del elemento es:', elemento[99])
```

```output
IndexError: índice de cadena fuera de rango
```

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Rellena los espacios en blanco

Rellena los espacios en blanco para que el programa de abajo produzca la salida que se muestra.

```python
values = ____
valores.____(1)
valores.____(3)
valores.____(5)
print('primera vez:', valores)
valores = valores[____]
print('segunda vez:', valores)
```

```output
primera vez: [1, 3, 5]
segunda vez: [3, 5]
```

::::::::::::::::: solución

## Solución

```python
values = []
values.append(1)
values.append(3)
values.append(5)
print('first time:', values)
values = values[1:]
print('second time:', values)
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## ¿Qué tan grande es una corteza?

Si `start` y `stop` son ambos enteros no negativos,
¿cuánto es la lista de `values[start:stop]`?

::::::::::::::::: solución

## Solución

La lista de `values[start:stop]` tiene hasta `stop - start`.  Por ejemplo,
`values[1:4]` tiene los 3 elementos `values[1]`, `values[2]`, y `values[3]`.
¿Por qué "hasta"? As we saw in [episode 2](02-variables.md),
if `stop` is greater than the total length of the list `values`,
we will still get a list back but it will be shorter than expected.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## De cadenas a listas y atrás

Dado esto:

```python
print('string a lista:', list('tin'))
print('list to string:', ''.join(['g', 'o', 'l', 'd']))
```

```output
cadena a lista: ['t', 'i', 'n']
lista a cadena: oro
```

1. ¿Qué hace `list('alguna cadena')`?
2. ¿Qué genera `'-'.join(['x', 'y', 'z'])`?

::::::::::::::::: solución

## Solución

1. [`list('some string')`](https://docs.python.org/3/library/stdtypes.html#list) convierte una cadena en una lista que contiene todos sus caracteres.

2. [`join`](https\://docs.python.org/3/library/stdtypes.html#str. oin) devuelve una cadena que es la _concatenación_
   de cada elemento de cadena en la lista y añade el separador entre cada elemento en la lista. Esto resulta en
   `x-y-z`. El separador entre los elementos es la cadena que proporciona este método.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Trabajando con el final

¿Qué imprime el siguiente programa?

```python
elemento = 'helium'
print(element[-1])
```

1. ¿Cómo interpreta Python un índice negativo?
2. Si una lista o cadena tiene N elementos,
   cuál es el índice más negativo que puede ser utilizado con seguridad con ella, ¿
   y qué ubicación representa ese índice?
3. Si `values` es una lista, ¿qué hace `del values[-1]`?
4. ¿Cómo se pueden mostrar todos los elementos excepto el último sin cambiar `valores`?
   (Sugerencia: necesitará combinar cortes e índices negativos.)

::::::::::::::::: solución

## Solución

El programa imprime `m`.

1. Python interpreta un índice negativo como comenzando desde el final (a diferencia de
   empezando desde el principio).  El último elemento es `-1`.

2. El último índice que puede utilizarse con seguridad con una lista de elementos N es el elemento
   `-N`, que representa el primer elemento.

3. `del values[-1]` elimina el último elemento de la lista.

4. `valores[:-1]`

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Pasar a través de una lista

¿Qué imprime el siguiente programa?

```python
elemento = 'fluorine'
print(element[::2]) Impresión
(element[::-1])
```

1. Si escribimos una porción como `low:high:stride`, ¿qué hace `stride`?
2. ¿Qué expresión seleccionaría todos los elementos numerados pares de una colección?

::::::::::::::::: solución

## Solución

El programa imprime

```python
pelaje
eniroulfo
```

1. `stride` es el tamaño del paso del corte.

2. La porción `1::2` selecciona todos los elementos numerados pares de una colección: comienza
   con el elemento `1` (que es el segundo elemento, ya que la indexación comienza en `0`),
   continúa hasta el final (ya que no se da ningún `end`), y usa un tamaño de paso de `2`
   (i. ., selecciona cada segundo elemento).

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Límites de corte

¿Qué imprime el siguiente programa?

```python
elemento = 'lithium'
print(element[0:20])
print(element[-1:3])
```

::::::::::::::::: solución

## Solución

```output
lithium

```

La primera sentencia imprime toda la cadena, ya que la rebanada sobrepasa la longitud total de la cadena.
La segunda sentencia devuelve una cadena vacía, porque la porción va "fuera de los límites" de la cadena.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Ordenar y ordenar

¿Qué imprimen estos dos programas?
En términos simples, explica la diferencia entre `sorted(letters)` y `letters.sort()`.

```python
# Programa A
letras = list('oro')
resultado = ordenado(letras)
print('letras es', letras, 'y resultado es', resultado)
```

```python
# Programa B
letras = list('oro')
resultado = letters.sort()
print('letras es', letras, 'y resultado es', resultado)
```

::::::::::::::::: solución

## Solución

Programa A Impresiones

```output
las letras son ['g', 'o', 'l', 'd'] y el resultado es ['d', 'g', 'l', 'o']
```

Impresiones del programa B

```output
las letras son ['d', 'g', 'l', 'o'] y el resultado no es ninguno
```

`sorted(letras)` devuelve una copia ordenada de la lista `letras` (la
original lista `letras` permanece sin cambios), mientras que `letras. ort()` ordena la lista
`letters` en su lugar y no devuelve nada.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Copiando (o no)

¿Qué imprimen estos dos programas?
En términos simples, explica la diferencia entre `new = old` y `new = old[:]`.

```python
# Programa A
viejo = list('oro')
new = viejo # asignación simple
new[0] = 'D'
print('new is', nuevo, 'y viejo es', viejo)
```

```python
# Programa B
viejo = list('oro')
new = antiguo[:] # asignar una porción
new[0] = 'D'
print('new is', nuevo, 'y viejo es', viejo)
```

::::::::::::::::: solución

## Solución

Programa A Impresiones

```output
new es ['D', 'o', 'l', 'd'] y viejo es ['D', 'o', 'l', 'd']
```

Impresiones del programa B

```output
new es ['D', 'o', 'l', 'd'] y viejo es ['g', 'o', 'l', 'd']
```

`new = old` hace que `new` sea una referencia a la lista `old`; `new` y `old` apuntan
hacia el mismo objeto.

`new = old[:]` sin embargo crea un nuevo objeto de lista `new` que contiene todos los elementos
de la lista `old`; `new` y `old` son objetos diferentes.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Una lista almacena muchos valores en una sola estructura.
- Utilice el índice de un elemento para obtenerlo de una lista.
- Los valores de las listas se pueden reemplazar asignándolas.
- Añadir elementos a una lista lo alarga.
- Usa `del` para eliminar elementos de una lista por completo.
- La lista vacía no contiene valores.
- Las listas pueden contener valores de diferentes tipos.
- Las cadenas de caracteres pueden ser indexadas como listas.
- Las cuerdas de caracteres son inmutables.
- Indexar más allá del final de la colección es un error.

::::::::::::::::::::::::::::::::::::::::::::::::::
