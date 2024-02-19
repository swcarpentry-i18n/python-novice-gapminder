---
title: Pandas DataFrames
teaching: 15
exercises: 15
---

::::::::::::::::::::::::::::::::::::::: objectives

- Seleccione valores individuales de un nombre de datos de Pandas.
- Seleccione filas enteras o columnas enteras desde un nombre de datos.
- Seleccione un subconjunto de filas y columnas de un nombre de fecha en una sola operación.
- Seleccione un subconjunto de un nombre de fecha según un único criterio booleano.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::::: preguntas

- ¿Cómo puedo hacer un análisis estadístico de los datos tabulares?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Nota sobre Pandas DataFrames/Series

Una [DataFrame][pandas-dataframe] es una colección de [Series][pandas-series];
El DataFrame es la forma en que Pandas representa una tabla, y la Serie es la estructura de datos
Pandas utilizan para representar una columna.

Pandas se construye sobre la biblioteca [Numpy][numpy] , lo que en la práctica significa que
la mayoría de los métodos definidos para Numpy Arrays se aplican a Pandas Series/DataFrames.

Lo que hace a Pandas tan atractivo es la poderosa interfaz para acceder a los registros individuales
de la tabla. manejo adecuado de los valores faltantes, y operaciones de bases de datos de relaciones
entre DataFrames.

## Seleccionando valores

Para acceder a un valor en la posición `[i,j]` de un DataFrame, tenemos dos opciones, dependiendo de
cuál es el significado de `i` en uso.
Recuerde que un DataFrame proporciona un _índice_ como una forma de identificar las filas de la tabla;
una fila, entonces, tiene una _posición_ dentro de la tabla así como una _etiqueta_, la cual
identifica su _entrada_ en el DataFrame.

## Usa `DataFrame.iloc[..., ...]` para seleccionar valores por su posición (entrada)

- Puede especificar la ubicación por índice numérico de forma analógica a la versión 2D de la selección de caracteres en cadenas.

```python
import pandas as as pd
data = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')
print(data.iloc[0, 0])
```

```output
1601.056136
```

## Usa `DataFrame.loc[..., ...]` para seleccionar valores por su etiqueta (entrada).

- Puede especificar la ubicación por fila y/o nombre de columna.

```python
print(data.loc["Albania", "gdpPercap_1952"])
```

```output
1601.056136
```

## Usa `:` por sí solo para significar todas las columnas o todas las filas.

- Al igual que la notación de corte habitual de Python.

```python
print(data.loc["Albania", :])
```

```output
gdpPercap_1952 1601.056136
gdpPercap_1957 1942.284244
gdpPercap_1962 2312.888958
gdpPercap_1967 2760. 96931
gdpPercap_1972 3313.422188
gdpPercap_1977 3533.003910
gdpPercap_1982 3630. 80722
gdpPercap_1987 3738.932735
gdpPercap_1992 2497.437901
gdpPercap_1997 3193. 54604
gdpPercap_2002 4604.211737
gdpPercap_2007 5937.029526
Nombre: Albania, dtype: float64
```

- Obtendría el mismo resultado imprimiendo `data.loc["Albania"]` (sin un segundo índice).

```python
print(data.loc[:, "gdpPercap_1952"])
```

```output
país
Albania 1601. 56136
Austria 6137. 76492
Bélgica 8343. 05127
Rápidamente
Suiza 14734. 32750
Pavo 1969. 00980
Reino Unido 9979. 08487
Nombre: gdpPercap_1952, dtype: float64
```

- Obtendría el mismo resultado imprimiendo `data["gdpPercap_1952"]`
- También obtén el mismo resultado imprimiendo `data.gdpPercap_1952` (no recomendado, porque fácilmente se confunde con `.` notación para métodos)

## Seleccione varias columnas o filas usando `DataFrame.loc` y una capa nombrada.

```python
print(data.loc['Italia':'Polonia', 'gdpPercap_1962':'gdpPercap_1972'])
```

