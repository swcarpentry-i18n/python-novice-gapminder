---
title: Variabili e Assegnazione
teaching: 10
exercises: 10
---

::::::::::::::::::::::::::::::::::::::::::::::: obiettivi

- Scrivi programmi che assegnano valori scalari alle variabili ed eseguono calcoli con questi valori.
- Tracciare correttamente i cambiamenti di valore nei programmi che utilizzano l'assegnazione scalare.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::: domande

- Come posso memorizzare i dati nei programmi?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Usa le variabili per memorizzare i valori.

- **Le variabili** sono nomi per valori.

- Denominazione della variabile

  - può **solo** contenere lettere, cifre e underscore `_` (tipicamente usato per separare le parole nei nomi delle variabili lunghe)
  - non è possibile iniziare con una cifra
  - sono **maiuscole e minuscole** (età, età ed età sono tre variabili diverse)

- Il nome dovrebbe anche essere significativo in modo che tu o un altro programmatore sappia cosa è

- I nomi delle variabili che iniziano con sottolineature come `__alistairs_real_age` hanno un significato speciale
  quindi non lo faremo fino a quando non capiremo la convenzione.

- In Python il simbolo `=` assegna il valore a destra al nome a sinistra.

- La variabile viene creata quando viene assegnato un valore.

- Qui Python assegna un'età a una variabile `age`
  e un nome tra virgolette a una variabile `first_name`.

  ```python
  età = 42
  first_name = 'Ahmed'
  ```

## Usa `print` per visualizzare i valori.

- Python ha una funzione integrata chiamata `print` che stampa cose come testo.
- Chiamare la funzione (cioè dire a Python di eseguirla) usando il suo nome.
- Fornire valori alla funzione (cioè le cose da stampare) tra parentesi.
- Per aggiungere una stringa alla stampa, avvolgere la stringa in virgolette singole o doppie.
- I valori passati alla funzione sono chiamati **argomenti**

```python
print(first_name, 'is', age, 'years old')
```

```output
Ahmed ha 42 anni
```

- `print` mette automaticamente uno spazio singolo tra gli oggetti per separarli.
- E si avvolge a una nuova linea alla fine.

## Le variabili devono essere create prima di essere utilizzate.

- Se una variabile non esiste ancora, o se il nome è stato erroneamente,
  Python segnala un errore. (Diversamente da alcune lingue, che "indovina" un valore predefinito.)

```python
print(last_name)
```

```error
---------------------------------------------------------------------------
NameError Traceback (most recent call last)
<ipython-input-1-c1fbb4e96102> in <module>()
----> 1 print(last_name)

NameError: name 'last_name' non è definito
```

