---
title: Ambito Variabile
teaching: 10
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- Identificare le variabili locali e globali.
- Identificare i parametri come variabili locali.
- Leggi una traceback e determina il file, la funzione e il numero di riga su cui si è verificato l'errore, il tipo di errore e il messaggio di errore.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::: domande

- Come funzionano effettivamente le chiamate funzionali?
- Come posso determinare dove si sono verificati errori?

::::::::::::::::::::::::::::::::::::::::::::::::::

## La portata di una variabile è la parte di un programma che può 'vedere' quella variabile.

- Ci sono solo così tanti nomi sensibili per le variabili.
- Le persone che usano le funzioni non dovrebbero preoccuparsi di
  quale variabile chiama l'autore della funzione utilizzata.
- Le persone che scrivono le funzioni non dovrebbero preoccuparsi di
  quale variabile chiama il chiamante della funzione.
- La parte di un programma in cui è visibile una variabile è chiamata il suo _campo di applicazione_.

```python
pressione = 103,9

def adjust(t):
    temperatura = t * 1,43 / pressione
    temperatura di ritorno
```

- `pressure` è una _variabile globale_.
  - Definito al di fuori di qualsiasi particolare funzione.
  - Visibile ovunque.
- `t` e `temperature` sono _variabili locali_ in `adjust`.
  - Definito nella funzione.
  - Non visibile nel programma principale.
  - Ricorda: un parametro funzione è una variabile
    a cui viene assegnato automaticamente un valore quando viene chiamata la funzione.

```python
print('adjusted:', adjust(0.9))
print('temperature after call:', temperatura)
```

```output
corretto: 0,01238691049085659
```

```error
Traceback (ultima chiamata):
  File "/Users/swcarpentry/foo.py", riga 8, in <module>
    print('temperature after call:', temperature)
NameError: name 'temperature' non è definito
```

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Uso variabile locale e globale

Traccia i valori di tutte le variabili di questo programma come viene eseguito.
(Usi '---' come valore delle variabili prima e dopo che esistono.)

```python
limit = 100

def clip(value):
    return min(max(0.0, value), limit)

value = -22.5
print(clip(value))
```

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Lettura Messaggi Di Errore

Leggere il traceback qui sotto e identificare quanto segue:

1. Quanti livelli ha la traceback?
2. Qual è il nome del file in cui si è verificato l'errore?
3. Qual è il nome della funzione in cui si è verificato l'errore?
4. Su quale numero di riga in questa funzione si è verificato l'errore?
5. Qual è il tipo di errore?
6. Qual è il messaggio di errore?

```error
-----------------------------------------------------------------------------------
KeyError Traceback (most recent call last)
<ipython-input-2-e4c4cbafeeb5> in <module>()
      1 import errors_02
----> 2 errors_02. rint_friday_message()

/Users/ghopper/thesis/code/errors_02. y in print_friday_message()
     13
     14 def print_friday_message():
---> 15 print_message("Friday")

/Users/ghopper/thesis/code/errors_02. y in print_message(day)
      9 "sunday": "Aw, il fine settimana è quasi finito.
     10 }
---> 11 print(messages[day])
     12
     13

KeyError: 'Venerdì'
```

::::::::::::::: soluzione

## Soluzione

1. Tre livelli.

2. `errors_02.py`

3. `print_message`

4. Linea 11

5. `KeyError`. Questi errori si verificano quando stiamo cercando di cercare una chiave che non esiste (di solito in una struttura di dati
   come un dizionario). Possiamo trovare maggiori informazioni su `KeyError` e altre eccezioni
   integrate nel [Python docs](https://docs.python.org/3/library/exceptions.html#KeyError).

6. `KeyError: 'Venerdì'`

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- La portata di una variabile è la parte di un programma che può 'vedere' quella variabile.

::::::::::::::::::::::::::::::::::::::::::::::::::