```output
             gdpPercap_1962 gdpPercap_1967 gdpPercap_1972
country
Italia 8243. 82340 10022.401310 12269.273780
Montenegro 4649. 93785 5907.850937 7778. 14017
Países Bajos 12790.849560 15363. 51360 18794.745670
Noruega 13450. 01510 16361.876470 18965.055510
Polonia 5338. 52143 6557.152776 8006.506993
```

In the above code, we discover that **slicing using `loc` is inclusive at both
ends**, which differs from **slicing using `iloc`**, where slicing indicates
everything up to but not including the final index.

## El resultado del corte se puede utilizar en otras operaciones.

- Por lo general, no se limite a imprimir una corte.
- Todos los operadores estadísticos que trabajan en los nombres
  de datos completos funcionan de la misma manera en rodajas.
- Por ejemplo, calcular el máximo de una corte.

```python
print(data.loc['Italia':'Polonia', 'gdpPercap_1962':'gdpPercap_1972'].max())
```

```output
gdpPercap_1962 13450.40151
gdpPercap_1967 16361.87647
gdpPercap_1972 18965.05551
dtype: float64
```

```python
print(data.loc['Italia':'Polonia', 'gdpPercap_1962':'gdpPercap_1972'].min())
```

```output
gdpPercap_1962 4649.593785
gdpPercap_1967 5907.850937
gdpPercap_1972 7778.414017
dtype: float64
```

## Utilice las comparaciones para seleccionar datos basados en el valor.

- La comparación se aplica elemento por elemento.
- Devuelve un nombre de dato similar de `True` y `False`.

```python
# Utilice un subconjunto de datos para mantener la salida legible.
subconjunto = datos. oc['Italy':'Poland', 'gdpPercap_1962':'gdpPercap_1972']
print('Subconjunto de datos:\n', subset)

# ¿Qué valores eran mayores que 10000 ?
print('\n¿Dónde están los valores grandes?\n', subconjunto > 10000)
```

```output
Subconjunto de datos:
             gdpPercap_1962 gdpPercap_1967 gdpPercap_1972
country
Italia 8243. 82340 10022.401310 12269.273780
Montenegro 4649.593785 5907. 50937 7778.414017
Países Bajos 12790.849560 15363. 51360 18794.745670
Noruega 13450. 01510 16361.876470 18965.055510
Polonia 5338. 52143 6557.152776 8006. 06993

¿Dónde están los valores grandes?
            gdpPercap_1962 gdpPercap_1967 gdpPercap_1972
country
Italy False True True
Montenegro False False False
Netherlands True True True
Norway True True True
Poland False False False
```

## Seleccione valores o NaN usando una máscara booleana.

- Un marco lleno de booleanos a veces se llama _máscara_ debido a cómo se puede usar.

```python
máscara = subconjunto > 10000
impresión (subconjunto[mask])
```

```output
             gdpPercap_1962 gdpPercap_1967 gdpPercap_1972
country
Italy NaN 10022. 0131 12269. 7378
Montenegro NaN NaN
Países Bajos 12790. 4956 15363.25136 18794. 4567
Noruega 13450.40151 16361. 7647 18965. 5551
Polonia NaN NaN NaN
```

- Obtener el valor donde la máscara es verdadera, y NaN (Not a Number) donde es falso.
- Útil porque NaNs es ignorado por operaciones como máximo, min, promedio, etc.

```python
print(subset[subconjunto > 10000].describe())
```

```output
       gdpPercap_1962 gdpPercap_1967 gdpPercap_1972
cuenta 2. 00000 3.000000 3.000000
significa 13120. 25535 13915.843047 16676.358320
std 466.373656 3408. 89070 3817.597015
min 12790.849560 10022. 01310 12269.273780
25% 12955.737547 12692.826335 15532. 09725
50% 13120.625535 15363.251360 18794. 45670
75% 13285.513523 15862.563915 18879. 00590
máx. 13450.401510 16361.876470 18965.055510
```

## Grupo por: combinación de aplicación dividida

::::::::::::::::::::::::::::::::::::::: instructor
Los estudiantes suelen luchar aquí, muchos pueden no trabajar con los datos financieros y los conceptos por lo que
encuentran los conceptos de ejemplo difícil de tener la cabeza. El mayor problema
aunque es la línea que genera wealth_score, este paso necesita ser hablado a través de
a través de:

