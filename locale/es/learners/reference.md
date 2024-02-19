---
title: Referencia
---

## Referencia

## [Ejecutando y Saliendo](episodes/01-run-quit.md)

- Los archivos Python tienen la extensión `.py`.
- Puede escribirse en un archivo de texto o en un [Jupyter Notebook][jupyter].
  - Los cuadernos de Jupyter tienen la extensión `.ipynb`
  - Los cuadernos de Jupyter pueden abrirse desde [Anaconda](https://docs.continuum.io/anaconda/install) o a través de la línea de comandos ingresando `$ cuadernos de jupyter`
    - Markdown y HTML están permitidos en las celdas markdown para documentar código.

## [Variables y asignaciones](episodes/02-variables.md)

- Las variables se almacenan usando `=`.
  - Las cadenas se definen en las comillas `'...'`.
  - Los números enteros y los números de punto flotante se definen sin comillas.
- Las variables pueden contener letras, dígitos y guiones bajos `_`.
  - No se puede comenzar con un dígito.
  - Las variables que comienzan con guiones bajos deben evitarse.
- Use `print(...)` para mostrar los valores como texto.
- Puede usar indexación en cadenas.
  - La indexación comienza en 0.
  - La posición es dada entre corchetes `[position]` siguiendo el nombre de la variable.
  - Toma una rebanada usando `[start:stop]`. Esto hace una copia de parte de la cadena original.
    - `start` es el índice del primer elemento.
    - `stop` es el índice del elemento después del último elemento deseado.
- Usa `len(...)` para encontrar la longitud de una variable o cadena.

## [Conversión de tipos de datos](episodes/03-types-conversion.md)

- Cada valor tiene un tipo. Esto controla lo que se puede hacer con él.
  - `int` representa un entero
  - `float` representa un número de punto flotante.
  - `str` representa una cadena.
- Para determinar un tipo de variable, utilice la función integrada `type(...)`, incluyendo el nombre de variable en el paréntesis.
- Modificando cadenas:
  - Usa `+` para concatenar cadenas.
  - Usa `*` para repetir una cadena.
  - Los números y las cadenas no se pueden añadir en otra.
    - Convierte la cadena a entero: `int(...)`.
    - Convierte entero a cadena: `str(...)`.

## [Funciones y ayuda integradas](episodes/04-built-in.md)

- Para añadir un comentario, coloca `#` antes de lo que no tienes para ser ejecutado.
- Funciones integradas empleadas por Común:
  - `min()` encuentra el valor más pequeño.
  - `max()` encuentra el mayor valor.
  - `round()` redondea un número de punto flotante.
  - `help()` muestra la documentación de la función en el paréntesis.
    - Otras formas de obtener ayuda incluyen mantener presionado `shift` y presionar `tab` en Jupyter Notebooks.

## [Libraries](episodios/06-libraries.md)

- Importando una biblioteca:
  - Usa `importar ...` para cargar una biblioteca.
  - Consulte esta biblioteca usando `module_name.thing_name`.
    - `.` indica 'parte de'.
- Para importar un elemento específico de una biblioteca: `de ... importar ...`
- Para importar una biblioteca usando un alias: `importar ... como ...`
- Importando la librería de matemáticas: `importar matemáticas`
  - Ejemplo de referencia a un elemento con el nombre del módulo: `math.cos(math.pi)`.
- Importando la biblioteca de trazado como un alias: `importar matplotlib como mpl`

## [Leyendo datos tabulares en DataFrames](episodes/07-reading-tabular.md)

- Utilice la biblioteca de pandas para hacer estadísticas sobre datos tabulares. Carga con `import pandas como pd`.
  - Para leer en un csv: `pd.read_csv()`, incluyendo el nombre de la ruta en el paréntesis.
    - Para especificar los valores de una columna debe utilizarse como encabezados de filas: `pd. ead_csv('ruta', index_col='nombre de columna')`, donde el nombre de la ruta y la columna deben ser reemplazados con los valores relevantes.
- Para obtener más información sobre un DataFrame, usa `DataFrame.info`, reemplazando `DataFrame` con el nombre de la variable de tu DataFrame.
- Usa `DataFrame.columns` para ver los nombres de columnas.
- Usa `DataFrame.T` para transponer un DataFrame.
- Usa `DataFrame.describe` para obtener estadísticas resumidas sobre tus datos.

## [Pandas DataFrames](episodes/08-data-frames.md)

- Selecciona datos usando `[i,j]`
  - Para seleccionar por posición de entrada: `DataFrame.iloc[..., ...]`
    - Esto incluye todo excepto el índice final.
  - Para seleccionar por etiqueta de entrada: `DataFrame.loc[..., ...]`
    - Puede seleccionar varias filas o columnas listando etiquetas.
    - Esto es inclusivo en ambos extremos.
  - Use `:` para seleccionar todas las filas o columnas.
- También puede seleccionar datos basados en valores usando `True` y `False`. Esta es una máscara booleana.
  - `máscara = subconjunto > 10000`
  - Entonces podemos usar esto para seleccionar los valores.
- Para usar una operación select-apply-combine usamos `data.apply(lambda x: x > x. ean())` donde `mean()` puede ser cualquier operación que el usuario desee aplicar a x.

## [Plotting](episodios/09-plotting.md)

- La biblioteca de plotting más utilizada es `matplotlib`.
  - Generalmente importado usando `import matplotlib.pyplot como plt`.
  - Para graficar usamos el comando `plt.plot(time, position)`.
  - Para crear una leyenda usa `plt.legend(['label1', 'label2'], loc='upper left')`
    - También puede definir etiquetas dentro de las sentencias de trazo usando `plt.plot(time, position, label='label')`. Para hacer que la leyenda aparezca, usa `plt.legend()`
  - Para etiquetar el eje x y y `plt.xlabel('label')` y `plt.ylabel('label')` son usados.
- Pandas DataFrames puede ser usado para graficar usando `DataFrame.plot()`. Cualquier operación que pueda ser usada en un DataFrame puede ser aplicada durante el trazado.
  - Para graficar una gráfica de barras `data.plot(kind='bar')`

```python
importar matplotlib.puplot como plot
plt.plot(time, position, label='label')
plt.xlabel('x axis label')
plt.ylabel('y axis label')
plt.legend()
```

## [Lists](episodios/11-lists.md)

- Definido dentro de `[...]` y separado por `,`.
  - Una lista vacía puede ser creada usando `[]`.
- Puede usar `len(...)` para determinar cuántos valores hay en una lista.
- Puede indexar como se hizo en lecciones anteriores.
  - La indexación puede utilizarse para reasignar valores `list_name[0] = newvalue`.
- Para añadir un elemento a una lista usa `list_name.append()`, con el elemento para añadir en el paréntesis.
- Para combinar dos listas use `list_name_1.extend(list_name_2)`.
- Para eliminar un elemento de una lista use `del list_name[index]`.

## [Para Loops](episodes/12-for-loops.md)

- Comienza un bucle for for number con `for number in [1, 2, 3]:`, con las siguientes líneas sangradas.
  - `[1, 2, 3]` es considerada la colección.
  - `number` es la variable de bucle.
  - La acción que sigue a la colección es el cuerpo.
- Para iterar sobre una secuencia de números usa `range(start, end)`

```python
para número en rango(0,5):
    print(number)
```

## [Conditionals](episodios/13-conditionals.md)

- Definido de forma similar a un bucle, usando `if variable condicional value:`.
  - Por ejemplo, `if variable > 5:`.
- Usa `elif:` para pruebas adicionales.
- Usa `else:` para cuando el comando si no es verdadero.
- Puede combinar más de una condición, usando `and` o `o`.
- A menudo se utiliza en combinación con bucles.
- Condiciones que se pueden utilizar:
  - `==` igual.
  - `>=` mayor o igual a.
  - `<=` menos o igual a.
  - `>` mayor que eso.
  - `<` menos que eso.

```python
para m en [3, 6, 7, 2, 8]:
    if m > 5:
        print(m, 'is large')
    elif m == 5:
        print(m, 'es 5')
    más:
        print(m, 'es pequeño')
```

## [Conjuntos de datos de bucles](episodes/14-looping-data-sets.md)

- Usa un bucle for : `for filename en [file1, file2]:`
- Para encontrar un conjunto de archivos usando un patrón usa `glob.glob`
  - Debe importar primero usando `import glob`.
  - `*` indica "coincidir cero o más caracteres"
  - `?` indica "coincidir exactamente con un carácter"
    - Por ejemplo: `glob.glob(*.txt)` encontrará todos los archivos que terminen con `.txt` en el directorio actual.
- Combina estos escribiendo un bucle utilizando: `para nombre de archivo en glob.glob(*.txt):`

```python
para nombre de archivo en glob.glob(*.txt):
  datos = pd.read_csv(nombre de archivo)
```

## [Escribiendo funciones](episodes/16-writing-functions.md)

- Definir una función usando `def function_name(parameters):`. Reemplaza `parameters` con las variables a usar cuando se ejecuta la función.
- Ejecute usando `function_name(parameters)`.
- Para devolver un resultado a la persona que llama usa `return ...` en la función.

```python
def add_numbers(a, b):
    result = a + b
    return result

add_numbers(1, 4)
```

## [Ámbito variable](episodes/17-scope.md)

- Una variable local se define en una función y sólo puede ser vista y usada dentro de esa función.
- Una variable global se define fuera de una función y puede ser vista o usada en cualquier lugar después de la definición.

## [Estilo de programación](episodes/18-style.md)

- Documenta tu código.
- Utilice nombres de variables claros y significativos.
- Sigue [la guía de estilo PEP8](https://www.python.org/dev/peps/pep-0008) al configurar tu código.
- Utilice las afirmaciones para comprobar si hay errores internos.
- Utilice docstrings para proporcionar ayuda.

## Glossary

Argumentos
: Valores pasados a las funciones.

Array
: Un contenedor que contiene elementos del mismo tipo.

Booleano
: Un objeto compuesto por `True` y `False`.

DataFrame
: La forma en que Pandas representa una tabla; una colección de series.

Elemento
: Un elemento en una lista o un arreglo. Para una cadena, estos son los caracteres individuales.

Función
: Un bloque de código que puede ser llamado y reutilizado en otros lugares.

Variable global
: Una variable definida fuera de una función que puede ser usada en cualquier lugar.

Índice
: La posición de un elemento determinado.

Jupyter Notebook
: Entorno de codificación interactivo que permite una combinación de código y markdown.

Biblioteca
: Una colección de archivos que contienen funciones utilizadas por otros programas.

Variable local
: Una variable definida dentro de una función que sólo puede ser usada dentro de esa función.

Máscara
: Un objeto booleano utilizado para seleccionar datos de otro objeto.

Método
: Una acción vinculada a un objeto en particular. Llamado usando `object.method`.

Módulos
: Los archivos dentro de una biblioteca que contienen funciones utilizadas por otros programas.

Parámetros
: Variables utilizadas al ejecutar una función.

Serie
: Una estructura de datos de Pandas para representar una columna.

Subcadena
: Una parte de una cadena.

Variables
: Nombres de valores.
