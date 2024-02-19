---
title: Funzioni integrate e aiuto
teaching: 15
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- Spiegare lo scopo delle funzioni.
- Chiamare correttamente le funzioni Python integrate.
- Nidi correttamente le chiamate alle funzioni integrate.
- Utilizzare l'aiuto per visualizzare la documentazione per le funzioni integrate.
- Descrivere correttamente le situazioni in cui si verificano SyntaxError e NameError.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::: domande

- Come posso usare le funzioni integrate?
- Come posso scoprire cosa fanno?
- Che tipo di errori possono verificarsi nei programmi?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Utilizzare i commenti per aggiungere documentazione ai programmi.

```python
# Questa frase non è eseguita da Python.
regolazione = 0.5 # Né è questa - nulla dopo '#' viene ignorato.
```

## Una funzione può richiedere zero o più argomenti.

- Abbiamo visto alcune funzioni già --- ora diamo un'occhiata più da vicino.
- Un _argomento_ è un valore passato in una funzione.
- `len` ne prende esattamente uno.
- `int`, `str`, e `float` creano un nuovo valore da uno esistente.
- `print` richiede zero o più.
- `print` senza argomenti stampa una riga vuota.
  - Deve sempre usare parentesi, anche se sono vuote,
    in modo che Python sappia che una funzione viene chiamata.

```python
print('before')
print()
print('after')
```

```output
prima di

dopo
```

## Ogni funzione restituisce qualcosa.

- Ogni chiamata di funzione produce qualche risultato.
- Se la funzione non ha un risultato utile per restituire,
  di solito restituisce il valore speciale `None`. `None` è un oggetto Python
  che sta in qualsiasi momento non c'è valore.

```python
result = print('example')
print('result of print is', result)
```

```output
esempio
risultato di stampa non è nessuno
```

## Le funzioni integrate comunemente usate includono `max`, `min`, e `round`.

- Usa `max` per trovare il valore più grande di uno o più valori.
- Usa `min` per trovare il più piccolo.
- Entrambi lavorano su stringhe di caratteri così come i numeri.
  - "Più grandi" e "più piccolo" uso (0-9, A-Z, a-z) per confrontare le lettere.

```python
print(max(1, 2, 3))
print(min('a', 'A', '0'))
```

```output
3
0
```

## Le funzioni possono funzionare solo per alcuni (combinazioni di) argomenti.

- `max` e `min` devono essere forniti almeno un argomento.
  - "Più grande del set vuoto" è una domanda senza senso.
- E devono essere date loro cose che possono essere confrontate in modo significativo.

```python
print(max(1, 'a'))
```

```error
TypeError Traceback (ultima chiamata)
<ipython-input-52-3f049acf3762> in <module>
----> 1 print(max(1, 'a'))

TypeError: '>' non supportato tra istanze di 'str' e 'int'
```

## Le funzioni possono avere valori predefiniti per alcuni argomenti.

- `round` terminerà un numero in virgola mobile.
- Per impostazione predefinita, arrotonda a zero decimali.

```python
round(3.712)
```

```output
4
```

- Possiamo specificare il numero di decimali che vogliamo.

```python
tondo(3.712, 1)
```

```output
3.7
```

## Le funzioni collegate agli oggetti sono chiamate metodi

- Le funzioni assumono un'altra forma che sarà comune negli episodi di panda.
- I metodi hanno parentesi come funzioni, ma vengono dopo la variabile.
- Alcuni metodi sono usati per operazioni interne in Python e sono contrassegnati con doppie sottolineature.

```python
mio_stringa = 'Ciao mondo! # creazione di una stringa object 

print(len(my_string)) # la funzione len prende una stringa come argomento e restituisce la lunghezza della stringa

print(my_string. wapcase()) # chiamare il metodo swapcase sul my_string object

print(my_string.__len__()) # chiamando il metodo interno __len__ sull'oggetto my_string utilizzato da len(my_string)

```

```output
12
HELLO WORLD!
12
```

- Potreste persino vederli incatenati assieme.  Operano da sinistra a destra.

```python
print(my_string.isupper()) # Non tutte le lettere sono maiuscole
print(my_string.upper()) # Questo capitalizza tutte le lettere

print(my_string.upper().isupper()) # Ora tutte le lettere sono maiuscole
```

```output
Falso
HELLO WORLD
Vero
```

## Usa la funzione `help` integrata per ottenere aiuto per una funzione.

- Ogni funzione integrata ha una documentazione online.

```python
help(round)
```

```output
Aiuto sulla funzione integrata round nel modulo integrato:

round(numero, ndigits=Nessuno)
    arrotonda un numero a una data precisione in cifre decimali.
    
    Il valore di ritorno è un numero intero se ndigits è omesso o Nessuno. Altrimenti
    il valore restituito ha lo stesso tipo del numero. ndigits può essere negativo.
```

## Il notebook Jupyter ha due modi per ottenere aiuto.

- Opzione 1: posizionare il cursore vicino a dove la funzione è invocata in una cella
  (cioè, il nome della funzione o i suoi parametri),
  - Tieni premuto <kbd>Maiusc</kbd>e premi <kbd>Tab</kbd>.
  - Fare questo più volte per espandere le informazioni restituite.
- Opzione 2: digitare il nome della funzione in una cella con un punto interrogativo dopo di essa. Quindi eseguire la cella.

## Python segnala un errore di sintassi quando non riesce a capire la fonte di un programma.

- Non cercherà nemmeno di eseguire il programma se non può essere analizzato.

```python
# Hai dimenticato di chiudere le virgolette intorno alla stringa.
name = 'Feng
```

```error
  File "<ipython-input-56-f42768451d55>", linea 2
    name = 'Feng
                ^
SyntaxError: EOL durante la scansione della stringa letterale
```