- Utiliza una conversión implícita entre valores booleanos y decimales que
  no ha cubierto en el curso hasta ahora.
- El argumento axis=1 debe explicarse claramente.
  :::::::::::::::::::::::::::::::::::::::::::::::::

Los métodos vectorizadores de Pandas y las operaciones de agrupación son características que proporcionan a los usuarios
mucha flexibilidad para analizar sus datos.

Por ejemplo, digamos que queremos tener una visión más clara sobre cómo se dividieron los países europeos
en función de su PIB.

1. Podemos echar un vistazo dividiendo los países en dos grupos durante los años encuestados,
   a aquellos que presentaron un PIB _mayor_ que el promedio europeo y a aquellos con un PIB _menor_.
2. We then estimate a _wealthy score_ based on the historical (from 1962 to 2007) values,
   where we account how many times a country has participated in the groups of _lower_ or _higher_ GDP

```python
máscara_superior = datos > data.mean()
wealth_score = mask_higher.aggregate('suma', axis=1) / len(data.columnas)
print(wealth_score)
```

```output
país
Albania 0. 00000
Austria 1. 00000
Bélgica 1. 00000
Bosnia y Herzegovina 0. 00000
Bulgaria 0. 00000
Croacia 0. 00000
República Checa 0. 00000
Dinamarca 1. 00000
Finlandia 1. 00000
Francia 1. 00000
Alemania 1. 00000
Grecia 0. 3333
Hungría 0. 00000
Celand 1. 00000
Irlanda 0. 3333
Italia 0. 00000
Montenegro 0. 00000
Países Bajos 1. 00000
Noruega 1. 00000
Polonia 0. 00000
Portugal 0. 00000
Rumanía 0. 00000
Serbia 0. 00000
República Eslovaca 0. 00000
eslovenos 0. 33333
España 0. 3333
Suecia 1. 00000
Suiza 1. 00000
Turquía 0. 00000
Reino Unido 1.000000
dtype: float64
```

Finalmente, para cada grupo en la tabla `wealth_score`, sumamos su contribución (financiera)
a través de los años encuestados utilizando métodos encadenados:

```python
print(data.groupby(puntos de wealth).sum())
```

```output
          gdpPercap_1952 gdpPercap_1957 gdpPercap_1962 gdpPercap_1967 \
0. 00000 36916.854200 46110.918793 56850.065437 71324. 48786   
.33333 16790.046878 20942.456800 25744.935321 33567. 67670   
0.500000 11807.544405 14505.000150 18380.449470 21421. 46200   
1.000000 104317.277560 12732.008735 149989.154201 178000. 50040   

          gdpPercap_1972 gdpPercap_1977 gdpPercap_1982 gdpPercap_1987 \
0. 00000 88569.346898 104459.358438 113553.768507 119649. 99409   
0.33333 45277.839976 53860. 56750 59679.634020 64436.912960   
0.500000 25377.727380 29056. 45370 31914.712050 35517.678220   
1.000000 215162.343140 241143. 12730 263388.781960 296825. 31210   

          gdpPercap_1992 gdpPercap_1997 gdpPercap_2002 gdpPercap_2007 
 0. 00000 92380. 47256 103772.937598 118590.929863 149577.357928  
0.33333 67918. 93220 80876.051580 102086.795210 122803.729520  
0. 00000 36310.666080 40723.538700 45564.308390 51403.028210  
1. 00000 315238.235970 346930.926170 385109.939210 427850.333420
```

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Selección de valores individuales

Supongamos que Pandas ha sido importado en tu cuaderno
y los datos del PIB de Gapminder para Europa se han cargado:

```python
import pandas as as pd

data_europe = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')
```

Escribe una expresión para encontrar el PIB de Per Capita de Serbia en 2007.

::::::::::::::::: solución

## Solución

La selección se puede hacer usando las etiquetas tanto para la fila ("Serbia") como para la columna ("gdpPercap_2007"):

