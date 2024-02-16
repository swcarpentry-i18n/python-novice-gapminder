---
title: Plotando
teaching: 15
exercises: 15
---

::::::::::::::::::::::::::::::::::::::: objectives

- Crear una gráfica de serie de tiempo que muestre un único conjunto de datos.
- Crea un diagrama de dispersión mostrando la relación entre dos conjuntos de datos.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::::: preguntas

- ¿Cómo puedo trazar mis datos?
- ¿Cómo puedo guardar mi parcela para la publicación?

::::::::::::::::::::::::::::::::::::::::::::::::::

## [`matplotlib`](https://matplotlib.org/) es la biblioteca de trazado científico más utilizada en Python.

- Comúnmente usa una subbiblioteca llamada [`matplotlib.pyplot`](https://matplotlib.org/stable/tutorials/introductory/pyplot.html).
- El Notebook de Jupyter renderizará las parcelas en línea por defecto.

```python
importar matplotlib.pyplot como plt
```

- Las parcelas simples son entonces (justamente) simples de crear.

```python
time = [0, 1, 2, 3]
position = [0, 100, 200, 300]

plt.plot(time, position)
plt.xlabel('Time (hr)')
plt.ylabel('Posición (km)')
```

![](fig/9_simple_position_time_plot.svg){alt='Simple Posición-Tiempo Plot'}

:::::::::::::::::::::::::::::::::::::::::  callout

## Mostrar todas las Figuras Abiertas

En nuestro ejemplo de Jupyter Notebook, ejecutar la celda debe generar la figura directamente debajo del código.
La figura también está incluida en el documento Notebook para su futura visualización.
Sin embargo, Otros entornos Python como una sesión interactiva de Python iniciada desde una terminal
o un script Python ejecutado a través de la línea de comandos requieren un comando adicional para mostrar la figura.

Instruye `matplotlib` para mostrar una figura:

```python
plt.show()
```

Este comando también se puede usar dentro de un Cuaderno - por ejemplo, para mostrar múltiples figuras
si varias son creadas por una sola celda.

::::::::::::::::::::::::::::::::::::::::::::::::::

## Trazar datos directamente desde un [`Pandas dataframe`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html).

- También podemos graficar [nombres de datos de Pandas](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.html).
- Antes de graficar, convertimos los encabezados de columnas de un tipo de datos `string` a `integer`, ya que representan valores numéricos,
  usando [str.replace()](https\://pandas.pydata.org/docs/reference/api/pandas.Series.str.replace. tml) para eliminar el prefijo `gpdPercap_`
  y luego [astype(int)](https\://pandas.pydata.org/docs/reference/api/pandas.Series.astype. tml)
  para convertir la serie de valores de cadena (`['1952', '1957', ..., '2007']`) a una serie de enteros: `[1925, 1957, ..., 2007]`.

```python
import pandas as pd

data = pd.read_csv('data/gapminder_gdp_oceania.csv', index_col='country')

# Extract year from last 4 characters of each column name
# The current column names are structured as 'gdpPercap_(year)', 
# so we want to keep the (year) part only for clarity when plotting GDP vs. years
# To do this we use replace(), which removes from the string the characters stated in the argument
# This method works on strings, so we use replace() from Pandas Series.str vectorized string functions

years = data.columns.str.replace('gdpPercap_', '')

# Convert year values to integers, saving results back to dataframe

data.columns = years.astype(int)

data.loc['Australia'].plot()
```

![](fig/9_gdp_australia.svg){alt='Grafico del PIB para el país'}

## Seleccione y transforme los datos y luego guárdelos.

- Por defecto, [`DataFrame.plot`](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.plot.html#pandas.DataFrame.plot) grafica con las filas como el eje X.
- Podemos transponer los datos con el fin de trazar múltiples series.

```python
data.T.plot()
plt.ylabel('PIB per cápita')
```

![](fig/9_gdp_australia_nz.svg){alt='gráfica del PIB para Australia y Nueva Zelanda'}

## Muchos estilos de parcela están disponibles.

- Por ejemplo, haga un gráfico de barras usando un estilo más elegante.

```python
plt.style.use('ggplot')
data.T.plot(kind='bar')
plt.ylabel('PIB per cápita')
```

![](fig/9_gdp_bar.svg){alt='PGB trampa de desmembramiento para el éxito'}

## Los datos también se pueden trazar llamando directamente a la función `matplotlib` `plot`.

- El comando es `plt.plot(x, y)`
- El color y el formato de los marcadores también se pueden especificar como un argumento opcional adicional e. ., `b-` es una línea azul, `g--` es una línea de guiones verdes.

## Obtener datos de Australia a partir del nombre

```python
años= data.columns
gdp_australia = data.loc['Contrasalia']

plt.plot(years, gdp_australia, 'g--')
```

![](fig/9_gdp_australia_formatted.svg){alt='PGB con formato de trama para mañalia'}

## Puede graficar muchos conjuntos de datos juntos.

```python
# Selecciona dos países' de datos.
gdp_australia = data.loc['mañalia']
gdp_nz = data.loc['Nueva Zeland']

# Dibuja con marcadores de diferentes colores.
pt. lot(years, gdp_australia, 'b-', label='Necesitalia')
plt.plot(years, gdp_nz, 'g-', label='Nueva Zelanda')

# Crear leyenda.
plt.legend(loc='superior izquierda')
plt.xlabel('año')
plt.ylabel('PIB per cápita ($)')
```

:::::::::::::::::::::::::::::::::::::::::  callout

## Añadir una leyenda

A menudo al graficar múltiples conjuntos de datos en la misma figura es deseable tener
una leyenda que describa los datos.

Esto puede hacerse en `matplotlib` en dos etapas:

- Proporciona una etiqueta para cada conjunto de datos en la figura:

```python
plt.plot(years, gdp_australia, label='Ninguna')
plt.plot(years, gdp_nz, label='Nueva Zelanda')
```

- Instruye `matplotlib` para crear la leyenda.

```python
plt.legend()
```

Por defecto matplotlib intentará colocar la leyenda en una posición adecuada. Si usted
prefiere especificar una posición, esto puede hacerse con el argumento `loc=`, e. para colocar
la leyenda en la esquina superior izquierda de la parcela, especifica `loc='upper left'`

::::::::::::::::::::::::::::::::::::::::::::::::::

![](fig/9_gdp_australia_nz_formatted.svg){alt='PGB con formato para Australia y Nueva Zelanda'}

- Trazar una trama de dispersión que correlacione el PIB de Australia y Nueva Zelanda
- Usa `plt.scatter` o `DataFrame.plot.scatter`

```python
plt.scatter(gdp_australia, gdp_nz)
```

![](fig/9_gdp_correlation_plt.svg){alt='Correlación del PIB usando plt.scatter'}

```python
data.T.plot.scatter(x = 'Corealia', y = 'Nueva Zelanda')
```

![](fig/9_gdp_correlation_data.svg){alt='Correlación del PIB usando datos.T.plot.scatter'}

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Minima y Maxima

Rellena los siguientes espacios en blanco para conscribir el PIB mínimo per cápita a lo largo del tiempo
para todos los países de Europa.
Modifiquémosla de nuevo para consagrar el PIB máximo per cápita a lo largo del tiempo para Europa.

```python
data_europe = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')
data_europe.____.plot(label='min')
data_europe.____
plt.legend(loc='mejor')
plt.xticks(rotation=90)
```

::::::::::::::::: solución

## Solución

```python
data_europe = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')
data_europe.min().plot(label='min')
data_europe.max().plot(label='max')
plt.legend(loc='mejor')
plt.xticks(rotation=90)
```

![](fig/9_minima_maxima_solution.png){alt='Solución máxima minima'}

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Correlaciones

Modificar el ejemplo en las notas para crear un diagrama disperso que muestre
la relación entre el PIB mínimo y máximo per cápita
entre los países de Asia por año en el conjunto de datos.
¿Qué relación ves (si la hay)?

::::::::::::::::: solución

## Solución

```python
data_asia = pd.read_csv('data/gapminder_gdp_asia.csv', index_col='country')
data_asia.describe().T.plot(kind='scatter', x='min', y='max')
```

![](fig/9_correlacions_solution1.svg){alt='Solución de correlaciones 1'}

No se puede ver ninguna correlación particular entre los valores mínimos y máximos de gdp
año tras año. Parece que las fortunas de los países asianos no se levantan y caen juntos.

:::::::::::::::::::::::::

Puede que tenga en cuenta que la variabilidad en el máximo es mucho mayor que
la del mínimo.  Echa un vistazo a los índices máximos y máximos:

```python
data_asia = pd.read_csv('data/gapminder_gdp_asia.csv', index_col='country')
data_asia.max().plot()
print(data_asia.idxmax())
print(data_asia.idxmin())
```

::::::::::::::::: solución

## Solución

![](fig/9_correlacions_solution2.png){alt='Solución de correlaciones 2'}

Parece que la variabilidad en este valor se debe a una caída brusca después de 1972.
Algunos geopolíticos en juego tal vez? Dado el dominio de los países productores de petróleo,
¿Tal vez el índice crudo de Brent haría una comparación interesante?
Mientras que Myanmar tiene consistentemente el gdp más bajo, la nación gdb más alta ha variado
de manera más notable.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Más correlaciones

Este corto programa crea una parcela que muestra
la correlación entre el PIB y la esperanza de vida para 2007,
normalizando el tamaño del marcador por población:

```python
data_all = pd.read_csv('data/gapminder_all.csv', index_col='country')
data_all.plot(kind='scatter', x='gdpPercap_2007', y='lifeExp_2007',
              s=data_all['pop_2007']/1e6)
```

Usando ayuda en línea y otros recursos,
explica lo que hace cada argumento a `plot`.

::::::::::::::::: solución

## Solución

![](fig/9_more_correlations_solution.svg){alt='Más Correlaciones'}

Un buen lugar para buscar es la documentación de la función de trazado -
ayuda (data_all.plot).

tipo - Como ya se ha visto, esto determina el tipo de parcela a dibujar.

x y y - Un nombre o índice de columna que determina qué datos serán
colocados en los ejes x e y de la trama

s - Los detalles para esto se pueden encontrar en la documentación de plt.scatter.
Un único número o un valor para cada punto de datos. Determina el tamaño
de los puntos trazados.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## Guardando tu trama en un archivo

Si está satisfecho con la parcela que ve puede guardarla en un archivo,
tal vez para incluirlo en una publicación. Hay una función en el módulo
matplotlib.pyplot que cumple esto:
[savefig](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.savefig.html).
Llamando a esta función, por ejemplo, con

```python
plt.savefig('mi_figure.png')
```

guardará la figura actual en el archivo `my_figure.png`. El formato de archivo
se deducirá automáticamente de la extensión del nombre del archivo (otros formatos
son pdf, ps, eps y svg).

Ten en cuenta que las funciones en `plt` se refieren a una variable global de la figura
y después de que se haya mostrado una figura en la pantalla (e. . con `plt.show`)
matplotlib hará que esta variable se refiera a una nueva figura vacía.
Por lo tanto, asegúrese de llamar a `plt.savefig` antes de que la gráfica se muestre en
la pantalla, de lo contrario puede encontrar un archivo con una gráfica vacía.

Cuando se usan nombres de datos, los datos se generan y se graban en una sola línea.
Además de usar `plt.savefig`, podemos guardar una referencia a la figura actual
en una variable local (con `plt. cf`) y llamar al método de clase `savefig` de
esa variable para guardar la figura en el archivo.

```python
data.plot(kind='bar')
fig = plt.gcf() # obtener la figura actual
fig.savefig('my_figure.png')
```

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## Hacer que sus parcelas sean accesibles

Cada vez que estás generando gráficos para ir a un papel o una presentación, hay algunas cosas que usted puede hacer para asegurarse de que todos puedan entender sus parcelas.

- Siempre asegúrese de que su texto sea lo suficientemente grande para leer. Usa el parámetro `fontsize` en `xlabel`, `ylabel`, `title`, y `legend`, y [`tick_params` con `labelsize`](https://matplotlib.org/stable/api/_as_gen/matplotlib.axes.Axes.tick_params.html) para aumentar el tamaño de texto de los números en tus ejes.
- Del mismo modo, debería facilitar la visualización de los elementos de su gráfico. Usa `s` para aumentar el tamaño de tus marcadores scatterplot y `ancho de línea` para aumentar los tamaños de tus líneas de diagrama.
- Utilizar el color (y nada más) para distinguir entre diferentes elementos de la parcela hará que tus parcelas sean ilegibles para cualquiera que esté cegado de color, o que tiene una impresora de oficina negra y blanca. Para líneas, el parámetro `linestyle` le permite usar diferentes tipos de líneas. Para scatterplots, `marker` te permite cambiar la forma de tus puntos. Si no estás seguro de tus colores, puedes usar [Coblis](https\://www\.color-blindness. om/coblis-color-blindness-simulator/) o [Oráculo de colores](https://colororacle.org/) para simular cómo se verían tus parcelas a aquellos con colorido.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- [`matplotlib`](https://matplotlib.org/) es la biblioteca de trazado científico más utilizada en Python.
- Trazar datos directamente desde un nombre de datos de Pandas.
- Seleccione y transforme los datos y luego guárdelos.
- Hay muchos estilos de gráficos disponibles: vea la [Galería gráfica de Python](https://python-graph-gallery.com/matplotlib/) para más opciones.
- Puede graficar muchos conjuntos de datos juntos.

::::::::::::::::::::::::::::::::::::::::::::::::::