- L'ultima riga di un messaggio di errore è di solito la più informativa.
- Vedremo in dettaglio i messaggi di errore [later](17-scope.md#reading-error-messages).

:::::::::::::::::::::::::::::::::::::::::  callout

## Variabili Persistere Tra Le Celle

Essere consapevoli che è il \*ordine \* di esecuzione delle celle che è importante in un notebook di Giove, non l'ordine
in cui appaiono. Python ricorderà _tutti_ il codice che è stato eseguito in precedenza, incluse tutte le variabili che hai definito
, indipendentemente dall'ordine nel notebook. Pertanto, se definisci le variabili più in basso nel taccuino e poi le celle
(ri)run più in alto, quelle definite più in basso saranno ancora presenti. Ad esempio, crea due celle con il seguente contenuto
, in questo ordine:

```python
print(myval)
```

```python
myval = 1
```

Se lo esegui in ordine, la prima cella darà un errore. Tuttavia, se esegui la prima cella _dopo_ la seconda cella
stamperà `1`. Per evitare confusione, può essere utile usare l'opzione `Kernel` -> `Restart & Run All` che
cancella l'interprete ed esegue tutto da un'ardesia pulita che va in alto in basso.

::::::::::::::::::::::::::::::::::::::::::::::::::

## Le variabili possono essere utilizzate nei calcoli.

- Possiamo usare variabili nei calcoli come se fossero valori.
  - Ricorda, abbiamo assegnato il valore `42` a `age` alcune righe fa.

```python
età = età + 3
print('Età in tre anni:', età)
```

```output
Età in tre anni: 45
```

## Usa un indice per ottenere un singolo carattere da una stringa.

- I caratteri (singole lettere, numeri e così via) in una stringa sono
  ordinati. Per esempio, la stringa `'AB'` non è la stessa di `'BA'`. A causa di
  questo ordinamento, possiamo trattare la stringa come una lista di caratteri.
- Ogni posizione nella stringa (primo, secondo, ecc.) è dato un numero. Questo numero
  è chiamato un **indice** o a volte un abbonamento.
- Gli indici sono numerati da 0.
- Usa l'indice della posizione tra parentesi quadre per ottenere il carattere in quella posizione
  .

![Una riga di codice Python, print(atom_name[0]), dimostra che utilizzando l'indice zero verrà visualizzata solo la lettera iniziale, in questo caso 'h' per elio. (fig/2_indexing.svg)

```python
atom_name = 'helium'
print(atom_name[0])
```

```output
h
```

## Usa una fetta per ottenere una substrato

- Una parte di una stringa è chiamata una **sottostringa**. Una sottostringa può essere corta come un singolo carattere
  .
- Un elemento in una lista è chiamato un elemento. Whenever we treat a string as if it
  were a list, the string's elements are its individual characters.
- Una fetta è una parte di una stringa (o, più in generale, una parte di qualsiasi cosa simil-lista).
- Prendiamo una fetta con la notazione `[start:stop]`, dove `start` è l'indice intero
  del primo elemento che vogliamo e `stop` è l'indice intero di
  l'elemento _subito dopo_ l'ultimo elemento che vogliamo.
- La differenza tra `stop` e `start` è la lunghezza della fetta.
- Prendendo una fetta non cambia il contenuto della stringa originale. Invece,
  prendere una fetta restituisce una copia di parte della stringa originale.

```python
atom_name = 'sodium'
print(atom_name[0:3])
```

```output
sod
```

## Usa la funzione `len` integrata per trovare la lunghezza di una stringa.

```python
print(len('helium'))
```

```output
6
```

- Le funzioni annidate sono valutate dall'interno,
  come nella matematica.

## Python è sensibile all'uso di maiuscolo/minuscolo.

- Python pensa che le lettere maiuscole e minuscole siano diverse,
  quindi `Name` e `name` sono variabili diverse.
- Ci sono convenzioni per usare lettere maiuscole all'inizio dei nomi delle variabili, quindi useremo lettere minuscole per ora.

## Usa nomi di variabili significativi.

- Python non si preoccupa di quello che chiami variabili finché obbediscono alle regole
  (caratteri alfanumerici e underscore).

```python
flabadab = 42
ewr_422_yY = 'Ahmed'
print(ewr_422_yY, 'is', flabadab, 'years old')
```

- Utilizzare nomi di variabili significativi per aiutare altre persone a capire cosa fa il programma.
- La più importante "altra persona" è il tuo futuro se stesso.

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Valori Di Swapping

Compila la tabella che mostra i valori delle variabili in questo programma
_dopo_ ogni istruzione viene eseguita.

```python
# Comando # Valore di x # Valore di y # Valore di swap #
x = 1. # # # #
y = 3. # # # #
swap = x # # # #
x = y # # # # #
y = swap # # # # # # #
```

::::::::::::::: soluzione

## Soluzione

```output
# Comando # Valore di x # Valore di y # Valore di swap #
x = 1. # 1. # non definito # non definito #
y = 3. # 1. # 3. # non definito #
swap = x # 1. # 3.0 # 1. #
x = y # 3. # 3.0 # 1. #
y = swap # 3. # 1.0 # 1. #
```

Queste tre righe scambiano i valori in `x` e `y` usando la variabile `swap`
per l'archiviazione temporanea. Questo è un idioma di programmazione abbastanza comune.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Valori Predicazione

Qual è il valore finale di `position` nel programma sottostante?
(Prova a prevedere il valore senza eseguire il programma,
quindi controlla la tua previsione.)

```python
iniziale = 'left'
posizione = iniziale
iniziale = 'destra'
```

::::::::::::::: soluzione

## Soluzione

```python
print(posizione)
```

```output
sinistra
```

Alla variabile `initial` è assegnato il valore `'left'`.
Nella seconda riga, la variabile `position` riceve anche
il valore della stringa `'left'`. Nella terza riga, la variabile `initial` è data al valore
`'right'`, ma la variabile `position` mantiene il suo valore di stringa
di `'left'`.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Sfida

Se assegni `a = 123`,
cosa succede se provi a ottenere la seconda cifra di `a` tramite `a[1]`?

::::::::::::::: soluzione

## Soluzione

I numeri non sono stringhe o sequenze e Python solleverà un errore se si tenta di eseguire un'operazione indice su un numero
. Nella [prossima lezione sui tipi e sulla conversione di tipo](03-types-conversion.md)
impareremo di più sui tipi e su come convertire tra tipi diversi. Se vuoi la nona cifra di un numero che
puoi convertire in una stringa usando la funzione `str` integrata e quindi eseguire un'operazione di indice su quella stringa.

```python
a = 123
print(a[1])
```

```error
TypeError: 'int' object is not subscriptable
```

```python
a = str(123)
print(a[1])
```

```output
2
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Scegliere un nome

Quale è un nome di variabile migliore, `m`, `min`, o `minuti`?
Perché?
Suggerimento: pensa al codice che preferisci ereditare
da qualcuno che sta uscendo dal laboratorio:

1. `ts = m * 60 + s`
2. `tot_sec = min * 60 + sec`
3. `total_seconds = minuti * 60 + secondi`

::::::::::::::: soluzione

## Soluzione

`minutes` è meglio perché `min` potrebbe significare qualcosa come "minimo"
(e in realtà è una funzione integrata esistente in Python che copriremo più tardi).

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Pratica di affettamento

Cosa stampa il seguente programma?

```python
atom_name = 'carbon'
print('atom_name[1:3] è:', atom_name[1:3])
```

::::::::::::::: soluzione

## Soluzione

```output
nome_atomo[1:3] è: ar
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Concetti di leccare

Data la seguente stringa:

```python
species_name = "Acacia buxifolia"
```

Che cosa tornerebbero queste espressioni?

1. `species_name[2:8]`
2. `species_name[11:]` (senza un valore dopo il colon)
3. `species_name[:4]` (senza un valore prima del colon)
4. `species_name[:]` (solo un colon)
5. `species_name[11:-3]`
6. `species_name[-5:-3]`
7. Cosa succede quando scegli un valore `stop` che è fuori raggio? (cioè, prova `species_name[0:20]` o `species_name[:103]`)

::::::::::::::: soluzione

## Soluzioni

1. `species_name[2:8]` restituisce la sottostringa `'acia b'`

2. `species_name[11:]` restituisce la sottostringa `'folia'`, dalla posizione 11 alla fine

3. `species_name[:4]` restituisce la sottostringa `'Acac'`, dall'avvio fino alla posizione 4 ma non inclusa

4. `species_name[:]` restituisce l'intera stringa `'Acacia buxifolia'`

5. `species_name[11:-3]` restituisce la sottostringa `'fo'`, dall'undicesima posizione alla terza ultima posizione

6. `species_name[-5:-3]` restituisce anche la sottostringa `'fo'`, dalla quinta ultima posizione alla terza ultima

7. Se una parte della fetta è fuori dall'intervallo, l'operazione non fallisce. `species_name[0:20]` dà lo stesso risultato di `species_name[0:]`, e `species_name[:103]` dà lo stesso risultato di `species_name[:]`

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Usa le variabili per memorizzare i valori.
- Usa `print` per visualizzare i valori.
- Le variabili persistono tra le celle.
- Le variabili devono essere create prima di essere utilizzate.
- Le variabili possono essere utilizzate nei calcoli.
- Usa un indice per ottenere un singolo carattere da una stringa.
- Usa una fetta per ottenere una substrato
- Usa la funzione `len` integrata per trovare la lunghezza di una stringa.
- Python è sensibile all'uso di maiuscolo/minuscolo.
- Usa nomi di variabili significativi.

::::::::::::::::::::::::::::::::::::::::::::::::::