```python
print(data_europe.loc['Serbia', 'gdpPercap_2007'])
```

La salida es

```output
9786.534714
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Extención de corte

1. ¿Las dos declaraciones siguientes producen la misma salida?
2. En base a esto,
   ¿qué regla rige lo que se incluye (o no) en rebanadas numéricas y rebanadas nombradas en Pandas?

```python
print(data_europe.iloc[0:2, 0:2])
print(data_europe.loc['Albania':'Bélgica', 'gdpPercap_1952':'gdpPercap_1962'])
```

::::::::::::::::: solución

## Solución

¡No, no producen la misma producción! La salida de la primera sentencia es:

```output
        gdpPercap_1952 gdpPercap_1957
country                                
Albania 1601.056136 1942.284244
Austria 6137.076492 8842.598030
```

La segunda declaración ofrece:

```output
        gdpPercap_1952 gdpPercap_1957 gdpPercap_1962
country                                                
Albania 1601.056136 1942.284244 2312.888958
Austria 6137.076492 8842.598030 10750.721110
Bélgica 8343.105127 9714.960623 10991.206760
```

Claramente, el segundo comando produce una columna adicional y un registro adicional en comparación con el primer comando.\
¿Qué conclusión podemos extraer? Vemos que una rebanada numérica, 0:2, _omite_ el índice final (i.e. index 2)
en el rango proporcionado,
mientras un slice, 'gdpPercap_1952':'gdpPercap_1962', _incluye_ el elemento final.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Reconstruyendo datos

Explicar lo que hace cada línea en el siguiente programa corto:
¿qué es en `primero`, `segundo`, etc.?

```python
first = pd.read_csv('data/gapminder_all.csv', index_col='country')
segundo = primero['continent'] == 'Américas']
tercero = second.drop('Puerto Rico')
cuarto = third.drop('continent', eje = 1)
cuarto_csv('result.csv')
```

::::::::::::::::: solución

## Solución

Vamos a pasar por esta pieza de código línea por línea.

```python
primero = pd.read_csv('data/gapminder_all.csv', índice_col='país')
```

Esta línea carga el conjunto de datos que contiene los datos del PIB de todos los países en un nombre de fecha llamado
`primero`. El parámetro `index_col='country'` selecciona qué columna usar como la fila
en el nombre de la fecha.

```python
second = primero['continente'] == 'Américas']
```

Esta línea hace una selección: solo aquellas filas de 'primero' para las que la columna 'continente' coincide con
'Américas' son extraídas. Observa cómo la expresión booleana dentro de los paréntesis,
`primero['continent'] == 'Américas'`, se utiliza para seleccionar solo aquellas filas donde la expresión es verdadera.
¡Intenta imprimir esta expresión! ¿Puedes imprimir también sus elementos individuales True/False?
(pista: primero asignar la expresión a una variable)

```python
tercero = second.drop('Puerto Rico')
```

Como sugiere la sintaxis, esta línea deja caer la fila de 'segundo', donde la etiqueta es 'Puerto Rico'. The
resulting dataframe `third` has one row less than the original dataframe `second`.

```python
cuarto = third.drop('continente', eje = 1)
```

De nuevo aplicamos la función de soltar, pero en este caso no estamos soltando una fila, sino toda una columna.
Para lograr esto, necesitamos especificar también el parámetro `axis` (queremos eliminar la segunda columna
que tiene índice 1).

```python
cuarto_csv('resultado.csv')
```

El paso final es escribir los datos en los que hemos estado trabajando en un archivo csv. Pandas hace esto fácil
con la función `to_csv()`. El único argumento requerido para la función es el nombre del archivo. Ten en cuenta que el archivo
se escribirá en el directorio desde el que iniciaste la sesión de Jupyter o Python.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Seleccionando índices

Explica en términos sencillos lo que `idxmin` y `idxmax` hacen en el programa corto a continuación.
¿Cuándo usaría estos métodos?

```python
data = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')
print(data.idxmin())
print(data.idxmax())
```

::::::::::::::::: solución

## Solución

Para cada columna en `data`, `idxmin` devolverá el valor de índice correspondiente al mínimo de cada columna;
`idxmax` hará lo mismo para el valor máximo de cada columna.

Puede utilizar estas funciones siempre que desee obtener el índice de registro del valor mínimo/máximo y no el valor mínimo / máximo real.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Práctica con selección

Supongamos que se ha importado Pandas y que se han cargado los datos del PIB de Gapminder para Europa.
Escribe una expresión para seleccionar cada una de las siguientes:

1. El PIB per cápita para todos los países en 1982.
2. El PIB per cápita de Dinamarca durante todos los años.
3. PIB per cápita para todos los países \*después de 1985.
4. El PIB per cápita de cada país en 2007 como múltiplo de
   PIB per cápita de ese país en 1952.

::::::::::::::::: solución

## Solución

1:

```python
data['gdpPercap_1982']
```

2:

```python
data.loc['Dinamarca',:]
```

3:

```python
data.loc[:,'gdpPercap_1985':]
```

Pandas es lo suficientemente inteligente como para reconocer el número al final de la etiqueta de columna y no le da un error, aunque no existe ninguna columna llamada `gdpPercap_1985` en realidad. Esto es útil si se añaden nuevas columnas al archivo CSV más adelante.

4:

```python
data['gdpPercap_2007']/data['gdpPercap_1952']
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Muchas formas de acceso