```python
# Un extra '=' nell'assegnazione.
età = = 52
```

```error
  File "<ipython-input-57-ccc3df3cf902>", linea 2
    età = = 52
          ^
SintassoErrore: sintassi non valida
```

- Guarda più da vicino il messaggio di errore:

```python
print("ciao mondo"
```

```error
  File "<ipython-input-6-d1cc229bf815>", linea 1
    print ("ciao mondo"
                        ^
SyntaxError: unexpected EOF durante l'analisi
```

- Il messaggio indica un problema alla prima riga dell'input ("riga 1").
  - In questo caso la sezione "ipython-input" del nome del file ci dice che
    stiamo lavorando con input in IPython,
    l'interprete Python usato dal Notebook di Giove.
- La parte `-6-` del nome file indica che
  l'errore si è verificato nella cella 6 del nostro notebook.
- Il prossimo è la linea di codice problematica,
  che indica il problema con un puntatore `^`.

## Python segnala un errore di esecuzione quando qualcosa va storto mentre un programma è in esecuzione. {#runtime-error}

```python
age = 53
rimanente = 100 - aege # mis-spelled 'age'
```

```error
NameError Traceback (ultima chiamata)
<ipython-input-59-1214fb6c55fc> in <module>
      1 età = 53
----> 2 rimanenti = 100 - aege # mis-spelled 'age'

NameError: name 'aege' non è definito
```

- Correggere gli errori di sintassi leggendo gli errori di origine e di esecuzione tracciando l'esecuzione.

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Cosa Succede Quando

1. Spiega in termini semplici l'ordine delle operazioni nel seguente programma:
   quando avviene l'aggiunta, quando avviene la sottrazione,
   quando ogni funzione viene chiamata, ecc.
2. Qual è il valore finale di `radiance`?

```python
radianza = 1,0
radianza = max(2.1, 2.0 + min(radianza, 1.1 * radianza - 0.5))
```

::::::::::::::: soluzione

## Soluzione

1. Ordine delle operazioni:

2. `1.1 * radianza = 1.1`

3. `1.1 - 0.5 = 0.6`

4. `min(radianza, 0.6) = 0.6`

5. `2.0 + 0.6 = 2.6`

6. `max(2.1; 2.6) = 2.6`

7. Alla fine, `radianza = 2.6`

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Spot la differenza

1. Prevedere ciò che ciascuna delle istruzioni `print` nel programma qui sotto stampa.
2. Il file `max(len(rich), poor)` viene eseguito o produce un messaggio di errore?
   Se funziona, il suo risultato ha qualche senso?

```python
easy_string = "abc"
print(max(easy_string))
rich = "gold"
poor = "tin"
print(max(rich, poor))
print(max(len(rich), len(poor)))
```

::::::::::::::: soluzione

## Soluzione

```python
print(max(easy_string))
```

```output
c
```

```python
print(max(ricchi, poveri))
```

```output
stagno
```

```python
print(max(len(rich), len(poor)))
```

```output
4
```

`max(len(rich), povero)` lancia un TypeError. Questo si trasforma in `max(4, 'tin')` e
come abbiamo discusso in precedenza una stringa e un intero non possono essere significativamente confrontati.

```error
TypeError Traceback (più recente chiamata ultima)
<ipython-input-65-bc82ad05177a> in <module>
----> 1 max(len(rich), poor)

TypeError: '>' non supportato tra istanze di 'str' e 'int'
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Perché No?

Perché `max` e `min` non restituiscono `None` quando vengono chiamati senza argomenti?

::::::::::::::: soluzione

## Soluzione

`max` e `min` restituiscono TypeErrors in questo caso perché il numero corretto di parametri
non è stato fornito. Se ha appena restituito `Nessuno`, l'errore sarebbe molto più difficile da rintracciare in quanto
probabilmente sarebbe memorizzato in una variabile e utilizzato in seguito nel programma, solo per lanciare probabilmente
un errore di runtime.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Ultimo carattere di una stringa

Se Python inizia a contare da zero,
e `len` restituisce il numero di caratteri in una stringa,
quale espressione indice otterrà l'ultimo carattere nella stringa `name`?
(Nota: vedremo un modo più semplice per farlo in un episodio successivo.)

::::::::::::::: soluzione

## Soluzione

`name[len(name) - 1]`

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## Esplora i documenti di Python!

La [documentazione ufficiale di Python](https://docs.python.org/3/) è probabilmente la fonte di informazioni
più completa sulla lingua. È disponibile in diverse lingue e contiene un sacco di risorse utili
. La [pagina Funzioni integrate](https://docs.python.org/3/library/functions.html) contiene un catalogo di
tutte queste funzioni, comprese quelle che abbiamo coperto in questa lezione. Alcuni di questi sono più avanzati e
inutili al momento, ma altri sono molto semplici e utili.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Utilizzare i commenti per aggiungere documentazione ai programmi.
- Una funzione può richiedere zero o più argomenti.
- Le funzioni integrate comunemente usate includono `max`, `min`, e `round`.
- Le funzioni possono funzionare solo per alcuni (combinazioni di) argomenti.
- Le funzioni possono avere valori predefiniti per alcuni argomenti.
- Usa la funzione `help` integrata per ottenere aiuto per una funzione.
- Il notebook Jupyter ha due modi per ottenere aiuto.
- Ogni funzione restituisce qualcosa.
- Python segnala un errore di sintassi quando non riesce a capire la fonte di un programma.
- Python segnala un errore di esecuzione quando qualcosa va storto mentre un programma è in esecuzione.
- Correggere gli errori di sintassi leggendo il codice sorgente e gli errori di esecuzione tracciando l'esecuzione del programma.

::::::::::::::::::::::::::::::::::::::::::::::::::
