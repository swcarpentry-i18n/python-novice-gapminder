---
title: Diseño de Lección
---

:::::::::::::::::::::::::::::::::::::::::  callout

## Ayuda Deseada

**Estamos rellenando los ejercicios [below](#stage-3-learning-plan)
para hacer el plan de clase más concreto.
Las contribuciones (tanto en forma de solicitudes de extracción con ejercicios rellenados,
y comentarios sobre ejercicios específicos, pedidos y tiempos) son muy apreciadas.**

::::::::::::::::::::::::::::::::::::::::::::::::::

## Proceso usado

> El consejo de Michael Pollan, si enseñó programación de R o Python:
>
> 1. Escribir código.
> 2. No demasiado.
> 3. Principalmente parcelas.
>
> — [Michael K.Utz](https://twitter.com/_mik.Utz/status/758021742078025728)
> {: .quotation}

Esta lección se desarrolló utilizando una variante adelgazada del proceso "Entendimiento por Diseño".
Las secciones principales son:

1. Assumptions about audience, time, etc.
   (The current draft also includes some conclusions and decisions in this
   section - that should be refactored.)

2. Resultados deseados:
   objetivos generales, evaluaciones sumativas en granularidad de medio día, lo que los estudiantes
   podrán hacer, lo que los estudiantes sepan.

3. Plan de aprendizaje:
   cada episodio tiene un título que resume lo que será cubierto,
   entonces calcula el tiempo que se dedicará a la enseñanza y a los ejercicios,
   mientras los ejercicios se dan como puntos de bala.

## Etapa 1: Supuestos

- Público
  - Gradua a los estudiantes en disciplinas numeradas desde la cosmología hasta la arqueología
  - Quién ha manipulado datos en hojas de cálculo y con herramientas interactivas como SAS
  - Pero _no_ han programado más allá de la CPD (copiar-pegar-desesperación)
- Restricciones
  - Un día completo 09:00-16:30
    - Tiempo de la clase 06:15
    - Almuerzo 0:45
    - 0:30 total para dos pausas de café
  - Los estudiantes utilizan instalaciones nativas en sus propias máquinas
    - Puede usar máquinas virtuales o recursos en la nube a discreción del instructor
    - Pero debe mantener la instalación local nativa como opción
  - No depender de otros módulos de Carpintería
    - En particular, no requiere conocimiento de shell o control de versiones
  - Usa el Cuadro de notas de Jupyter
    - Herramienta auténtica usada por muchos instructores
    - No hay realmente una alternativa
    - Y significa que incluso la gente que ha visto un poco de Python antes de
      probablemente aprenderá algo
- Motivando Ejemplo
  - Crear parcelas 2D adecuadas para su inclusión en documentos
  - Apelaciones a casi todos
  - Hace que la lección sea utilizable por ambos carpentradas
    - Y significa que incluso la gente que ha visto un poco de Python antes de
      probablemente aprenderá algo
- Datos
  - Usar los datos del gapminder a lo largo de todo
  - Pero rompa en múltiples archivos por continente
    - Para hacer la visualización de la salida a partir de ejemplos de mareador
      (por ejemplo, utilice el menú contextual/neozelandés, que es sólo dos líneas)
    - Y permitir ejemplos que muestran el uso de múltiples conjuntos de datos
- Concentrarse en Pandas en lugar de en NumPy
  - Hace que la lección sea utilizable tanto por la Carpintería de Datos como por la Carpintería de Software
  - Es probable que los principiantes originales quieran análisis de datos
  - Y personas con alguna experiencia anterior:
    - aceptará el análisis de datos como una tarea auténtica,
    - y es poco probable que haya encontrado a Pandas,
      así que seguirán recibiendo algo útil de la lección
- Los desafíos _no_ serán "escribir este código desde cero"
  - Desea muchos ejercicios cortos que puedan ser terminados de forma fiable en tiempo asignado
  - Así que use MCQs, llene en blanco, Parsons Problems, "modifique este código", etc.

## Etapa 2: Resultados deseados

### Preguntas

¿Cómo lo hago...

- ...leer datos tabular?
- ...grafica un único vector de valores?
- ...crear una trama de series horarias?
- ...crear un gráfico para cada uno de varios conjuntos de datos?
- ...obtener datos adicionales de un único conjunto de datos para trazar?
- ...escribir programas que puedo leer y reutilizar en el futuro?

### Habilidades

Puedo...

- ...escribir scripts cortos usando bucles y condicionales.
- ...escribir funciones con un número fijo de parámetros que devuelven un único resultado.
- ...importar bibliotecas usando alias y referirse al contenido de esas bibliotecas.
- ...hacer simple extracción de datos y formato usando Pandas.

### Conceptos

Lo soy...

- ...que un programa es una pieza de equipo de laboratorio que implementa un análisis
  - Necesita ser validado/calificado antes de usar/durante el uso
  - Hace que el análisis sea reproducible, revisable, compartible
- ...que los programas están escritos para personas, no para computadoras
  - Nombres de variables
  - Modularidad para legibilidad y reutilización
  - Sin duplicación
  - Propósito y uso del documento
- ...que no hay magia: los programas que usan no son diferentes
  en principio de aquellos que construyen
- ...cómo asignar valores a variables
- ...qué enteros, flotantes, cadenas, matrices NumPy y datosPandas son
- ...cómo rastrear la ejecución de un bucle `for`
- ...cómo rastrear la ejecución de las sentencias `si`/`else`
- ...cómo crear y indexar listas
- ...cómo crear e indexar matrices NumPy
- ...cómo crear e indexar los nombres de datos de Pandas
- ...cómo crear gráficos de series de tiempo
- ...la diferencia entre definir y llamar una función
- ...dónde encontrar documentación sobre bibliotecas estándar
- ...cómo averiguar qué más ofrece Python científico

## Etapa 3: Plan de aprendizaje

### Evaluación resumida

- Midpoint: cree una trama de serie temporal para cada archivo en un directorio.
- Final: extrae datos de la fecha
  de Pandas y cree una gráfica comparativa de series de tiempo de varias líneas.

### [Ejecutando y Saliendo Interactivamente](../episodes/01-run-quit.md) (9:00)

- Enseñando: 15 min (porque problemas de configuración)
  - Inicie el Notebook de Jupyter, cree nuevos cuadernos y salga del Notebook.
  - Crear celdas de Markdown en un cuaderno.
  - Crear y ejecutar celdas de Python en un cuaderno.
- Desafíos: 0 min (contabilizado en tiempo de enseñanza - sin ejercicios separados)
  - Creando listas en Markdown
  - ¿Qué se muestra cuando se ponen varias expresiones en una sola celda?
  - Cambiar una celda existente de código a Markdown
  - Renderizando ecuaciones de estilo LaTeX

### [Variables y asignaciones](../episodes/02-variables.md) (9:15)

- Enseñando: 10 min
  - Escriba programas que asignen valores escalares a variables y realicen cálculos con esos valores.
  - Rastrear correctamente los cambios de valor en los programas que usan asignación escalar.
- Desafíos: 10 min
  - Ejecución de seguimiento de código intercambiando dos valores usando una variable intermedia.
  - Predecir los valores finales de las variables después de varias asignaciones.
  - ¿Qué pasa si intentas indexar un número?
  - ¿Cuál es un mejor nombre de variable, `m`, `min`, o `minutes`?
  - ¿Qué producen las siguientes expresiones de rebanada?

### [Conversión de tipos de datos](../episodes/03-types-conversion.md) (09:35)

- Enseñando: 10 min
  - Explicar las diferencias de clave entre enteros y números de punto flotante.
  - Explicar las diferencias entre números y cadenas de caracteres.
  - Utilice funciones integradas para convertir entre enteros, números de punto flotante y cadenas.
- Desafíos: 10 min
  - ¿Qué tipo de valor es 3.4?
  - ¿Qué tipo de valor es 3.25 + 4?
  - Qué tipo de valor usaría para representar:
    - Número de días desde el comienzo del año.
    - Tiempo transcurrido desde el comienzo del año.
    - Etc.
  - ¿Cómo puedes usar `//` (división entera) y `%` (modulo)?
  - ¿Qué hace `int("3.4")`?
  - Dados estos valores flotantes, int, y cadenas, ¿qué expresiones imprimirán un resultado particular?
  - ¿Qué esperas que produzca `1+2j + 3`?

### [Funciones y ayuda integradas](../episodes/04-built-in.md) (09:55)

- Enseñando: 15 min
  - Explicar el propósito de las funciones.
  - Llamar correctamente a las funciones incorporadas de Python.
  - Anidar correctamente las llamadas a funciones integradas.
  - Utilice ayuda para mostrar documentación para funciones integradas.
  - Describe correctamente las situaciones en las que se producen SyntaxError y NameError.
- Desafíos: 10 min
  - Explicar el orden de las operaciones en la siguiente expresión compleja.
  - ¿Qué producirá cada combinación anidada de llamadas `min` y `max`?
  - ¿Por qué no `max` y `min` devuelven `nunca` cuando no se dan argumentos?
  - Dada lo que hemos visto hasta ahora,
    ¿qué expresión de índice obtendrá el último carácter en una cadena?

### [Coffee](../episodes/05-café.md): 15 min (10:20)

### [Libraries](../episodes/06-libraries.md) (10:35)

- Enseñando: 10 min
  - Explique qué son las bibliotecas de software y por qué los programadores las crean y las utilizan.
  - Escribe programas que importan y usan bibliotecas de la biblioteca estándar de Python.
  - Encuentre y lea documentación para las bibliotecas estándar de forma interactiva (en el intérprete) y en línea.
- Desafíos: 10 min
  - ¿Qué función de la biblioteca estándar de matemáticas puede usar para calcular una raíz cuadrada?
  - ¿Qué biblioteca usaría para seleccionar un valor aleatorio de datos?
  - Si `help(math)` produce un error, ¿qué has olvidado hacer?
  - Rellene los espacios en blanco en el código de abajo para que la instrucción de importación y el programa funcionen.

### [Leyendo datos tabular](../episodes/07-reading-tabular.md) (10:55)

- Enseñando: 10 min
  - Importa la biblioteca de Pandas.
  - Utilice Pandas para cargar un simple conjunto de datos CSV.
  - Obtener información básica sobre un DataFrame de Pandas.
- Desafíos: 10 min
  - Lea los datos para las Américas y muestre sus estadísticas resumidas.
  - ¿Qué hacen `.head` y `.tail`?
  - ¿Qué cadena(s) debe pasar a `read_csv` para leer archivos de otros directorios?
  - ¿Cómo puedes _escribir_ los datos CSV?

### [DataFrames](../episodes/08-data-frames.md) (11:15)

- Enseñando: 15 min
  - Seleccione valores individuales de un nombre de datos de Pandas.
  - Seleccione filas enteras o columnas enteras desde un nombre de datos.
  - Seleccione un subconjunto de filas y columnas de un nombre de fecha en una sola operación.
  - Seleccione un subconjunto de un nombre de fecha según un único criterio booleano.
- Desafíos: 15 min
  - Escribe una expresión para encontrar el PIB de Per Capita de Serbia en 2007.
  - ¿Qué regla rige lo que está (o no) incluido en rebanadas numéricas y denominadas en Pandas?
  - ¿Qué hace cada línea en el siguiente programa corto?
  - ¿Qué hacen `idxmin` y `idxmax`?
  - Escribe expresiones para obtener el PIB per cápita para todos los países en 1982,
    para todos los países _después_ de 1985,
    , etc.
  - Dada la forma en que sus fronteras han cambiado desde 1900,
    ¿qué harías si se le pidiera crear una tabla de PIB per cápita para Polonia
    para el siglo XX?

### [Plotting](../episodes/09-plotting.md) (11:45)

- Enseñando: 15 min
  - Crear una gráfica de serie de tiempo que muestre un único conjunto de datos.
  - Crea un diagrama de dispersión mostrando la relación entre dos conjuntos de datos.
- Ejercicio: 15 min
  - Llene los espacios en blanco para conspirar el PIB mínimo per cápita en el tiempo para los países europeos.
  - Modificar el ejemplo para crear una trama dispersión del PIB per cápita en los países asiáticos.
  - Explicar lo que hace cada argumento a `plot` en el siguiente ejemplo.

### [Lunch](../episodes/10-almuerzo.md) (12:15): 45 min

### [Lists](../episodes/11-lists.md) (13:00)

- Enseñando: 10 min
  - Explicar por qué los programas necesitan colecciones de valores.
  - Escribe programas que crean listas planas, los indizan, los rebanan y los modifican mediante llamadas de asignación y métodos.
- Desafíos: 10 min
  - Rellena los espacios en blanco para que el programa produzca la salida que se muestra.
  - ¿Cuán grandes son las siguientes rebanadas?
  - ¿Qué imprimen las expresiones negativas del índice?
  - ¿Qué hace un "paso" en una rebanada?
  - ¿Cómo tratan las rebanadas fuera de los límites?
  - ¿Cuáles son las diferencias entre ordenar estas dos vías?
  - ¿Cuál es la diferencia entre `new = old` y `new = old[:]`?

### [Loops](../episodes/12-for-loops.md) (13:20)

- Enseñando: 10 min
  - Explicar para qué bucles se utilizan normalmente.
  - Traza la ejecución de un bucle simple (sin anidado) y indica correctamente los valores de las variables en cada iteración.
  - Escribe para bucles que utilicen el patrón de Acumulador para añadir valores.
- Desafíos: 15 min
  - ¿Es un error de sangría un error de sintaxis o un error de ejecución?
  - Rastrear qué líneas de este programa se ejecutan en qué orden.
  - Rellena los espacios en blanco de este programa para que revierta una cadena.
  - Rellena los espacios en blanco en esta serie de ejemplos para obtener valores acumulados en la práctica.
  - Reordenar e indentar estas líneas para calcular la suma acumulada de los valores de la lista.

### [Conjunto de datos sobre looping](13-looping-data-sets) (13:45)

- Enseñando: 5 min
  - Ser capaz de leer y escribir expresiones de globo que coincidan con conjuntos de archivos.
  - Utilice glob para crear listas de archivos.
  - Escribe los bucles para realizar operaciones sobre archivos dados sus nombres en una lista.
- Desafíos: 10 min
  - ¿Qué nombres de archivo _no_ coinciden con esta expresión glob?
  - Modificar este programa para que imprima el número de registros en el archivo más corto.
  - Escriba un programa que lea y trace todos los conjuntos de datos regionales.

### [Funciones de escritura](14-writing-functions) (14:00)

- Enseñando: 10 min
  - Explicar e identificar la diferencia entre la definición de la función y la llamada a la función.
  - Escriba una función que tome un pequeño número fijo de argumentos y produzca un único resultado.
- Desafíos: 15 min
  - Este código define y llama a una función - ¿qué se imprime cuando se ejecuta?
  - Explique por qué este programa corto imprime las cosas en el orden que hace.
  - Rellene los espacios en blanco para crear una función que encuentre el valor mínimo en un archivo de datos.
  - Rellena los espacios en blanco para crear una función que encuentra el primer valor negativo en una lista.
    ¿Qué hace su función si la lista está vacía?
  - ¿Por qué a veces es útil pasar argumentos nombrando los parámetros correspondientes?
  - Rellena los espacios en blanco y convierte esta pequeña pieza de código en una función.

### [Ámbito variable](15-scope) (14:25)

- Enseñando: 10 min
  - Identificar variables locales y globales.
  - Identificar parámetros como variables locales.
  - Lee un traceback y determina el archivo, función y número de línea en el que se produjo el error.
- Desafíos: 10 min
  - Rastrear los cambios a los valores de este programa,
    tener cuidado de distinguir los valores locales de los globales.

### [Coffee](16-café) (14:45): 15 min

### [Conditionals](17 condicionales) (15:00)

- Enseñando: 10 min
  - Escribir correctamente los programas que usan sentencias si y si no, y expresiones booleanas simples (sin operadores lógicos).
  - Traza la ejecución de condicionales no anidados dentro de bucles.
- Desafíos: 15 min
  - Seguimiento de la ejecución de esta declaración condicional.
  - Rellena los espacios en blanco para que esta función reemplace los valores negativos con ceros.
  - Modificar este programa para que sólo procese archivos con menos de 50 registros.
  - Modifique este programa para que siempre encuentre los valores más grandes y pequeños en una lista
    sin importar cuáles sean los valores de la lista.

### [Estilo de programación](../episodes/18-style.md) (15:25)

- Enseñando: 15 min
  - ¿Cómo puedo hacer mis programas más legibles?
  - ¿Cómo formatean la mayoría de programadores su código?
  - ¿Cómo pueden los programas comprobar su propia operación?
- Desafíos: 15 min
  - ¿Qué líneas de este código estarán disponibles como ayuda en línea?
  - Convierte los comentarios en este programa en docstrings.
  - Reescribir este corto programa para ser más legible.

### [Wrap-Up](../episodes/19-wrap.md) (15:55)

- Enseñando: 20 min
  - Nombrar y localizar sitios de la comunidad científica de Python para software, talleres y ayuda.
- Desafíos: 0 min
  - Ninguno.

### [Feedback](../episodes/20-feedback.md) (16:15)

- Enseñando: 0 min
- Desafíos: 15 min
  - Recoger comentarios

### Finalizar (16:30)