Hay al menos dos formas de acceder a un valor o rebanada de un DataFrame: por nombre o índice.
Sin embargo, hay muchos otros. Por ejemplo, se puede acceder a una sola columna o fila ya sea como un objeto `DataFrame`
o un objeto `Series`.

Sugerir diferentes maneras de hacer las siguientes operaciones en un DataFrame:

1. Acceder a una sola columna
2. Acceder a una sola fila
3. Acceder a un elemento DataFrame individual
4. Acceder a varias columnas
5. Acceder a varias filas
6. Acceder a un subconjunto de columnas y filas específicas
7. Acceder a un subconjunto de rangos de fila y columna

::::::::::::::::: solución

## Solución

1\. Acceder a una sola columna:

```python
# by name
data["col_name"] # as a Series
data[["col_name"]] # as a DataFrame

# by name using .loc
. .loc["col_name"] # as a Series
data.T.loc[["col_name"]].T # as a DataFrame

# Dot notation (Series)
data. ol_name

# por índice (iloc)
data.iloc[:, col_index] # como datos de la Serie
. loc[:, [col_index]] # como un DataFrame

# usando una máscara
data.T[data.T.index == "col_name"].T
```

2\. Acceder a una sola fila:

```python
# por nombre usando .loc
data.loc["row_name"] # como datos de la Serie
. oc[["row_name"]] # as a DataFrame

# by name
data.T["row_name"] # as a Series
data.T[["row_name"]]. # as a DataFrame

# by index
data.iloc[row_index]   # as a Series
data. loc[[row_index]] # como un DataFrame

# usando máscara
data[data.index == "row_name"]
```

3\. Acceder a un elemento DataFrame individual:

```python
# by column/row names
data["column_name"]["row_name"]         # as a Series

data[["col_name"]].loc["row_name"]  # as a Series
data[["col_name"]].loc[["row_name"]]  # as a DataFrame

data.loc["row_name"]["col_name"]  # as a value
data.loc[["row_name"]]["col_name"]  # as a Series
data.loc[["row_name"]][["col_name"]]  # as a DataFrame

data.loc["row_name", "col_name"]  # as a value
data.loc[["row_name"], "col_name"]  # as a Series. Preserves index. Column name is moved to `.name`.
data.loc["row_name", ["col_name"]]  # as a Series. Index is moved to `.name.` Sets index to column name.
data.loc[["row_name"], ["col_name"]]  # as a DataFrame (preserves original index and column name)

# by column/row names: Dot notation
data.col_name.row_name

# by column/row indices
data.iloc[row_index, col_index] # as a value
data.iloc[[row_index], col_index] # as a Series. Preserves index. Column name is moved to `.name`
data.iloc[row_index, [col_index]] # as a Series. Index is moved to `.name.` Sets index to column name.
data.iloc[[row_index], [col_index]] # as a DataFrame (preserves original index and column name)

# column name + row index
data["col_name"][row_index]
data.col_name[row_index]
data["col_name"].iloc[row_index]

# column index + row name
data.iloc[:, [col_index]].loc["row_name"]  # as a Series
data.iloc[:, [col_index]].loc[["row_name"]]  # as a DataFrame

# using masks
data[data.index == "row_name"].T[data.T.index == "col_name"].T
```

