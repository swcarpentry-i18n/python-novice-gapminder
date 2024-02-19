---
title: Bucle sobre conjuntos de datos
teaching: 5
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- Ser capaz de leer y escribir expresiones de globo que coincidan con conjuntos de archivos.
- Utilice glob para crear listas de archivos.
- Escribe los bucles para realizar operaciones sobre archivos dados sus nombres en una lista.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::::: preguntas

- ¿Cómo puedo procesar muchos conjuntos de datos con un solo comando?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Usa un bucle `for` para procesar archivos dados una lista de sus nombres.

- Un nombre de archivo es una cadena de caracteres.
- Y las listas pueden contener cadenas de caracteres.

```python
import pandas as as pd
for filename in ['data/gapminder_gdp_africa.csv', 'data/gapminder_gdp_asia.csv']:
    data = pd.read_csv(filename, index_col='country')
    print(filename, data.min())
```

```output
data/gapminder_gdp_africa.csv gdpPercap_1952    298.846212
gdpPercap_1957    335.997115
gdpPercap_1962    355.203227
gdpPercap_1967    412.977514
⋮ ⋮ ⋮
gdpPercap_1997    312.188423
gdpPercap_2002    241.165877
gdpPercap_2007    277.551859
dtype: float64
data/gapminder_gdp_asia.csv gdpPercap_1952    331
gdpPercap_1957    350
gdpPercap_1962    388
gdpPercap_1967    349
⋮ ⋮ ⋮
gdpPercap_1997    415
gdpPercap_2002    611
gdpPercap_2007    944
dtype: float64
```

## Usa [`glob.glob`](https://docs.python.org/3/library/glob.html#glob.glob) para encontrar conjuntos de archivos cuyos nombres coinciden con un patrón.

- En Unix, el término "globbing" significa "emparejar un conjunto de archivos con un patrón".
- Los patrones más comunes son:
  - `*` significa "coincidir cero o más caracteres"
  - `?` significa "coincidir exactamente con un carácter"
