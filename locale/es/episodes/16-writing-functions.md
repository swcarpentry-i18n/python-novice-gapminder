---
title: Funciones de escritura
teaching: 10
exercises: 15
---

::::::::::::::::::::::::::::::::::::::: objectives

- Explicar e identificar la diferencia entre la definición de la función y la llamada a la función.
- Escriba una función que tome un pequeño número fijo de argumentos y produzca un único resultado.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::::: preguntas

- ¿Cómo puedo crear mis propias funciones?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Descomprima los programas en funciones para hacerlos más fáciles de entender.

- Los seres humanos sólo pueden guardar algunos elementos en la memoria de trabajo a la vez.
- Entender ideas más grandes/más complicadas comprendiendo y combinando piezas.
  - Componentes en una máquina.
  - Lemas al probar teoremas.
- Las funciones tienen el mismo propósito en los programas.
  - _Encapsular_ complejidad para que podamos tratarla como una sola "cosa".
- También permite _reutilizar_.
  - Escribe una vez, usa muchas veces.

## Definir una función usando `def` con un nombre, parámetros y un bloque de código.

- Comience la definición de una nueva función con `def`.
- Seguido con el nombre de la función.
  - Debe obedecer las mismas reglas que los nombres de variables.
- Luego _parámetros_ en paréntesis.
  - Paréntesis vacías si la función no toma ninguna entrada.
  - Lo debatiremos en detalle dentro de un momento.
- Luego un dos puntos.
- Entonces un bloque de código sangrado.

```python
def print_greeting():
    print('¡Hola!')
    print('El clima es bueno hoy')
    print('¿Derecho?')
```

## Definir una función no la ejecuta.

- Definir una función no la ejecuta.
  - Como asignar un valor a una variable.
- Debe llamar a la función para ejecutar el código que contiene.

```python
print_saludo()
```

```output
¡Hola!
```

## Los argumentos en una llamada a función se corresponden con sus parámetros definidos.

- Las funciones son más útiles cuando pueden operar con diferentes datos.
- Especifique _parámetros_ al definir una función.
  - Se convierten en variables cuando se ejecuta la función.
  - Se asignan los argumentos en la llamada (es decir, los valores pasados a la función).
  - Si no nombra los argumentos al usarlos en la llamada, los argumentos coincidirán con parámetros
    en el orden en que los parámetros están definidos en la función.

```python
def print_date(year, month, day):
    joined = str(year) + '/' + str(month) + '/' + str(day)
    print(joined)

print_date(1871, 3, 19)
```

```output
1871/3/19
```

O, podemos nombrar los argumentos cuando llamamos a la función, lo que nos permite especificar
en cualquier orden y añade claridad al sitio de llamadas; de lo contrario como
uno está leyendo el código que podrían olvidar si el segundo argumento es el mes
o el día, por ejemplo.

```python
print_date(mes=3, día=19, año=1871)
```

```output
1871/3/19
```

