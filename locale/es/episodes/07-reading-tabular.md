---
title: Leyendo datos tabulares en DataFrames
teaching: 10
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- Importa la biblioteca de Pandas.
- Utilice Pandas para cargar un simple conjunto de datos CSV.
- Obtener información básica sobre un DataFrame de Pandas.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::::: preguntas

- ¿Cómo puedo leer los datos de la tabla?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Utilice la biblioteca de Pandas para hacer estadísticas sobre datos tabulares.

- [Pandas](https://pandas.pydata.org/) es una biblioteca Python ampliamente utilizada para estadísticas, particularmente en datos tabulares.
- Presenta muchas características de R's datuames.
  - Una tabla 2-dimensional cuyas columnas tienen nombres
    y potencialmente tienen diferentes tipos de datos.
- Carga Pandas con `importar pandas como pd`. El alias `pd` se usa comúnmente para referirse a la biblioteca de Pandas en código.
- Lea un archivo de datos de Valores Separados por Comas (Vales Separados) con `pd.read_csv`.
  - Argumento es el nombre del archivo a leer.
  - Devuelve un nombre de dato que puede asignar a una variable

```python
import pandas as as pd

data_oceania = pd.read_csv('data/gapminder_gdp_oceania.csv')
print(data_oceania)
```

```output
       country gdpPercap_1952 gdpPercap_1957 gdpPercap_1962 \
0 Australia 10039. 9564 10949.64959 12217. 2686
1 Nueva Zelanda 10556.57566 12247. 9532 13175. 7800

   gdpPercap_1967 gdpPercap_1972 gdpPercap_1977 gdpPercap_1982 \
0 14526. 2465 16788.62948 18334.19751 19477.00928
1 14463. 1893 16046.03728 16233.71770 17632. 1040

   gdpPercap_1987 gdpPercap_1992 gdpPercap_1997 gdpPercap_2002 \
0 21888. 8903 23424.76683 26997. 3657 30687.75473
1 19007. 9129 18363.32494 21050.41377 23189. 0135

   gdpPercap_2007
0 34435.36744
1 25185.00911
```

- Las columnas en un nombre de fecha son las variables observadas y las filas son las observaciones.
- Pandas utiliza barra inversa `\` para mostrar líneas envueltas cuando la salida es demasiado amplia para caber en la pantalla.
- El uso de nombres de nombres de datos descriptivos nos ayuda a distinguir entre múltiples nombres de datos, por lo que no sobrescribiremos accidentalmente un nombre de dato o leer del incorrecto.

:::::::::::::::::::::::::::::::::::::::::  callout

## Archivo no encontrado

Nuestras lecciones almacenan sus archivos de datos en un subdirectorio de `data`,
, por lo que la ruta al archivo es `data/gapminder_gdp_oceania.csv`.
If you forget to include `data/`,
or if you include it but your copy of the file is somewhere else,
you will get a [runtime error](04-built-in.md)
that ends with a line like this:

```error
FileNotFoundError: [Error 2] No existe tal archivo o directorio: 'data/gapminder_gdp_oceania.csv'
```

::::::::::::::::::::::::::::::::::::::::::::::::::

## Usa `index_col` para especificar que los valores de una columna deben ser usados como cabeceras de fila.

- Los encabezados de las filas son números (0 y 1 en este caso).
- Realmente quiere indexar por país.
- Pasa el nombre de la columna a `read_csv` como su parámetro `index_col` para hacer esto.
- Nombrando la fecha `data_oceania_country` nos dice qué región incluye los datos (`oceania`) y cómo se indexa (`country`).

```python
data_oceania_country = pd.read_csv('data/gapminder_gdp_oceania.csv', index_col='país')
print(data_oceania_country)
```

```output
             gdpPercap_1952 gdpPercap_1957 gdpPercap_1962 gdpPercap_1967 \
country
Australia 10039. 9564 10949.64959 12217.22686 14526.12465
Nueva Zelanda 10556. 7566 12247.39532 13175.67800 14463. 1893

             gdpPercap_1972 gdpPercap_1977 gdpPercap_1982 gdpPercap_1987 \
country
Australia 16788. 2948 18334.19751 19477.00928 21888.88903
Nueva Zelanda 16046. 3728 16233.71770 17632.41040 19007. 9129

             gdpPercap_1992 gdpPercap_1997 gdpPercap_2002 gdpPercap_2007
country
Australia 23424. 6683 26997.93657 30687.75473 34435.36744
Nueva Zelanda 18363. 2494 21050.41377 23189.80135 25185.00911
```

## Utilice el método `DataFrame.info()` para averiguar más acerca de un nombre de datos.

```python
data_oceania_país.info()
```

```output
<class 'pandas.core.frame.DataFrame'>
Index: 2 entries, Australia to New Zealand
Data columns (total 12 columns):
gdpPercap_1952    2 non-null float64
gdpPercap_1957    2 non-null float64
gdpPercap_1962    2 non-null float64
gdpPercap_1967    2 non-null float64
gdpPercap_1972    2 non-null float64
gdpPercap_1977    2 non-null float64
gdpPercap_1982    2 non-null float64
gdpPercap_1987    2 non-null float64
gdpPercap_1992    2 non-null float64
gdpPercap_1997    2 non-null float64
gdpPercap_2002    2 non-null float64
gdpPercap_2007    2 non-null float64
dtypes: float64(12)
memory usage: 208.0+ bytes
```

- Esto es un `DataFrame`
- Dos filas nombradas `'/etcalia'` y `'Nueva Zeland'`
- Doce columnas, cada una de las cuales tiene dos valores flotantes reales de 64 bits.
  - Más tarde hablaremos de valores nulos, que se utilizan para representar observaciones que faltan.
- Utiliza 208 bytes de memoria.

## La variable `DataFrame.columns` almacena información sobre las columnas del marco de datos.

- Tenga en cuenta que esto son datos, _no_ un método.  (No tiene paréntesis.)
  - Como `math.pi`.
  - Así que no use `()` para intentar llamarlo.
- Llamada a una _variable de miembro_, o sólo a _miembro_.

```python
print(data_oceania_país.columnas)
```

```output
Index(['gdpPercap_1952', 'gdpPercap_1957', 'gdpPercap_1962', 'gdpPercap_1967',
       'gdpPercap_1972', 'gdpPercap_1977', 'gdpPercap_1982', 'gdpPercap_1987',
       'gdpPercap_1992', 'gdpPercap_1997', 'gdpPercap_2002', 'gdpPercap_2002', 'gdpPercap_2007'],
      dtype='object')
```

## Usa `DataFrame.T` para transponer un nombre de datos.

- A veces quieren tratar las columnas como filas y viceversa.
- Transpose (escrito `.T`) no copia los datos, sólo cambia la vista del programa.
- Como `columns`, es una variable miembro.

```python
impres(data_oceania_país.T)
```

```output
country Australia New Zealand
gdpPercap_1952 10039.59564 10556. 7566
gdpPercap_1957 10949.64959 12247.39532
gdpPercap_1962 12217. 2686 13175.67800
gdpPercap_1967 14526.12465 14463.91893
gdpPercap_1972 16788.62948 16046.03728
gdpPercap_1977 183334. 9751 16233.71770
gdpPercap_1982 19477.00928 17632.41040
gdpPercap_1987 21888.88903 19007.19129
gdpPercap_1992 23424.76683 18363. 2494
gdpPercap_1997 26997.93657 21050.41377
gdpPercap_2002 30687.75473 23189.80135
gdpPercap_2007 34435.36744 25185.00911
```

## Usa `DataFrame.describe()` para obtener estadísticas resumidas sobre datos.

`DataFrame.describe()` obtiene las estadísticas resumidas de sólo las columnas que tienen datos numéricos.
Todas las demás columnas son ignoradas, a menos que utilice el argumento `include='all'`.

```python
print(data_oceania_country.describe())
```

```output
       gdpPercap_1952 gdpPercap_1957 gdpPercap_1962 gdpPercap_1967 \
cuenta 2. 00000 2.000000 2. 00000 2.000000
significa 10298.085650 11598.522455 12696. 52430 14495.021790
std 365.560078 917. 44806 677.727301 43. 86086
min 10039.595640 10949. 49590 12217.226860 14463.918930
25% 10168. 40645 11274.086022 12456.839645 14479.470360
50% 10298. 85650 11598.522455 12696.452430 14495. 21790
75% 10427.330655 11922.958888 12936.065215 14510. 73220
máx. 10556.575660 12247.395320 13175. 78000 14526. 24650

       gdpPercap_1972 gdpPercap_1977 gdpPercap_1982 gdpPercap_1987 \
cuenta 2. 0000 2.000000 2.000000 2. 00000
significa 16417. 3338 17283.957605 18554.709840 20448. 40160
std 525.09198 1485.263517 1304. 28377 2037.668013
min 16046.03728 16233. 17700 17632.410400 19007.191290
25% 16231.68533 16758. 37652 18093.560120 19727.615725
50% 16417. 3338 17283.957605 18554.709840 20448.040160
75% 16602. 8143 17809.077557 19015.859560 21168. 64595
max 16788.62948 18334.197510 19477.009280 21888. 89030

       gdpPercap_1992 gdpPercap_1997 gdpPercap_2002 gdpPercap_2007
count 2. 00000 2.000000 2.0000 2. 00000
significa 20894. 45885 24024.175170 26938.778040 29810.188275
std 3578. 79883 4205.533703 5301.853680 6540. 91104
min 18363.324940 21050.413770 23189.801350 25185. 09110
25% 19628.685413 22537.294470 25064. 89695 27497.598692
50% 20894.045885 24024. 75170 26938.778040 29810.188275
75% 22159. 06358 25511.055870 28813.266385 32122.777857
max 23424. 66830 26997.936570 30687.754730 34435.367440
```

- No particularmente útil con solo dos registros,
  pero muy útil cuando hay miles.

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Leyendo otros datos

Lee los datos en `gapminder_gdp_americas.csv`
(que debería estar en el mismo directorio que `gapminder_gdp_oceania. sv`)
en una variable llamada `data_americas`
y muestra sus estadísticas resumidas.

::::::::::::::::: solución

## Solución

Para leer en un CSV, usamos `pd.read_csv` y pasamos el nombre del archivo `'data/gapminder_gdp_americas.csv'` a él.
También pasamos el nombre de la columna `'country'` al parámetro `index_col` para indexar por país.
Las estadísticas de resumen se pueden mostrar con el método `DataFrame.describe()`.

```python
data_Technicas = pd.read_csv('data/gapminder_gdp_americas.csv', index_col='country')
data_americas.describe()
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Inspección de datos

Después de leer los datos para las Américas,
use `help(data_americas.head)` y `help(data_americas.tail)`
para averiguar lo que hacen `DataFrame.head` y `DataFrame.tail`.

1. ¿Qué método de llamada mostrará las tres primeras filas de estos datos?
2. ¿Qué método de llamada mostrará las tres últimas columnas de estos datos?
   (Sugerencia: puede que tengas que cambiar la vista de los datos.)

::::::::::::::::: solución

## Solución

1. Podemos revisar las primeras cinco filas de `data_americas` ejecutando `data_americas.head()`
   que nos permite ver el comienzo del DataFrame. Podemos especificar el número de filas que deseamos
   para ver especificando el parámetro `n` en nuestra llamada a `data_americas.head()`.
   Para ver las tres primeras filas, ejecuta:

```python
datos_americas.head(n=3)
```

```output
          Continente gdpPercap_1952 gdpPercap_1957 gdpPercap_1962 \
country
Argentina Americas 5911. 15053 6856. 56212 7133.166023
Bolivia América 2677.326347 2127. 86326 2180.972546
Brasil América 2108.944355 2487. 65989 3336. 85802

          gdpPercap_1967 gdpPercap_1972 gdpPercap_1977 gdpPercap_1982 \
country
Argentina 8052. 53021 9443.038526 10079.026740 8997.897412
Bolivia 2586. 86053 2980.331339 3548.097832 3156. 10452
Brasil 3429. 64357 4985.711467 6660.118654 7030. 35878

           gdpPercap_1987 gdpPercap_1992 gdpPercap_1997 gdpPercap_2002 \
country
Argentina 9139. 71389 9308.418710 10967.281950 8797.640716
Bolivia 2753. 91490 2961.699694 3326.143191 3413. 62690
Brasil 7807. 95818 6950.283021 7957.980824 8131. 12843

           gdpPercap_2007
country
Argentina 12779. 79640
Bolivia 3822.137084
Brasil 9065.800825
```

2. Para ver las últimas tres filas de `data_americas`, usaríamos el comando,
   `americas.tail(n=3)`, analogoso a `head()` usado arriba. Sin embargo, aquí queremos mirar
   las últimas tres columnas, así que necesitamos cambiar nuestra vista y luego usar `tail()`. To do so, we
   create a new DataFrame in which rows and columns are switched:

```python
americas_volteado = data_americas.T
```

Entonces podemos ver las últimas tres columnas de `americas` viendo las tres últimas filas
de `americas_flipped`:

```python
americas_flipped.tail(n=3)
```

```output
country        Argentina  Bolivia   Brazil   Canada    Chile Colombia  \
gdpPercap_1997   10967.3  3326.14  7957.98  28954.9  10118.1  6117.36
gdpPercap_2002   8797.64  3413.26  8131.21    33329  10778.8  5755.26
gdpPercap_2007   12779.4  3822.14   9065.8  36319.2  13171.6  7006.58

country        Costa Rica     Cuba Dominican Republic  Ecuador    ...     \
gdpPercap_1997    6677.05  5431.99             3614.1  7429.46    ...
gdpPercap_2002    7723.45  6340.65            4563.81  5773.04    ...
gdpPercap_2007    9645.06   8948.1            6025.37  6873.26    ...

country          Mexico Nicaragua   Panama Paraguay     Peru Puerto Rico  \
gdpPercap_1997   9767.3   2253.02  7113.69   4247.4  5838.35     16999.4
gdpPercap_2002  10742.4   2474.55  7356.03  3783.67  5909.02     18855.6
gdpPercap_2007  11977.6   2749.32  9809.19  4172.84  7408.91     19328.7

country        Trinidad and Tobago United States  Uruguay Venezuela
gdpPercap_1997             8792.57       35767.4  9230.24   10165.5
gdpPercap_2002             11460.6       39097.1     7727   8605.05
gdpPercap_2007             18008.5       42951.7  10611.5   11415.8
```

Esto muestra los datos que queremos, pero podemos preferir mostrar tres columnas en lugar de tres filas,
para que podamos volverlo hacia atrás:

```python
americas_flipped.tail(n=3).T    
```

**Nota:** podríamos haber hecho lo anterior en una sola línea de código 'encadenando' los comandos:

```python
datos_americas.T.tail(n=3).T
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Leyendo archivos en otros directorios

Los datos para tu proyecto actual se almacenan en un archivo llamado `microbes.csv`,
que se encuentra en una carpeta llamada `field_data`.
Estás haciendo análisis en un cuaderno llamado `analysis.ipynb`
en una carpeta hermana llamada `thesis`:

```output
your_home_directory
+-- field_data/
| +-- microbes.csv
+-- estis/
    +-- analysis.ipynb
```

¿Qué valor(es) debes pasar a `read_csv` para leer `microbes.csv` en `analysis.ipyText`?

::::::::::::::::: solución

## Solución

Necesitamos especificar la ruta al archivo de interés en la llamada a `pd.read_csv`. Primero necesitamos 'saltar' fuera de
la carpeta `estos` usando '../' y luego en la carpeta `field_data` usando 'field_data/'. Luego podemos especificar el nombre de archivo \`microbes.csv.
El resultado es el siguiente:

```python
data_microbes = pd.read_csv('../field_data/microbes.csv')
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Datos de escritura

Además de la función `read_csv` para leer datos de un archivo,
Pandas proporciona una función `to_csv` para escribir nombres de datos en archivos.
Aplicando lo que has aprendido sobre leer de archivos,
escribe uno de tus datosen un archivo llamado `processed.csv`.
Puedes usar `help` para obtener información sobre cómo usar `to_csv`.

::::::::::::::::: solución

## Solución

Para escribir el DataFrame `data_americas` en un archivo llamado `processed.csv`, ejecuta el siguiente comando:

```python
datos_americas.to_csv('procesado.csv')
```

Para ayuda en `read_csv` o `to_csv`, puedes ejecutar, por ejemplo:

```python
ayuda(data_americas.to_csv)
ayuda(pd.read_csv)
```

Ten en cuenta que `help(to_csv)` o `help(pd.to_csv)` lanza un error! Esto se debe al hecho de que `to_csv` no es una función global de Pandas, sino
una función miembro de DataFrames. Esto significa que solo puedes llamarlo en una instancia de un DataFrame
por ejemplo, `data_americas.to_csv` o `data_oceania.to_csv`

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Utilice la biblioteca de Pandas para obtener estadísticas básicas de datos tabulares.
- Usa `index_col` para especificar que los valores de una columna deben ser usados como cabeceras de fila.
- Usa `DataFrame.info` para saber más sobre un nombre de datos.
- La variable `DataFrame.columns` almacena información sobre las columnas del marco de datos.
- Usa `DataFrame.T` para transponer un nombre de datos.
- Usa `DataFrame.describe` para obtener estadísticas resumidas sobre datos.

::::::::::::::::::::::::::::::::::::::::::::::::::