4\. Acceder a varias columnas:

```python
# por nombre
data[["col1", "col2", "col3"]]
data.loc[:, ["col1", "col2", "col3"]]

# por índice
data.iloc[:, [col1_index, col2_index, col3_index]]
```

5\. Acceder a varias filas

```python
# by name
data.loc[["row1", "row2", "row3"]]

# by index
data.iloc[[row1_index, row2_index, row3_index]]
```

6\. Acceder a un subconjunto de columnas y filas específicas

```python
# por nombres
data.loc[["row1", "row2", "row3"], ["col1", "col2", "col3"]]

# por índices
datos. loc[[row1_index, row2_index, row3_index], [col1_index, col2_index, col3_index]]

# nombres de columna + índices de fila
data[["col1", "col2", "col3"]]. loc[[row1_index, row2_index, row3_index]]

# columnas indices + nombres de filas
data.iloc[:, [col1_index, col2_index, col3_index]].loc[["row1", "row2", "row3"]]
```

7\. Acceder a un subconjunto de rangos de fila y columna

```python
# por nombre
data.loc["row1":"row2", "col1":"col2"]

# por índice
data.iloc[row1_index:row2_index, col1_index:col2_index]

# nombres de columna + índices de fila
datos. oc[:, "col1_name":"col2_name"].iloc[row1_index:row2_index]

# columnas indices + nombres de fila
data.iloc[:, col1_index:col2_index].loc["row1":"row2"]
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Explorando métodos disponibles usando la función `dir()`

Python incluye una función `dir()` que puede ser usada para mostrar todos los métodos disponibles (funciones) que están incorporados en un objeto de datos.  En Episodio 4, usamos algunos métodos con una cadena. Pero podemos ver muchos más están disponibles usando `dir()`:

```python
my_string = '¡Hola mundo!' # creación de un objeto de cadena 
dir(my_string)
```

Este comando devuelve:

```python
['__add__',
...
'__subclasshook__',
'capitalize',
'casefold',
'center',
...
'upper',
'zfill']
```

Puedes usar `help()` o <kbd>Shift</kbd>+<kbd>Tabla</kbd> para obtener más información sobre lo que hacen estos métodos.

Supongamos que Pandas ha sido importado y los datos del PIB de Gapminder para Europa se han cargado como `datos`.  Luego, usa `dir()`
para encontrar la función que imprime el PIB medio per cápita en todos los países europeos para cada año que la información esté disponible.

::::::::::::::::: solución

## Solución

Entre muchas opciones, `dir()` lista la función `median()` como una posibilidad.  Por lo tanto,

```python
data.median()
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Interpretación

Las fronteras de Polonia han sido estables desde 1945,
pero cambiaron varias veces en los años anteriores.
¿Cómo manejaríamos esto si creáramos una tabla de PIB per cápita para Polonia
durante todo el siglo XX?

::::::::::::::::::::::::::::::::::::::::::::::::::

[pandas-dataframe]: https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.html

[pandas-series]: https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.html

[numpy]: https://www.numpy.org/

:::::::::::::::::::::::::::::::::::::::: keypoints

- Use `DataFrame.iloc[..., ...]` para seleccionar valores por ubicación entera.
- Usa `:` por sí solo para significar todas las columnas o todas las filas.
- Seleccione varias columnas o filas usando `DataFrame.loc` y una capa nombrada.
- El resultado del corte se puede utilizar en otras operaciones.
- Utilice las comparaciones para seleccionar datos basados en el valor.
- Seleccione valores o NaN usando una máscara booleana.

::::::::::::::::::::::::::::::::::::::::::::::::::
