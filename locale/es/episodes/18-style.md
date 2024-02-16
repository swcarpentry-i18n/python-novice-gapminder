---
title: Estilo de programación
teaching: 15
exercises: 15
---

::::::::::::::::::::::::::::::::::::::: objectives

- Proporcionar justificaciones sólidas para las reglas básicas del estilo de codificación.
- Refactar programas de una página para hacerlos más legibles y justificar los cambios.
- Usar estándares de codificación comunitaria de Python (PEP-8).

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::::: preguntas

- ¿Cómo puedo hacer mis programas más legibles?
- ¿Cómo formatean la mayoría de programadores su código?
- ¿Cómo pueden los programas comprobar su propia operación?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Coding style

Un estilo de codificación consistente ayuda a otros (incluyendo nuestro futuro a sí mismos) a leer y entender código más fácilmente. El código se lee mucho más a menudo de lo que está escrito, y como dice el [Zen de Python](https://www.python.org/dev/peps/pep-0020), "Readability cuenta".
Python propuso un estilo estándar a través de una de sus primeras propuestas de mejora de Python (PEP), [PEP8](https://www.python.org/dev/peps/pep-0008).

Algunos puntos que vale la pena destacar:

- documentar su código y asegurarse de que los supuestos, algoritmos internos, entradas esperadas, salidas esperadas, etc., sean claros
- usar nombres de variables claros y semánticamente significativos
- usar espacio en blanco, _no_ pestañas para sangrar líneas (las pestañas pueden causar problemas en diferentes editores de texto, sistemas operativos y sistemas de control de versiones)

## Sigue el estilo estándar de Python en tu código.

- [PEP8](https\://www\.python. rg/dev/peps/pep-0008):
  una guía de estilo para Python que discute temas tales como cómo nombrar variables,
  cómo sangrar tu código,
  cómo estructurar tus declaraciones `import`,
  , etc.
  Adherir a PEP8 hace más fácil que otros desarrolladores de Python lean y entiendan tu código, y para entender cómo deberían ser sus contribuciones.
- Para comprobar el cumplimiento de tu código PEP8, puedes usar la [aplicación pycodesty](https://pypi.org/project/pycodestyle/) y herramientas como el [formateador de código negro](https\://github. om/psf/black) puede formatear automáticamente tu código para que se ajuste a PEP8 y pycodestyle (un formateador de notebook de Jupyter también existe [Text_black](https://github.com/dnanhkhoa/nb_black)).
- Algunos grupos y organizaciones siguen diferentes pautas de estilo además de PEP8. Por ejemplo, la [guía de estilo de Google en Python](https://google.github.io/styleguide/pyguide.html) hace recomendaciones ligeramente diferentes. Google escribió una aplicación que puede ayudarte a formatear tu código en su estilo o en PEP8 llamado [yapf](https://github.com/google/yapf/).
- Con respecto al estilo de codificación, la clave es _consistencia_. Elige un estilo para tu proyecto PEP8, el estilo de Google, o cualquier otra cosa y hacer todo lo que esté en su mano para asegurarse de que usted y cualquier otra persona con la que esté colaborando con la adherencia. La coherencia dentro de un proyecto es a menudo más impactante que el estilo utilizado en particular. Un estilo consistente hará que su software sea más fácil de leer y entender para los demás y para su yo futuro.

## Utilice las afirmaciones para comprobar si hay errores internos.

Las afirmaciones son un método simple pero poderoso para asegurarse de que el contexto en el que se está ejecutando el código es el que espera.

```python
def calc_bulk_density(masa, volumen):
    '''Regresa densidad a granel seco = masa de polvo / volumen de polvo.'''
    afirmar volumen > 0
    devolver masa / volumen
```

Si la afirmación es `False`, el intérprete de Python plantea una excepción al tiempo de ejecución `AssertionError`. El código fuente de la expresión que falló se mostrará como parte del mensaje de error. Para ignorar las afirmaciones en su código, ejecute el intérprete con el interruptor '-O' (optimizar). Las afirmaciones deben contener sólo comprobaciones simples y nunca cambiar el estado del programa. Por ejemplo, una afirmación nunca debería contener una asignación.

## Utilice docstrings para proporcionar ayuda incorporada.

Si la primera cosa de una función es una cadena de caracteres que no está asignada directamente a una variable, Python lo adjunta a la función, accesible a través de la función de ayuda incorporada. Esta cadena que proporciona documentación también es conocida como _docstring_.

```python
Promedio def (valores):
    "Devuelve el promedio de valores, o Ninguno si no se proporcionan valores.

    si len(valores) == 0:
        return None
    return sum(valores) / len(valores)

ayuda (promedio)
```

```output
Ayuda sobre el promedio de la función en el módulo __main__:

promedio (valores)
    Devuelve el promedio de los valores, o ninguno si no se proporcionan valores.
```

:::::::::::::::::::::::::::::::::::::::::  callout

## Cadenas múltiples

A menudo usa _cadenas multilíneas_ para documentación.
Estos caracteres comienzan y terminan con tres comillas (individuales o dobles)
y terminan con tres caracteres coincidentes.

```python
"""Esta cadena abarca
múltiples líneas.

Las líneas en blanco están permitidas."""
```

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## ¿Qué se mostrará?

Destaca las líneas en el código de abajo que estarán disponibles como ayuda en línea.
¿Hay líneas que deberían estar disponibles, pero no lo estará?
¿Alguna línea producirá un error de sintaxis o un error de ejecución?

```python
"Encuentra la distancia máxima de edición entre varias secuencias."
# Esto encuentra la distancia máxima entre todas las secuencias.

def overall_max(sequences):
    ''''Determinar la distancia total máxima de edición. ''

    más alto = 0
    para la izquierda en secuencias:
        para la derecha en secuencias:
            ''Evitar la secuencia de comprobación contra sí misma. ''
            si se ha ido ! derecha:
                esto = edit_distance(izquierda, derecha)
                más alto = máximo (más alto, esto)

    # Reporte.
    retorno más alto
```

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Documentar esto

Utiliza los comentarios para describir y ayudar a otros a entender las secciones
potencialmente poco intuitivas o líneas individuales de código. They are especially useful to whoever
may need to understand and edit your code in the future, including yourself.

Utilice docstrings para documentar las entradas aceptables y las salidas esperadas de un método
o clase, su propósito, suposiciones y comportamiento previsto. Los documentos se muestran
cuando un usuario invoca el método integrado `help` en tu método o clase.

Convierte el comentario en la siguiente función en una docstring
y comprueba que `help` lo muestre correctamente.

```python
def middle(a, b, c):
    # Return the middle value of three.
    # Assumes the values can actually be compared.
    values = [a, b, c]
    values.sort()
    return values[1]
```

::::::::::::::::: solución

## Solución

```python
def middle(a, b, c):
    '''Return the middle value of three.
    Assumes the values can actually be compared.'''
    values = [a, b, c]
    values.sort()
    return values[1]
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Limpiar este código

1. Lea este breve programa e intente predecir lo que hace.
2. Ejecutarlo: ¿con qué precisión fue su predicción?
3. Actualice el programa para hacerlo más legible.
   Recuerde ejecutarlo después de cada cambio para asegurarse de que su comportamiento no ha cambiado.
4. Compara tu reescritura con la de tu vecino.
   ¿Qué hizo usted?
   ¿Qué hiciste de otra manera, y por qué?

```python
n = 10
s = 'et cetera'
print(s)
i = 0
while i < n:
    # print('at', j)
    new = ''
    for j in range(len(s)):
        left = j-1
        right = (j+1)%len(s)
        if s[left]==s[right]: new = new + '-'
        else: new = new + '*'
    s=''.join(new)
    print(s)
    i += 1
```

::::::::::::::::: solución

## Solución

Esta es una solución.

```python
cadena def (entrada_cadena, iteraciones):
    """
    toma input_string y genera una nueva cadena con -'s y *'s
    correspondiente a caracteres que tienen caracteres idénticos adyacentes
    o no. respectivamente. Itera a través de este procedimiento con las cadenas
    resultantes para el número de iteraciones proporcionadas.
    """
    print(input_string)
    input_string_length = len(input_string)
    old = input_string
    for i in range(iterations):
        new = ''
        # iterar a través de caracteres en la anterior cadena
        for j in range(input_string_length):
            left = j-1
            right = (j+1) % input_string_length # asegurarse de que el índice derecho se envuelve alrededor de
            if old[left] == old[right]:
                new = new + '-'
            else:
                new = new + '*'
        print(new)
        # almacenar nueva cadena como antigua
        viejos = new     

string_machine('et cetera', 10)
```

```output
et cetera
*****-***
----*-*--
---*---*-
--*-*-*-*
**-------
***-----*
--**---**
*****-***
----*-*--
---*---*-
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Sigue el estilo estándar de Python en tu código.
- Utilice docstrings para proporcionar ayuda incorporada.

::::::::::::::::::::::::::::::::::::::::::::::::::