- La biblioteca estándar de Python contiene el módulo [`glob`](https://docs.python.org/3/library/glob.html) para proporcionar funcionalidad de patrón
- El módulo [`glob`](https://docs.python.org/3/library/glob.html) contiene una función también llamada `glob` para que coincida con los patrones de archivo
- Por ejemplo, `glob.glob('*.txt')` coincide con todos los archivos en el directorio actual
  cuyos nombres terminan con `.txt`.
- El resultado es una lista (posiblemente vacía) de cadenas de caracteres.

```python
import glob
print('todos los archivos csv en el directorio de datos:', glob.glob('data/*.csv'))
```

```output
todos los archivos csv en el directorio de datos: ['data/gapminder_all.csv', 'data/gapminder_gdp_africa.csv', \
'data/gapminder_gdp_americas.csv', 'data/gapminder_gdp_asia.csv', 'data/gapminder_gdp_europe.csv', \
'data/gapminder_gdp_oceania.csv']
```

```python
print('todos los archivos PDB:', glob.glob('*.pdb'))
```

```output
todos los archivos PDB: []
```

## Usa `glob` y `for` para procesar lotes de archivos.

- Ayuda mucho si los archivos son nombrados y almacenados sistemáticamente
  para que los patrones simples encuentren los datos correctos.

```python
for filename in glob.glob('data/gapminder_*.csv'):
    data = pd.read_csv(filename)
    print(filename, data['gdpPercap_1952'].min())
```

```output
data/gapminder_all.csv 298.8462121
data/gapminder_gdp_africa.csv 298.8462121
data/gapminder_gdp_americas.csv 1397.717137
data/gapminder_gdp_asia.csv 331.0
data/gapminder_gdp_europe.csv 973.5331948
data/gapminder_gdp_oceania.csv 10039.59564
```

- Esto incluye todos los datos, así como los datos por región.
- Utilice un patrón más específico en los ejercicios para excluir todo el conjunto de datos.
- Pero tenga en cuenta que el mínimo de todo el conjunto de datos es también el mínimo de uno de los conjuntos de datos,
  que es una buena comprobación de la exactitud.

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Determinar partidas

¿Cuál de estos archivos _no_ coincide con la expresión `glob.glob('data/*as*.csv')`?

1. `data/gapminder_gdp_africa.csv`
2. `data/gapminder_gdp_americas.csv`
3. `data/gapminder_gdp_asia.csv`

::::::::::::::::: solución

## Solución

1 no coincide con el globo.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Tamaño mínimo del archivo

Modifique este programa para que imprima el número de registros en
el archivo que tiene menos registros.

```python
import glob
import pandas as as pd
fewest = ____
para el nombre de archivo en glob.glob('data/*.csv'):
    datsalario = pd. ___(nombre de archivo)
    menos = min(____, dataframe.shape[0])
print('archivo más pequeño tiene', menos 'registros')
```

Tenga en cuenta que el [`DataFrame.shape()` método][shape-method]
devuelve una tupla con el número de filas y columnas del marco de datos.

::::::::::::::::: solución

## Solución

```python
import glob
import pandas as as pd
fewest = float('Inf')
para el nombre de archivo en glob.glob('data/*.csv'):
    datsalario = pd. ead_csv(nombre de archivo)
    menor = min(menos, dataframe.shape[0])
print('el archivo más pequeño tiene', menos, 'registros')
```

Puede que hayas elegido inicializar la variable `fewest` con un número mayor que los números
que estás tratando, pero eso podría causar problemas si reutilizas el código con números más grandes.
Python te permite usar infinidad positiva, que funcionará sin importar lo grandes que sean tus números.
¿Qué otras cadenas especiales reconoce la [función 'float'][float-function]?

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Comparando datos

Escribe un programa que lea en los datos regionales establece
y grafica el PIB promedio per cápita para cada región a lo largo del tiempo
en un solo gráfico.

::::::::::::::::: solución

## Solución

Esta solución construye una leyenda útil usando el [método `split`][split-method] a
extrae `region` de la ruta 'data/gapminder\_gdp\_a\_specific\_region.csv'.

```python
import glob
import pandas as as pd
import matplotlib.pyplot as plotlib.pyplot as plt
fig, ax = plt.subplots(1,1)
for filename in glob.glob('data/gapminder_gdp*. sv'):
    datos de nombre = pd. ead_csv(filename)
    # extrae <region> del nombre de archivo, se espera que esté en el formato 'data/gapminder_gdp_<region>.csv'.
    # dividiremos la cadena usando el método dividido y `_` como nuestro separador,
    # recupera la última cadena de la lista que retorna (`<region>. sv`), 
    # y luego eliminar el `. sv` extensión de esa cadena.
    region = filename.split('_')[-1][:-4] 
    nombre de datos. ean().plot(ax=ax, label=region)
plt.legend()
plt.show()
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## Tratando rutas de archivos

El [`pathlib` module][pathlib-module] proporciona abstracciones útiles para la manipulación de archivos y rutas como
devolviendo el nombre de un archivo sin la extensión del archivo. Esto es muy útil al hacer bucle sobre archivos y directorios
. En el ejemplo siguiente, creamos un objeto `Path` e inspeccionamos sus atributos.

```python
from pathlib import Path

p = Path("data/gapminder_gdp_africa.csv")
print(p.parent), print(p.stem), print(p.suffix)
```

```output
datos
gapminder_gdp_Physica
.csv
```

**Pista:** ¡Es posible comprobar todos los atributos y métodos disponibles en el objeto `Ruta` con la función `dir()`
!

::::::::::::::::::::::::::::::::::::::::::::::::::

[shape-method]: https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.shape.html

[float-function]: https://docs.python.org/3/library/functions.html#float

[split-method]: https://docs.python.org/3/library/stdtypes.html#str.split

[pathlib-module]: https://docs.python.org/3/library/pathlib.html

:::::::::::::::::::::::::::::::::::::::: keypoints

- Usa un bucle `for` para procesar archivos dados una lista de sus nombres.
- Usa `glob.glob` para encontrar conjuntos de archivos cuyos nombres coinciden con un patrón.
- Usa `glob` y `for` para procesar lotes de archivos.

::::::::::::::::::::::::::::::::::::::::::::::::::
