---
title: Liste
teaching: 10
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- Spiega perché i programmi hanno bisogno di collezioni di valori.
- Scrivere programmi che creano liste piatte, indicizzarli, tagliarli e modificarli attraverso l'assegnazione e le chiamate di metodo.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::: domande

- Come posso memorizzare più valori?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Una lista memorizza molti valori in una singola struttura.

- Fare calcoli con un centinaio di variabili chiamate `pressure_001`, `pressure_002`, ecc.,
  sarebbe almeno lento come farlo a mano.
- Usa una _list_ per memorizzare insieme molti valori.
  - Contenuto all'interno delle parentesi quadre `[...]`.
  - Valori separati da virgole `,`.
- Usa `len` per scoprire quanti valori sono in una lista.

```python
pressioni = [0,273, 0,275, 0,277, 0,275, 0,276]
print('pressures:', pressure)
print('length:', len(pressures))
```

```output
pressure: [0,273, 0,275, 0,277, 0,275, 0,276]
lunghezza: 5
```

## Usa un indice di un elemento per recuperarlo da una lista.

- Proprio come le stringhe.

```python
print('elemento zero delle pressioni:', pressioni[0])
print('quarto elemento delle pressioni:', pressioni[4])
```

```output
elemento zero delle pressioni: 0.273
quarto elemento delle pressioni: 0.276
```

## I valori delle liste possono essere sostituiti assegnandoli.

- Usa un'espressione indice sulla sinistra dell'assegnazione per sostituire un valore.

```python
pressioni[0] = 0.265
print('pressioni sono ora:', pressioni)
```

```output
la pressione è ora: [0,265, 0,275, 0,277, 0,275, 0,276]
```

## Gli elementi in attesa di una lista lo allungano.

- Usa `list_name.append` per aggiungere elementi alla fine di un elenco.

```python
primes = [2, 3, 5]
print('primes is initially:', primes)
primes.append(7)
print('primes has divente:', primes)
```

```output
primes è inizialmente: [2, 3, 5] I primes
sono diventati: [2, 3, 5, 7]
```

- `append` è un _metodo_ delle liste.
  - Come una funzione, ma legata ad un oggetto particolare.
- Usa `object_name.method_name` per chiamare i metodi.
  - Deliberatamente assomiglia al modo in cui ci riferiamo alle cose in una biblioteca.
- Ci incontreremo altri metodi di liste mentre andremo avanti.
  - Usa `help(list)` per un'anteprima.
- `extend` è simile a `append`, ma permette di combinare due liste.  Per esempio:

```python
teen_primes = [11, 13, 17, 19]
middle_aged_primes = [37, 41, 43, 47]
print('primes is currently:', primes)
primes. xtend(teen_primes)
print('primes has ora become e:', primes)
primes.append(middle_aged_primes)
print('primes has finalmente become e:', primes)
```

```output
primes è attualmente: [2, 3, 5, 7]
primes ora è diventato: [2, 3, 5, 7, 11, 13, 17, 19]
primes è finalmente diventato: [2, 3, 5, 7, 11, 13, 17, 19, [37, 41, 43, 47]]
```

Nota che mentre `extend` mantiene la struttura "piatta" dell'elenco, aggiungere una lista a una lista significa che
l'ultimo elemento in `primes` sarà di per sé una lista, non un numero intero. Le liste possono contenere valori di qualsiasi tipo
; pertanto, sono possibili liste di liste.

## Usa `del` per rimuovere completamente gli elementi da una lista.