- Via [Twitter](https://twitter.com/minisciencegirl/status/693486088963272705):
  `()` contiene los ingredientes para la función
  mientras que el cuerpo contiene la receta.

## Las funciones pueden devolver un resultado a su persona que llama usando `return`.

- Usa `return ...` para devolver un valor a la persona que llama.
- Puede ocurrir en cualquier parte de la función.
- Pero las funciones son más fáciles de entender si `return` ocurre:
  - Al principio de tratar casos especiales.
  - Al final, con un resultado final.

```python
promedio def (valores):
    if len(valores) == 0:
        return None
    return sum(valores) / len(valores)
```

```python
a = promedio([1, 3, 4])
print('promedio de valores reales:', a)
```

```output
promedio de valores reales: 2.66666666666666666665
```

```python
print('promedio de lista vacía:', promedio([]))
```

```output
promedio de lista vacía: ninguna
```

- Recuerde: [cada función devuelve algo](04-built-in.md).
- Una función que no `devuelve explícitamente` un valor automáticamente devuelve `Ninguno`.

```python
resultado = print_date(1871, 3, 19)
print('resultado de la llamada es:', resultado)
```

```output
1871/3/19
el resultado de la llamada es: Ninguno
```

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Identificar errores de sintaxis

1. Lee el siguiente código e intenta identificar cuáles son los errores
   _sin_ ejecutarlo.
2. Ejecute el código y lea el mensaje de error.
   ¿Es un `SyntaxError` o un `IndentationError`?
3. Corregir el error.
4. Repita los pasos 2 y 3 hasta que haya corregido todos los errores.

```python
def another_function
  print("Los errores de sintaxis son molestos. )
   print("Pero al menos python nos dice sobre ellos!") impresión
  ("Así que normalmente no son demasiado difíciles de arreglar.")
```

::::::::::::::::: solución

## Solución

```python
def another_function():
  print("Los errores de sintaxis son molestos. )
  print("Pero al menos Python nos dice sobre ellos!") impresión
  ("Así que normalmente no son demasiado difíciles de arreglar.")
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Definición y uso

¿Qué imprime el siguiente programa?

```python
def report(pressure):
    print('pressure is', pressure)

print('llamando', informe, 22.5)
```

::::::::::::::::: solución

## Solución

```output
llamando <function report at 0x7fd128ff1bf8> 22.5
```

Una llamada a función siempre necesita paréntesis, de lo contrario obtendrá la dirección de memoria del objeto de función. Por lo tanto, si queríamos llamar a la función llamada informe, y darle el valor 22. para informar sobre ello, podríamos hacer una llamada a nuestra función de la siguiente forma

```python
print("calling")
report(22.5)
```

```output
llamar a presión
es 22,5
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Orden de operaciones

1. ¿Qué hay de malo en este ejemplo?

```python
result = print_time(11, 37, 59)

def print_time(hora, minuto, segundo):
   time_string = str(hour) + ':' + str(minuto) + ':' + str(second)
   print(time_string)
```

2. Después de solucionar el problema de arriba, explica por qué ejecutar este código de ejemplo:

```python
result = print_time(11, 37, 59)
print('resultado de la llamada es:', resultado)
```

da esta salida:

```output
11:37:59
el resultado de la llamada es: Ninguna
```

3. ¿Por qué es el resultado de la llamada `Ninguno`?

::::::::::::::::: solución

## Solución

1. El problema con el ejemplo es que la función `print_time()` es definida _después_ de la llamada a la función es hecha. Python
   no sabe cómo resolver el nombre `print_time` ya que aún no ha sido definido y generará un `NameError` e. .,
   `NameError: el nombre 'print_time' no está definido`

2. La primera línea de salida `11:37:59` está impresa por la primera línea de código, `result = print_time(11, 37, 59)` que vincula el valor
   devuelto al invocar `print_time` a la variable `result`. La segunda línea es de la segunda llamada de impresión para imprimir el contenido
   de la variable `resultado`.

3. `print_time()` no `devuelve explícitamente un valor, por lo que automáticamente devuelve `Ninguno\`.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Encapsulación

Fill in the blanks to create a function that takes a single filename as an argument,
loads the data in the file named by the argument,
and returns the minimum value in that data.

```python
import pandas as as pd

def min_in_data(____):
    data = ____
    return ____
```

::::::::::::::::: solución

## Solución

```python
import pandas as as pd

def min_in_data(filename):
    data = pd.read_csv(filename)
    return data.min()
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Encuentra el primero

Rellena los espacios en blanco para crear una función que tome una lista de números como argumento
y devuelve el primer valor negativo en la lista.
¿Qué hace su función si la lista está vacía? ¿Qué pasa si la lista no tiene números negativos?

```python
def first_negative(values):
    para v en ____:
        if ____:
            return ____
```

::::::::::::::::: solución

## Solución

```python
def first_negative(values):
    para v en valores:
        if v < 0:
            return v
```

Si se pasa una lista vacía o una lista con todos los valores positivos a esta función, devuelve `Ninguno`:

```python
my_list = []
print(first_negative(my_list))
```

```output
Ninguna
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Llamando por nombre

Anteriormente vimos esta función:

```python
def print_date(year, month, day):
    joined = str(year) + '/' + str(month) + '/' + str(day)
    print(joined)
```

Vimos que podemos llamar a la función usando _argumentos nombrados_, así:

```python
print_date(día=1, mes=2, año=2003)
```

1. ¿Qué imprime `print_date(day=1, mes=2, año=2003)`?
2. ¿Cuándo has visto una llamada de función como esta antes?
3. ¿Cuándo y por qué es útil llamar funciones de esta manera?

::::::::::::::::: solución

## Solución

1. `2003/2/1`

2. Vimos ejemplos de usar _argumentos nombrados_ al trabajar con la biblioteca de pandas. Por ejemplo, al leer en un conjunto de datos
   usando `data = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')`, el último argumento `index_col` es un argumento llamado
   .

3. Usar argumentos nombrados puede hacer que el código sea más legible ya que desde la función se puede ver qué nombre tienen los diferentes argumentos
   dentro de la función. También puede reducir las posibilidades de pasar argumentos en el orden incorrecto, ya que usando los argumentos nombrados
   el orden no importa.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Capsulación de un bloque Si/Imprimir

El siguiente código se ejecutará en una impresora de etiquetas para huevos de pollo.  Una escala digital reportará una masa de huevo de pollo (en gramos)
a la computadora y luego la computadora imprimirá una etiqueta.

```python
import random
for i in range(10):

    # simulating the mass of a chicken egg
    # the (random) mass will be 70 +/- 20 grams
    mass = 70 + 20. * (2.0 * random.random() - 1. )

    imprimir(masa)

    # maquinaria de talla de huevos imprime una etiqueta
    si masa >= 85:
        print("jumbo")
    masa elif >= 70:
        print("grande")
    masa elif < 70 y masa >= 55:
        impresión ("mediana")
    más:
        impresión ("pequeña")
```

El bloque if que clasifica los huevos puede ser útil en otras situaciones,
para evitar repetirlo, podríamos plegarlo en una función, `get_egg_label()`.
Revisar el programa para usar la función nos daría esto:

```python
# versión revisada
importar
al azar para i en rango(10):

    # simular la masa de un huevo de pollo
    # la masa (aleatoria) será 70 +/- 20 gramos
    masa = 70 + 20. * (2.0 * random.random() - 1.0)

    print(masa, get_egg_label(mass))

```

1. Crea una definición de función para `get_egg_label()` que funcionará con el programa revisado arriba.  Tenga en cuenta que el valor de retorno de la función `get_egg_label()` será importante. La salida de ejemplo del programa anterior sería `71.23 grande`.
2. Un huevo sucio podría tener una masa de más de 90 gramos, y un huevo estropeado o roto probablemente tendrá una masa de menos de 50 gramos.  Modifica tu función `get_egg_label()` para tener en cuenta estas condiciones de error. La salida de ejemplo podría ser `25 demasiado ligera, probablemente estropeada`.

::::::::::::::::: solución

## Solución

```python
def get_egg_label(mass):
    # La maquinaria de tamaño del huevo imprime una etiqueta
    egg_label = "Sin etiquetar"
    if mass >= 90:
        egg_label = "warning: el huevo podría ser dirty"
    elif masa >= 85:
        egg_label = "jumbo"
    elif masa >= 70:
        egg_label = "grande"
    elif masa < 70 y masa >= 55:
        egg_label = "medium"
    elif mass < 50:
        egg_label = "too light, 
 elif mass < 70 and mass > = 55: 
 egg_label = "medium" 
 elif mass < 50: 
 egg_label = "too light, probablemente estropeado"
    else :
        egg_label = "pequeño"
    return egg_label
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Análisis de datos encapsulando

Supongamos que el siguiente código ha sido ejecutado:

```python
import pandas as as pd

data_asia = pd.read_csv('data/gapminder_gdp_asia.csv', index_col=0)
japan = data_asia.loc['Japón']
```

1. Completa las siguientes proposiciones para obtener el PIB promedio de Japón
   a lo largo de los años reportados en la década de 1980.

```python
year = 1983
gdp_decade = 'gdpPercap_' + str(year // ____)
avg = (japan.loc[gdp_decade + ___] + japan.loc[gdp_decade + ___]) / 2
```

2. Resumen el código anterior en una sola función.

```python
def avg_gdp_in_decade(país, continente, año):
    data_countries = pd.read_csv('data/gapminder_gdp_'+___+'.csv',delimiter=',',index_col=0)
    ____
    ____
    ____
    return prog
```

3. ¿Cómo generalizarías esta función
   si no sabías de antemano qué años específicos ocurrieron como columnas en los datos?
   Por ejemplo, ¿qué pasa si también contáramos con datos de años que terminan en 1 y 9 por cada década?
   (Sugerencia: usa las columnas para filtrar las que corresponden a la década,
   en lugar de enumerarlas en el código.)

::::::::::::::::: solución

## Solución

1. El PIB promedio de Japón a lo largo de los años reportados para la década de 1980 se calcula con:

```python
year = 1983
gdp_decade = 'gdpPercap_' + str(year // 10)
avg = (japan.loc[gdp_decade + '2'] + japan.loc[gdp_decade + '7']) / 2
```

2. Ese código como función es:

```python
def avg_gdp_in_decade(país, continente, año):
    data_countries = pd.read_csv('data/gapminder_gdp_' + continente + '.csv', index_col=0)
    c = data_countries. oc[country]
    gdp_decade = 'gdpPercap_' + str(year // 10)
    avg = (c. oc[gdp_decade + '2'] + c.loc[gdp_decade + '7'])/2
    return prog
```

3. Para obtener la media de los años pertinentes, tenemos que hacer un bucle sobre ellos:

```python
def avg_gdp_in_decade(país, continente, año):
    data_countries = pd.read_csv('data/gapminder_gdp_' + continente + '. sv', index_col=0)
    c = datos_países. oc[country]
    gdp_decade = 'gdpPercap_' + str(year // 10)
    total = 0.
    num_years = 0
    para yr_header en c. ndex: # el índice de C contiene los años reportados
        si yr_header. tartswith(gdp_decade):
            total = total + c. oc[yr_header]
            num_years = num_years + 1
    retorno total/num_years
```

La función ahora puede ser llamada por:

```python
avg_gdp_in_decade('Japón','asia',1983)
```

```output
20880.023800000003
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Simular un sistema dinámico

En matemáticas, un [sistema dinámico](https://en.wikipedia.org/wiki/Dynamical_system) es un sistema
en el que una función describe la dependencia del tiempo de un punto en un espacio geométrico. Un ejemplo canónico
de un sistema dinámico es el [mapa logístico](https\://en.wikipedia. rg/wiki/Logistic_map),
un modelo de crecimiento que calcula una nueva densidad de población (entre 0 y 1) basada en la densidad
actual. En el modelo, el tiempo toma valores discretos 0, 1, 2, ...

1. Define una función llamada `logistic_map` que toma dos entradas: `x`, representando la población
   actual (en el tiempo `t`), y un parámetro `r = 1`. Esta función debe devolver un valor
   que representa el estado del sistema (población) en el momento `t + 1`, usando la función de mapeo:

`f(t+1) = r * f(t) * [1 - f(t)]`

2. Usando un bucle `for` o `while e`, iterar la función `logistic_map` definida en la parte 1, comenzando
   desde una población inicial de 0. , por un período de tiempo `t_final = 10`. Almacenar el intermedio
   resulta en una lista para que después de que el bucle termine, se haya acumulado una secuencia de valores
   que representa el estado del mapa logístico a veces `t = [0,1, . .,t_final]` (11 valores en total).
   Imprime esta lista para ver la evolución de la población.

3. Encapsular la lógica de tu bucle en una función llamada `iterate` que toma la población
   inicial como su primera entrada, el parámetro `t_final` como su segunda entrada y el parámetro
   `r` como su tercera entrada. La función debe devolver la lista de valores que representan el estado de
   el mapa logístico a veces `t = [0,1,...,t_final]`. Ejecuta esta función para los periodos `t_final = 100`
   y `1000` e imprime algunos de los valores. ¿La población está inclinándose hacia un estado estable?

::::::::::::::::: solución

## Solución

1. ```python
   ```

def logistic_map(x, r):
return r \* x \* (1 - x)

````

2. ```python
initial_population = 0.5
t_final = 10
r = 1.
población = [initial_population]
para t en rango(t_final):
    population.append( logistic_map(population[t], r)
````

3. ```python
   ```

def iterate(initial_population, t_final, r):
population = [initial_population]
for t in range(t_final):
population.append( logistic_map(population[t], r)
population return

para el período en (10, 100, 1000):
población = iterate(0.5, periodo, 1)
impresión (población[-1])

````

```output
0.06945089389714401
0.009395779870614648
0.0009913908614406382
````

Parece que la población se acerca a cero.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## Uso de funciones con condicionales en Pandas

Las funciones suelen contener condicionales.  Aquí hay un pequeño ejemplo de que
indicará en qué cuadriculo está el argumento basado en los valores codificados a mano
para los puntos de corte cuartil.

```python
def calculate_life_quartile(exp):
    si exp < 58. 1:
        # Esta observación está en el primer cuartil
        return 1
    elif exp >= 58. 1 y exp < 67. 5:
        # Esta observación está en el segundo cuartil
       return 2
    elif exp >= 67. 5 y exp < 71. 0:
        # Esta observación está en el tercer cuartil
       return 3
    elif exp >= 71. 0:
        # Esta observación está en el cuarto cuartil
       return 4
    else:
        # Esta observación tiene datos incorrectos
       return None

calculate_life_quartile(62.5)
```

```output
2
```

Esa función normalmente se usaría dentro de un bucle `for`, pero Pandas tiene
una función diferente, una forma más eficiente de hacer lo mismo, y eso es por
_aplicando_ una función a un nombre de dato o una porción de un nombre de datos.  Aquí
es un ejemplo, utilizando la definición anterior.

```python
data = pd.read_csv('data/gapminder_all.csv')
data['life_qrtl'] = data['lifeExp_1952'].apply(calculate_life_quartile)
```

Hay mucho en esa segunda línea, así que tomémosla por pedazo.
En el lado derecho del `=` empezamos con `data['lifeExp']`, que es la columna
en el nombre de datos llamado `data` etiquetado como `lifExp`.  Utilizamos el
`apply()` para hacer lo que dice, aplicar el `calculate_life_quartile` al valor
de esta columna para cada fila en el nombre de la fecha.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Descomprima los programas en funciones para hacerlos más fáciles de entender.
- Definir una función usando `def` con un nombre, parámetros y un bloque de código.
- Definir una función no la ejecuta.
- Los argumentos en una llamada a función se corresponden con sus parámetros definidos.
- Las funciones pueden devolver un resultado a su persona que llama usando `return`.

::::::::::::::::::::::::::::::::::::::::::::::::::
