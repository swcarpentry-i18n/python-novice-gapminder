---
title: Ejecutando y Saliendo
teaching: 15
exercises: 0
---

::::::::::::::::::::::::::::::::::::::::::::::::::: objetivos

- Inicie el servidor JupyterLab.
- Create a new Python script.
- Crear un cuaderno de Jupyter.
- Apague el servidor de JupyterLab.
- Entender la diferencia entre un script Python y un cuaderno de Jupyter.
- Crear celdas de Markdown en un cuaderno.
- Crear y ejecutar celdas de Python en un cuaderno.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::::: preguntas

- ¿Cómo puedo ejecutar programas Python?

::::::::::::::::::::::::::::::::::::::::::::::::::

Para ejecutar Python, vamos a usar \[Jupyter Notebooks]\[jupyter] vía [JupyterLab][jupyterlab] para el resto de este taller. Las notebooks de Jupyter son comunes en la ciencia de datos y la visualización y sirven como una experiencia conveniente de denominador común para ejecutar el código de Python de forma interactiva donde podemos ver y compartir fácilmente los resultados de nuestro código de Python.

Hay otras formas de editar, administrar y ejecutar código. Los desarrolladores de software a menudo usan un entorno de desarrollo integrado (I [PyCharm](https\://www\.jetbrains. om/pycharm/) o [Visual Studio Code](https://code.visualstudio.com/), o editores de texto como Vim o Emacs, para crear y editar sus programas Python. Después de editar y guardar tus programas Python puedes ejecutar esos programas dentro del propio IDE o directamente en la línea de comandos. En contraste, los cuadernos de Jupyter nos permiten ejecutar y ver los resultados de nuestro código de Python inmediatamente dentro del cuaderno.

JupyterLab tiene otras características útiles:

- Puedes fácilmente escribir, editar y copiar y pegar bloques de código.
- La pestaña completa te permite acceder fácilmente a los nombres de las cosas que estás usando
  y aprender más sobre ellas.
- Te permite anotar tu código con enlaces, texto de diferentes tamaños, balas, etc.
  para que sea más accesible para ti y tus colaboradores.
- Te permite mostrar figuras junto al código que las produce
  para contar una historia completa del análisis.

Cada cuaderno contiene una o más celdas que contienen código, texto o imágenes.

## Comenzando con JupyterLab

JupyterLab es un servidor de aplicaciones con una interfaz de usuario web de [Project Jupyter][jupyter] que
permite trabajar con documentos y actividades como cuadernos de Jupyter, editores de texto, terminales,
e incluso componentes personalizados de una manera flexible, integrada y extensa. JupyterLab requiere un navegador
razonablemente actualizado (idealmente una versión actual de Chrome, Safari o Firefox); Internet
Las versiones 9 y siguientes de Explorer _no_ son compatibles.

JupyterLab está incluido como parte de la distribución Anaconda Python. Si aún no has instalado
la distribución de Anaconda Python, mira [las instrucciones de configuración](../learners/setup.md)
para instrucciones de instalación.

En esta lección ejecutaremos JupyterLab localmente en nuestras propias máquinas, por lo que no requerirá una conexión a Internet además de
la conexión inicial para descargar e instalar Anaconda y JupyterLab

- Iniciar el servidor JupyterLab en su máquina
- Utilice un navegador web para abrir una URL local especial que se conecta a su servidor JupyterLab
- El servidor JupyterLab hace el trabajo y el navegador web muestra el resultado
- Escriba el código en el navegador y vea los resultados después de que su servidor JupyterLab haya terminado de ejecutar su código

:::::::::::::::::::::::::::::::::::::::::  callout

## JupyterLab? ¿Qué pasa con los cuadernos de Jupyter?

JupyterLab es la [siguiente etapa en la evolución del Jupyter Notebook](https://jupyterlab.readthedocs.io/es/stable/getting_started/overview.html#overview).
Si tiene experiencia previa trabajando con los cuadernos Jupyter, entonces tendrá una buena idea de lo que puede esperar de JupyterLab.

Los usuarios experimentados de cuadernos Jupyter están interesados en una discusión más detallada de las similitudes y diferencias
entre las interfaces de usuario JupyterLab y Jupyter notebook pueden encontrar más información en la
[documentación de la interfaz de usuario de JupyterLab][jupyterlab-ui].

::::::::::::::::::::::::::::::::::::::::::::::::::

## Iniciando JupyterLab

Puede iniciar el servidor de JupyterLab a través de la línea de comandos o a través de una aplicación llamada
`Anaconda Navigator`. Anaconda Navigator está incluido como parte de la distribución Anaconda Python.

### macOS - Línea de comandos

Para iniciar el servidor JupyterLab necesitará acceder a la línea de comandos a través de la Terminal.
Hay dos maneras de abrir la Terminal en Mac.

1. En su carpeta Aplicaciones, abra Utilities y haga doble clic en Terminal
2. Pulsa <kbd>Comando</kbd> + <kbd>barra espaciadora</kbd> para iniciar Spotlight. Escriba `Terminal` y luego
   haga doble clic en el resultado de búsqueda o presione <kbd>Enter</kbd>

Después de haber iniciado Terminal, escriba el comando para iniciar el servidor JupyterLab.

```bash
$ jupyter lab
```

### Usuarios de Windows - Línea de comandos

Para iniciar el servidor de JupyterLab necesitará acceder al Anaconda Prompt.

Pulsa <kbd>Windows Logo Key</kbd> y busca `Anaconda Prompt`, haz clic en el resultado o presiona intro.

Después de haber lanzado el Anaconda Prompt, escriba el comando:

```bash
$ jupyter lab
```

### Anaconda Navigator

Para iniciar un servidor de JupyterLab desde Anaconda Navigator primero debes [iniciar Anaconda Navigator (haz clic para obtener instrucciones detalladas sobre macOS, Windows y Linux)](https://docs.anaconda.com/free/navigator/getting-started/#navigator-starting-navigator). Puedes buscar Anaconda Navigator a través de Spotlight en macOS (<kbd>Comando</kbd> + <kbd>barra espaciadora</kbd>), la función de búsqueda de Windows (<kbd>Logo Key</kbd>) o abrir una consola de terminal y ejecutar el ejecutable `anaconda-navigator` desde la línea de comandos.

Después de haber lanzado Anaconda Navigator, haga clic en el botón `Launch` debajo de JupyterLab. Puede que necesites
para deslizar hacia abajo para encontrarlo.

Aquí hay una captura de pantalla de una página Anaconda Navigator similar a la que debería abrir en macOS
o Windows.

<p align='center'>
  <img alt="Anaconda Navigator landing page" src="fig/0_anaconda_navigator_landing_page.png" width="750"/>
</p>

Y aquí hay una captura de pantalla de una página de inicio de JupyterLab que debería ser similar a la que se abre en tu navegador web
predeterminado después de iniciar el servidor JupyterLab en macOS o Windows.

<p align='center'>
  <img alt="JupyterLab landing page" src="fig/0_jupyterlab_landing_page.png" width="750"/>
</p>

## La interfaz de JupyterLab

JupyterLab tiene muchas características encontradas en entornos de desarrollo tradicionales integrados (IDEs), pero
se centra en proporcionar bloques de construcción flexibles para computación interactiva y exploratoria.

La [interfaz de JupyterLab][jupyterlab-ui]
consiste en la barra de menú, una barra lateral izquierda colapsable. y el Área principal de trabajo que contiene las pestañas
de documentos y actividades.

### Barra de menú

La Barra de Menú en la parte superior de JupyterLab tiene los menús de nivel superior que exponen varias acciones
disponibles en JupyterLab junto con sus atajos de teclado (en su caso). The following
menus are included by default.

- **Archivo:** Acciones relacionadas con archivos y directorios como _Nuevo_, _Abierto_, _Cerrar_, _Guardar_, etc. El menú _File_ también incluye la acción _Shut Down_ usada para apagar el servidor de JupyterLab.
- **Editar:** Acciones relacionadas con la edición de documentos y otras actividades como _Deshacer_, _Cortar_, _Copiar_, _Pegar_, etc.
- **Ver:** Acciones que alteran la apariencia de JupyterLab.
- **Ejecutar:** Acciones para ejecutar código en diferentes actividades como portátiles y consolas de código (discutido a continuación).
- **Kernel:** Acciones para la gestión de núcleos. Los núcleos de Jupyter se explicarán con más detalle a continuación.
- **Temas:** Una lista de los documentos y actividades abiertos en el área de trabajo principal.
- **Configuración:** Los ajustes comunes de JupyterLab pueden configurarse usando este menú. También hay una opción de _Editor de Configuración Avanzada_ en el menú desplegable que proporciona un control más fino de las opciones de configuración y configuración de JupyterLab.
- **Ayuda:** Una lista de enlaces de ayuda de JupyterLab y del núcleo.

:::::::::::::::::::::::::::::::::::::::::  callout

## Núcleo

El JupyterLab [docs](https://jupyterlab.readthedocs.io/en/stable/user/documents_kernels.html)
define los kernels como "procesos separados iniciados por el servidor que ejecuta tu código en diferentes lenguajes de programación y entornos."
Cuando abrimos un Notebook de Jupyter, que inicia un núcleo - un proceso - que va a ejecutar el código.
En esta lección, usaremos el núcleo de Jupyter ipython que nos permite ejecutar el código de Python 3 interactivamente.

Usar otros [kernels de Jupyter para otros lenguajes de programación](https\://github. om/jupyter/jupyter/wiki/Jupyter-kernels) nos dejaría
escribir y ejecutar código en otros lenguajes de programación en la misma interfaz de JupyterLab, como R, Java, Julia, Ruby, JavaScript, Fortran,
etc.

::::::::::::::::::::::::::::::::::::::::::::::::::

A continuación se proporciona una captura de pantalla de la barra de menú por defecto.

<p align='center'>   <img alt="JupyterLab Menu Bar" src="fig/0_jupyterlab_menu_bar.png" width="750"/>
</p>

### Left Sidebar

La barra lateral izquierda contiene un número de pestañas comúnmente usadas, tal como un navegador de archivos (mostrando el contenido
del directorio donde fue lanzado el servidor JupyterLab), una lista de kernels ejecutando
y terminales, la paleta de comandos, y una lista de pestañas abiertas en el área de trabajo principal. Una captura de pantalla de
la barra lateral izquierda por defecto se proporciona a continuación.

<p align='center'>   <img alt="JupyterLab Left Side Bar" src="fig/0_jupyterlab_left_side_bar.png" width="250"/>
</p>

La barra lateral izquierda puede colapsarse o expandirse seleccionando "Mostrar barra lateral izquierda" en el menú Ver o
haciendo clic en la pestaña lateral activa.

### Área principal de trabajo

El área de trabajo principal en JupyterLab le permite organizar documentos (cuadernos, archivos de texto, etc.)
y otras actividades (terminales, consolas de código, etc.) into panels of tabs that can be resized or
subdivided. A continuación se proporciona una captura de pantalla de la zona principal de trabajo por defecto.

Si no ve la ficha Launcher, haga clic en el signo azul más debajo de los menús "Archivo" y "Editar" y aparecerá.

<p align='center'>   <img alt="JupyterLab Main Work Area" src="fig/0_jupyterlab_main_work_area.png" width="750"/>
</p>

Arrastre una pestaña al centro de un panel para mover la pestaña al panel. Subdivide un panel de pestañas por
arrastrando una pestaña a la izquierda, derecha, superior o inferior del panel. El área de trabajo tiene una única actividad
actual. La pestaña para la actividad actual está marcada con un borde superior coloreado (azul por defecto).

## Creando un script Python

- Para comenzar a escribir un nuevo programa de Python haga clic en el icono de Archivo de Texto debajo de la cabecera _Otro_ en la pestaña Launcher del Área de Trabajo Principal.
  - También puede crear un nuevo archivo de texto plano seleccionando el _Nuevo -> Archivo de Texto_ en el menú _Archivo_ en la barra de menú.
- Para convertir este archivo de texto plano a un programa Python, seleccione la acción _Guardar archivo com_ del menú _Archivo_ en la barra de menú y dé a su nuevo archivo de texto un nombre que termine con el `. y` extensión.
  - La extensión `.py` permite que todos (incluyendo el sistema operativo) sepan que este archivo de texto es un programa Python.
  - Se trata de un convenio, no de un requisito.

## Crear un Cuaderno de Jupyter

Para abrir un nuevo cuaderno haga clic en el ícono de Python 3 bajo la cabecera _Notebook_ en la pestaña Launcher en
el área de trabajo principal. También puede crear un nuevo cuaderno seleccionando _New -> Notebook_ en el menú _File_ en la barra de menú.

Notas adicionales sobre los cuadernos de Jupyter.

- Los archivos de notas tienen la extensión `.ipynb` para distinguirlos de los programas Python de texto simple.
- Los bloc de notas se pueden exportar como scripts Python que se pueden ejecutar desde la línea de comandos.

A continuación se muestra una captura de pantalla de un cuaderno de Jupyter corriendo dentro de JupyterLab. Si está interesado en
más detalles, vea la [documentación oficial de cuaderno][jupyterlab-notebook-docs].

<p align='center'>   <img alt="Example Jupyter Notebook" src="fig/0_jupyterlab_notebook_screenshot.png" width="750"/>
</p>

:::::::::::::::::::::::::::::::::::::::::  callout

## Cómo se almacena

- El archivo notebook se almacena en un formato llamado JSON.
- Al igual que una página web, lo que se ha guardado se ve diferente de lo que ves en tu navegador.
- Pero este formato permite a Jupyter mezclar código fuente, texto e imágenes, todo en un solo archivo.

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Documentos en Paneles de Pestañas

En el Área principal de Trabajo de JupyterLab puede organizar documentos en paneles de pestañas. Here is an
example from the [official documentation][jupyterlab].

<p align='center'>   <img alt="Multi-panel JupyterLab" src="fig/0_multipanel_jupyterlab_screenshot.png" width="750"/>
</p>

Primero, crea un archivo de texto, consola Python y ventana de terminal y organízalos en tres paneles
en el área de trabajo principal. A continuación, cree un cuaderno, una ventana de terminal y un archivo de texto, y
los organice en tres paneles en el área de trabajo principal. Finalmente, crea tu propia combinación de paneles
y pestañas. ¿Qué combinación de paneles y pestañas cree que será más útil para su flujo de trabajo
?

::::::::::::::::: solución

## Solución

Después de crear las pestañas necesarias, puedes arrastrar una de las pestañas al centro de un panel a
mover la pestaña al panel; a continuación puedes subdividir un panel de pestañas arrastrando una pestaña a la izquierda,
derecha, superior o inferior del panel.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## Código contra texto

Jupyter mezcla código y texto en diferentes tipos de bloques, llamadas celdas. A menudo usamos el término "código"
para significar "el código fuente del software escrito en un lenguaje como Python".
Una "celda de código" en un Cuaderno es una celda que contiene software;
una "celda de texto" es una que contiene una prosa común escrita para seres humanos.

::::::::::::::::::::::::::::::::::::::::::::::::::

## El Cuadro de notas tiene modos Comando y Editando.

- Si presionas <kbd>Esc</kbd> y <kbd>Retornar</kbd> alternativamente, el borde exterior de tu celda de código cambiará de gris a azul.
- Estos son los modos **Command** (gris) y **Edit** (azul) de tu cuaderno.
- El modo Command le permite editar las características a nivel de cuadernos, y el modo Editar cambia el contenido de las celdas.
- En modo Comando (esc/gris),
  - La tecla <kbd>b</kbd> creará una nueva célula debajo de la celda seleccionada actualmente.
  - La tecla <kbd></kbd> hará una arriba.
  - La tecla <kbd>x</kbd> eliminará la celda actual.
  - La tecla <kbd>z</kbd> deshará tu última operación de celda (que podría ser una eliminación, creación, etc.).
- Todas las acciones se pueden hacer usando los menús, pero hay muchos atajos de teclado para acelerar las cosas.

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Comando Vs. Editar

¿En la página de Jupyter notebook está actualmente en modo Comando o Editando?\
Cambiar entre los modos.
Utilice los accesos directos para generar una nueva celda.
Utilice los accesos directos para eliminar una celda.
Utilice los accesos directos para deshacer la última operación de celda que realizó.

::::::::::::::::: solución

## Solución

El modo Command tiene un borde gris y el modo Edit tiene un borde azul.
Usa <kbd>Esc</kbd> y <kbd>Retorna</kbd> para cambiar entre modos.
Tienes que estar en modo Comando (Presco <kbd>Esc</kbd> si tu celda es azul).  Escribe <kbd>b</kbd> o <kbd>a</kbd>.
Tienes que estar en modo Comando (Presco <kbd>Esc</kbd> si tu celda es azul).  Escribe <kbd>x</kbd>.
Tienes que estar en modo Comando (Presco <kbd>Esc</kbd> si tu celda es azul).  Escribe <kbd>z</kbd>.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

### Utilice el teclado y el ratón para seleccionar y editar las celdas.

- Presionando la tecla <kbd>Retorno</kbd> gira el borde azul y activa el modo Edición, lo que le permite a
  escribir dentro de la celda.
- Porque queremos ser capaces de escribir muchas líneas de código en una única célula,
  pulsando la tecla <kbd>Retornar</kbd> cuando en modo Editar (azul) mueve el cursor a la siguiente línea
  en la celda al igual que en un editor de texto.
- Necesitamos otra forma de decirle al Cuaderno que queremos ejecutar lo que hay en la celda.
- Pressing <kbd>Shift</kbd>+<kbd>Return</kbd> together will execute the contents of the cell.
- Ten en cuenta que las teclas <kbd>Devuelve</kbd> y <kbd>Mayús</kbd> a la derecha del teclado están
  justo al lado del otro.

### El Cuaderno de notas convertirá Markdown en documentación impresa en papel.

- Los bloc de notas también pueden renderizar [Markdown][markdown].
  - Un formato simple de texto plano para escribir listas, enlaces,
    y otras cosas que pueden ir a una página web.
  - Equivalentemente, un subconjunto de HTML que se parece a lo que enviarías en un correo electrónico de moda antigua.
- Convierte la célula actual en una célula de Markdown ingresando al modo Comando (<kbd>Esc</kbd>/gris)
  y pulsa la tecla <kbd>M</kbd>.
- `En [ ]:` desaparecerá para mostrar que ya no es una celda de código y podrás escribir
  Markdown.
- Convierte la célula actual en una célula Code ingresando al modo Comando (<kbd>Esc</kbd>/gray) y
  presiona la tecla <kbd>y</kbd>.

### Markdown hace la mayor parte de lo que hace HTML.

<div class="row">

  <div class="col-md-6" markdown="1">

```
* Usa asteriscos
* para crear listas
*.
```

  

  <div class="col-md-6" markdown="1">

- Usar asteriscos
- crear
- listas de balas.

  </div>

</div>

<div class="row">

  <div class="col-md-6" markdown="1">

```
1. Usa los números
1. para crear listas numeradas
1.
```

  

  <div class="col-md-6" markdown="1">

1. Usar números
2. crear
3. listas numeradas.

  

</div>

<div class="row">

  <div class="col-md-6" markdown="1">

```
* Puedes usar sangrías
	* Para crear sub-guiones 
	* del mismo tipo
* O sub-listas
	1. De diferentes tipos
	1.
```

  

  <div class="col-md-6" markdown="1">

- Puedes usar sangrías
  - Crear sublistas
  - del mismo tipo
- O sublistas

  1. De diferentes
  2. tipos

  </div>

</div>

<div class="row">

  <div class="col-md-6" markdown="1">

```
# Un rumbo de Nivel 1
```

  

  <div class="col-md-6" markdown="1">

## Un encabezado de nivel 1

  

</div>

<div class="row">

  <div class="col-md-6" markdown="1">

```
## Rumbo Nivel 2 (etc.)
```

  

  <div class="col-md-6" markdown="1">

## Un Rumbo de Nivel 2 (etc.)

  

</div>

<div class="row">

  <div class="col-md-6" markdown="1">

```
Saltos de línea
no importan.

Pero líneas en blanco
crean nuevos párrafos.
```

  

  <div class="col-md-6" markdown="1">

Saltos de línea
no importan.

Pero las líneas en blanco
crean nuevos párrafos.

  

</div>

<div class="row">

  <div class="col-md-6" markdown="1">

```
[Crear enlaces](http://software-carpentry.org) con `[...](...)`.
O usa [named links][data_carpentry].

[data_carpentry]: http://datacarpentry.org
```

  

  <div class="col-md-6" markdown="1">

[Crear enlaces](https://software-carpentry.org) con `[...](...)`.
O use [named links][data_carpentry].

  

</div>

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Creando listas en Markdown

Crear una lista anidada en una clula de Markdown en un cuaderno que se vea así:

1. Obtener financiación.
2. Trabajar.

- Experiencia de diseño.
- Recopilar datos.
- Analizar.

3. Escribir.
4. Publicar.

::::::::::::::::: solución

## Solución

Este desafío integra tanto la lista numerada como la lista de balas.
Tenga en cuenta que la lista de balas está sangrada 2 espacios para que esté en línea con los elementos de la lista numerada.

```
1. Obtén fondos.
2. Hazlo.
    * experimento de diseño.
    * Recopilar datos.
    * Analizar.
3. Escribir.
4. Publicar.
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Más matemáticas

¿Qué se muestra cuando se ejecuta una celda de Python en un cuaderno
que contiene varios cálculos?
Por ejemplo, ¿qué sucede cuando se ejecuta esta célula?

```python
7 * 3
2 + 1
```

::::::::::::::::: solución

## Solución

Python devuelve la salida del último cálculo.

```python
3
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Cambiar una clula existente de código a Markdown

¿Qué pasa si escribes algún Python en una celda de código
y luego lo cambias a una celda de Markdown?
Por ejemplo,
ponga lo siguiente en una celda de código:

```python
x = 6 * 7 + 12
imprimir(x)
```

Y luego ejecútelo con <kbd>Shift</kbd>+<kbd>Return</kbd> para asegurarse de que funciona como una celda de código.
Ahora vuelve a la celda y usa <kbd>Esc</kbd> luego <kbd>m</kbd> para cambiar la celda a Markdown
y "ejecutarla" con <kbd>Mayús</kbd>+<kbd>Retornar</kbd>.
¿Qué ocurrió y cómo podría ser útil?

::::::::::::::::: solución

## Solución

El código Python es tratado como texto Markdown.
Las líneas parecen formar parte de un párrafo contiguo.
Esto podría ser útil para encender y apagar temporalmente las celdas en los cuadernos que se utilizan para múltiples propósitos.

```python
x = 6 * 7 + 12 imprimir(x)
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Ecuaciones

Markdown estándar (como estamos usando para estas notas) no renderizará ecuaciones,
pero el Cuaderno lo hará.
Crea una nueva célula Markdown
e ingresa lo siguiente:

```
$\sum_{i=1}^{N} 2^{-i} \approx 1$
```

(Probablemente sea más fácil copiar y pegar.)
¿Qué se muestra?
¿Qué crees que el guión bajo, `_`, circumflam, `^`, y el signo de dólares, `$`, hacer?

::::::::::::::::: solución

## Solución

El cuaderno muestra la ecuación ya que sería renderizada desde la sintaxis de ecuación LaTeX.
El signo del dólar, `$`, se utiliza para decirle a Markdown que el texto intermedio es una ecuación de LaTeX.
Si no está familiarizado con LaTeX, underscore, `_`, se utiliza para los suscriptos y circunstancias, `^`, se utiliza para las supercriptas.
Un par de llaves llaves, `{` y `}`, se usa para agrupar texto juntos para que la instrucción `i=1` se convierta en el subíndice y `N` se convierte en el supercripto.
Del mismo modo, `-i` está en llaves para hacer de toda la proposición el superíndice de `2`.
`\sum` y `\approx` son comandos LaTeX para "suma" y símbolos "aproximados".

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

## Cerrando JupyterLab

- En la Barra de Menú seleccione el menú "Archivo" y luego seleccione "Cerrar Abajo" en la parte inferior del menú desplegable. Se le pedirá que confirme que desea apagar el servidor JupyterLab (no olvide guardar su trabajo!). Haga clic en "Cerrar Abajo" para apagar el servidor JupyterLab.
- Para reiniciar el servidor de JupyterLab necesitará volver a ejecutar el siguiente comando desde un shell.

```
$ jupyter lab
```

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Cerrando JupyterLab

Practica cerrar y reiniciar el servidor de JupyterLab.

::::::::::::::::::::::::::::::::::::::::::::::::::

[jupyterlab]: https://jupyterlab.readthedocs.io/es/estable/

[jupyterlab-ui]: https://jupyterlab.readthedocs.io/es/stable/user/interface.html

[jupyterlab-notebook-docs]: https://jupyterlab.readthedocs.io/es/stable/user/notebook.html

[markdown]: https://es.wikipedia.org/wiki/Markdown

[data_carpentry]: https://datacarpentry.org

:::::::::::::::::::::::::::::::::::::::: keypoints

- Los scripts Python son archivos de texto plano.
- Usa el Cuaderno de Jupyter para editar y ejecutar Python.
- El Cuadro de notas tiene modos Comando y Editando.
- Utilice el teclado y el ratón para seleccionar y editar las celdas.
- El Cuaderno de notas convertirá Markdown en documentación impresa en papel.
- Markdown hace la mayor parte de lo que hace HTML.

::::::::::::::::::::::::::::::::::::::::::::::::::