- Usiamo `del list_name[index]` per rimuovere un elemento da una lista (nell'esempio, 9 non è un numero primario) e quindi abbreviarlo.
- `del` non è una funzione o un metodo, ma una dichiarazione nella lingua.

```python
primes = [2, 3, 5, 7, 9]
print('primes before remove last item:', primes)
del primes[4]
print('primes after remove last item:', primes)
```

```output
primes prima di rimuovere l'ultimo elemento: [2, 3, 5, 7, 9]
primes dopo aver rimosso l'ultimo elemento: [2, 3, 5, 7]
```

## La lista vuota non contiene valori.

- Usa `[]` da solo per rappresentare una lista che non contiene alcun valore.
  - "Lo zero delle liste."
- Utile come punto di partenza per la raccolta dei valori
  (che vedremo nel [prossimo episodio](12-for-loops.md)).

## Le liste possono contenere valori di tipi diversi.

- Una singola lista può contenere numeri, stringhe e qualsiasi altra cosa.

```python
gol = [1, 'Crea liste.', 2, 'Estrai elementi dalle liste.', 3, 'Modifica liste.']
```

## Le stringhe di caratteri possono essere indicizzate come liste.

- Ottieni singoli caratteri da una stringa di caratteri usando indici tra parentesi quadre.

```python
element = 'carbon'
print('zeroth character:', element[0])
print('third character:', element[3])
```

```output
carattere zerot: c
terzo carattere: b
```

## Le stringhe dei caratteri sono immutabili.

- Non è possibile cambiare i caratteri in una stringa dopo la creazione.
  - _Immutabile_: non può essere modificato dopo la creazione.
  - Al contrario, le liste sono _mutabili_: possono essere modificate al loro posto.
- Python considera la stringa un singolo valore con parti,
  non una raccolta di valori.

```python
elemento[0] = 'C'
```

```error
TypeError: 'str' object does not support item assignment
```

- Le liste e le stringhe di caratteri sono entrambe _collezioni_.

## Indicizzare oltre la fine della collezione è un errore.

- Python segnala un `IndexError` se tentiamo di accedere a un valore che non esiste.
  - Questa è una sorta di [errore di runtime](04-built-in.md).
  - Non può essere rilevato come il codice è analizzato
    perché l'indice potrebbe essere calcolato in base ai dati.

```python
print('99esimo elemento dell'elemento è:', elemento[99])
```

```output
IndexError: index string out of range
```

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Riempi gli spazi vuoti

Riempi gli spazi vuoti in modo che il programma sottostante produca l'output mostrato.

```python
values = ____
values.____(1)
values.____(3)
values.____(5)
print('first time:', values)
values = values[____]
print('second time:', values)
```

```output
prima volta: [1, 3, 5]
seconda volta: [3, 5]
```

::::::::::::::: soluzione

## Soluzione

```python
values = []
values.append(1)
values.append(3)
values.append(5)
print('first time:', values)
values = values[1:]
print('second time:', values)
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Quanto è grande un pidocchio?

Se `start` e `stop` sono entrambi interi non negativi,
quanto tempo è la lista `values[start:stop]`?

::::::::::::::: soluzione

## Soluzione

La lista `values[start:stop]` ha fino agli elementi `stop - start`.  Ad esempio,
`values[1:4]` ha i 3 elementi `values[1]`, `values[2]`, and `values[3]`.
Perché 'fino a'? Come abbiamo visto in [episodio 2](02-variables. d),
se `stop` è maggiore della lunghezza totale della lista `values`,
otterremo ancora una lista indietro ma sarà più breve del previsto.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Dalle stringhe alle liste e indietro

Dato questo:

```python
print('string to list:', list('tin'))
print('list to string:', ''.join(['g', 'o', 'l', 'd']))
```

```output
string to list: ['t', 'i', 'n']
list to string: gold
```

1. Cosa fa `list('some string')`?
2. Cosa genera `'-'.join(['x', 'y', 'z'])`?

::::::::::::::: soluzione

## Soluzione

1. [`list('some string')`](https://docs.python.org/3/library/stdtypes.html#list) converte una stringa in una lista contenente tutti i suoi caratteri.

2. [`join`](https\://docs.python.org/3/library/stdtypes.html#str. oin) restituisce una stringa che è la _concatenazione_
   di ogni elemento di stringa nella lista e aggiunge il separatore tra ogni elemento nella lista. Questo si traduce in
   `x-y-z`. Il separatore tra gli elementi è la stringa che fornisce questo metodo.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Lavorare con la fine

Cosa stampa il seguente programma?

```python
element = 'helium'
print(element[-1])
```

1. Come interpreta Python un indice negativo?
2. Se una lista o una stringa ha elementi N,
   qual è l'indice più negativo che può essere utilizzato in modo sicuro,
   e quale posizione rappresenta quell'indice?
3. Se `values` è un elenco, cosa fa `del valori[-1]`?
4. Come è possibile visualizzare tutti gli elementi tranne gli ultimi senza cambiare `value`?
   (Suggerimento: è necessario combinare affettatura e indicizzazione negativa.)

::::::::::::::: soluzione

## Soluzione

Il programma stampa `m`.

1. Python interpreta un indice negativo come a partire dalla fine (invece di
   a partire dall'inizio).  L'ultimo elemento è `-1`.

2. L'ultimo indice che può essere usato in modo sicuro con un elenco di elementi N è l'elemento
   `-N`, che rappresenta il primo elemento.

3. `del values[-1]` rimuove l'ultimo elemento dalla lista.

4. `values[:-1]`

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Passaggio attraverso una lista

Cosa stampa il seguente programma?

```python
element = 'fluorine'
print(element[::2])
print(element[::-1])
```

1. Se scriviamo una fetta come `low:high:stride`, cosa fa `stride`?
2. Quale espressione selezionerebbe tutti gli oggetti pariteticamente numerati da una collezione?

::::::::::::::: soluzione

## Soluzione

Le stampe del programma

```python
furn
eniroulf
```

1. `stride` è la dimensione del passo del ritaglio.

2. La fetta `1::2` seleziona tutti gli oggetti parita-numerati da una collezione: inizia
   con l'elemento `1` (che è il secondo elemento, dal momento che l'indicizzazione inizia da `0`),
   va avanti fino alla fine (dal momento che non viene dato `end`), e utilizza una dimensione di passo di `2`
   (i. ., seleziona ogni secondo elemento).

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Limiti Della Fetta

Cosa stampa il seguente programma?

```python
element = 'lithium'
print(element[0:20])
print(element[-1:3])
```

::::::::::::::: soluzione

## Soluzione

```output
lithium

```

La prima dichiarazione stampa l'intera stringa, poiché la fetta va oltre la lunghezza totale della stringa.
La seconda istruzione restituisce una stringa vuota, perché la parte va "fuori dai limiti" della stringa.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Ordina e Ordinato

Cosa stampano questi due programmi?
In termini semplici, spiegare la differenza tra `sorted(lettere)` e `letters.sort()`.

```python
# Programma A
letters = list('gold')
result = sorted(letters)
print('letters is', letters, 'and result is', result)
```

```python
# Programma B
letters = list('gold')
result = letters.sort()
print('letters is', letters, 'and result is', result)
```

::::::::::::::: soluzione

## Soluzione

Programma A stampe

```output
letters is ['g', 'o', 'l', 'd'] and result is ['d', 'g', 'l', 'o']
```

Stampe del programma B

```output
letters is ['d', 'g', 'l', 'o'] and result is Nessuno
```

`sorted(lettere)` restituisce una copia ordinata della lista `letters` (la lista originale
`letters` rimane invariata), mentre `letters. ort()` ordina la lista
`letters` nel posto e non restituisce nulla.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Copia (o non)

Cosa stampano questi due programmi?
In termini semplici, spiegare la differenza tra `new = old` e `new = old[:]`.

```python
# Programma A
old = list('gold')
new = old # simple assignment
new[0] = 'D'
print('new is', nuovo, 'e vecchio è', vecchio)
```

```python
# Programma B
old = list('gold')
new = old[:] # assegnando una fetta
new[0] = 'D'
print('new is', nuovo, 'e vecchio è', vecchio)
```

::::::::::::::: soluzione

## Soluzione

Programma A stampe

```output
new is ['D', 'o', 'l', 'd'] and old is ['D', 'o', 'l', 'd']
```

Stampe del programma B

```output
new is ['D', 'o', 'l', 'd'] and old is ['g', 'o', 'l', 'd']
```

`new = old` rende `new` un riferimento alla lista `old`; `new` e `old` punto
verso lo stesso oggetto.

`new = old[:]` tuttavia crea un nuovo oggetto di lista `new` contenente tutti gli elementi
dalla lista `old`; `new` e `old` sono oggetti diversi.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Una lista memorizza molti valori in una singola struttura.
- Usa un indice di un elemento per recuperarlo da una lista.
- I valori delle liste possono essere sostituiti assegnandoli.
- Gli elementi in attesa di una lista lo allungano.
- Usa `del` per rimuovere completamente gli elementi da una lista.
- La lista vuota non contiene valori.
- Le liste possono contenere valori di tipi diversi.
- Le stringhe di caratteri possono essere indicizzate come liste.
- Le stringhe dei caratteri sono immutabili.
- Indicizzare oltre la fine della collezione è un errore.

::::::::::::::::::::::::::::::::::::::::::::::::::
