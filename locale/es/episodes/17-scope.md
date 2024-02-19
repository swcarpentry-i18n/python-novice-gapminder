---
title: Alcance variable
teaching: 10
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- Identificar variables locales y globales.
- Identificar parámetros como variables locales.
- Lee un traceback y determina el archivo, función y número de línea en el que ocurrió el error, el tipo de error y el mensaje de error.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::::: preguntas

- ¿Cómo funcionan realmente las llamadas de funciones?
- ¿Cómo puedo determinar dónde ocurrieron los errores?

::::::::::::::::::::::::::::::::::::::::::::::::::

## El alcance de una variable es la parte de un programa que puede 'ver' esa variable.

- Sólo hay tantos nombres sensatos para las variables.
- Las personas que usan funciones no deberían tener que preocuparse por
  qué nombres de variables usa el autor de la función.
- Las personas que escriben funciones no deberían tener que preocuparse por
  qué nombres de variables utiliza el llamador de la función.
- La parte de un programa en el que una variable es visible se llama su \*ámbito \*.

```python
presión = 103.9

ajuste de def (t):
    temperatura = t * 1.43 / presión
    temperatura de retorno
```

- `pressure` es una _variable global_.
  - Definido fuera de cualquier función en particular.
  - Visible en todas partes.
- `t` y `temperature` son _variables locales_ en `ajust`.
  - Definido en la función.
  - No visible en el programa principal.
  - Recuerda: un parámetro de función es una variable
    que se asigna automáticamente un valor cuando se llama a la función.

```python
print('ajustado:', adjust(0.9))
print('temperatura después de la llamada:', temperatura)
```

```output
ajustado: 0.01238691049085659
```

```error
Tracebo (la última llamada más reciente):
  Archivo "/Users/swcarpentry/foo.py", línea 8, en <module>
    print('temperature after call:', temperature)
NameError: nombre 'temperature' no está definido
```

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Uso variable local y global

Traza los valores de todas las variables en este programa mientras se ejecuta.
(Usar '---' como el valor de las variables antes y después de que existan.)

```python
limit = 100

clip def (valor):
    return min(max(0.0, valor), limit)

valor = -22.5
print(clip(valor))
```

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: desafío

## Leyendo mensajes de error

Lee la traza abajo, e identifica lo siguiente:

1. ¿Cuántos niveles tiene la traceback?
2. ¿Cuál es el nombre del archivo donde se produjo el error?
3. ¿Cuál es el nombre de la función donde se produjo el error?
4. ¿En qué número de línea de esta función se produjo el error?
5. ¿Cuál es el tipo de error?
6. ¿Cuál es el mensaje de error?

```error
-------------------------------------------------------------------
KeyError Traceback (última llamada)
<ipython-input-2-e4c4cbafeeb5> en <module>()
      1 error de importación_02
----> 2 errores_02. rint_friday_message()

/Users/ghopper/thesis/code/errors_02. y en print_friday_message()
     13
     14 def print_friday_message():
---> 15 print_message("Viern")

/Users/ghopper/thesis/code/errors_02. y en print_message(day)
      9 "sunday": "Aw, el fin de semana está casi terminado.
     10 }
---> 11 print(messages[day])
     12
     13

KeyError: 'Viernes'
```

::::::::::::::::: solución

## Solución

1. Tres niveles.

2. `errors_02.py`

3. `print_message`

4. Línea 11

5. `KeyError`. Estos errores ocurren cuando estamos intentando buscar una clave que no existe (normalmente en una estructura
   de datos como un diccionario). Podemos encontrar más información sobre `KeyError` y otras excepciones incorporadas
   en la [documentación de Python](https://docs.python.org/3/library/exceptions.html#KeyError).

6. `KeyError: 'Viernes'`

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- El alcance de una variable es la parte de un programa que puede 'ver' esa variable.

::::::::::::::::::::::::::::::::::::::::::::::::::
