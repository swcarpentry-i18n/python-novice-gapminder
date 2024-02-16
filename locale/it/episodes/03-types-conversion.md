---
title: Tipi di dati e conversione di tipo
teaching: 10
exercises: 10
---

::::::::::::::::::::::::::::::::::::::::::::::: obiettivi

- Spiega le differenze chiave tra numeri interi e numeri in virgola mobile.
- Spiega le differenze tra numeri e stringhe di caratteri.
- Usa le funzioni integrate per convertire tra numeri interi, numeri in virgola mobile e stringhe.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::: domande

- Quali tipi di dati memorizzano i programmi?
- Come posso convertire un tipo in un altro?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Ogni valore ha un tipo.

- Ogni valore in un programma ha un tipo specifico.
- Intero (`int`): rappresenta numeri interi positivi o negativi come 3 o -512.
- Numero a virgola mobile (`float`): rappresenta numeri reali come 3.14159 o -2.5.
- Stringa di carattere (solitamente chiamata "stringa", `str`): testo.
  - Scritto in virgolette singole o in virgolette doppie (purché corrispondenti).
  - I preventivi non sono stampati quando viene visualizzata la stringa.

## Usa la funzione `type` integrata per trovare il tipo di valore.

- Usa la funzione `type` integrata per scoprire che tipo ha un valore.
- Funziona anche su variabili.
  - Ma ricorda: il _value_ ha il tipo --- la _variabile_ è solo un'etichetta.

```python
print(type(52))
```

```output
<class 'int'>
```

```python
fitness = 'media'
print(type(fitness))
```

```output
<class 'str'>
```

## I tipi controllano quali operazioni (o metodi) possono essere eseguite su un dato valore.

- Il tipo di valore determina ciò che il programma può fare ad esso.

```python
print(5 - 3)
```

```output
2
```

```python
print('hello' - 'h')
```

```error
---------------------------------------------------------------------------
TypeError Traceback (most recent call last)
<ipython-input-2-67f5626a1e07> in <module>()
----> 1 print('hello' - 'h')

TypeError: unsupported operand type(s) for -: 'str' and 'str'
```

## È possibile utilizzare gli operatori "+" e "\*" sulle stringhe.

- Le stringhe di caratteri "Aggiungi" le concatenano.

```python
full_name = 'Ahmed' + ' ' + 'Walsh'
print(full_name)
```

```output
Ahmed Walsh
```

- Moltiplicare una stringa di caratteri per un intero _N_ crea una nuova stringa che consiste di quella stringa di caratteri ripetuta _N_ volte.
  - Dal momento che la moltiplicazione è aggiunta ripetuta.

```python
separator = '=' * 10
print(separator)
```

```output
==========
```

## Le stringhe hanno una lunghezza (ma i numeri non sono).

- La funzione `len` incorporata conta il numero di caratteri in una stringa.

```python
print(len(full_name))
```

```output
11
```

- Ma i numeri non hanno una lunghezza (nemmeno zero).

```python
print(len(52))
```

```error
---------------------------------------------------------------------------
TypeError Traceback (most recent call last)
<ipython-input-3-f769e8e8097d> in <module>()
----> 1 print(len(52))

TypeError: object of type 'int' has no len()
```

## È necessario convertire i numeri in stringhe o viceversa quando si opera su di esse. {#convert-numbers-and-strings}

- Impossibile aggiungere numeri e stringhe.

```python
print(1 + '2')
```

```error
---------------------------------------------------------------------------
TypeError Traceback (most recent call last)
<ipython-input-4-fe4f54a023c6> in <module>()
----> 1 print(1 + '2')

TypeError: unsupported operand type(s) for +: 'int' and 'str'
```

- Non consentito perché è ambiguo: `1 + '2'` dovrebbe essere `3` o `'12'`?
- Alcuni tipi possono essere convertiti in altri tipi utilizzando il nome del tipo come funzione.

```python
print(1 + int('2'))
print(str(1) + '2')
```

```output
3
12
```

## Puoi mescolare interi e galleggianti liberamente nelle operazioni.

- I numeri interi e i numeri a virgola mobile possono essere mescolati in aritmetica.
  - Python 3 converte automaticamente gli interi in float secondo necessità.

```python
print('half is', 1 / 2.0)
print('three squared is', 3.0 ** 2)
```

```output
metà è 0,5
tre quadrati è 9.0
```

## Le variabili cambiano valore solo quando è assegnato qualcosa a loro.

- Se facciamo una cella in un foglio di calcolo dipende da un altro,
  e aggiorna il secondo,
  gli aggiornamenti precedenti automaticamente.
- Questo **non** accade nei linguaggi di programmazione.

```python
variable_one = 1
variable_two = 5 * variable_one
variable_one = 2
print('first is', variable_one, 'and second is', variable_two)
```

```output
il primo è 2 e il secondo è 5
```

- Il computer legge il valore di `variable_one` quando si esegue la moltiplicazione,
  crea un nuovo valore e lo assegna a `variable_two`.
- Successivamente, il valore di `variable_two` è impostato al nuovo valore e _non dipende da `variable_one`_ quindi il suo valore
  non cambia automaticamente quando `variable_one` cambia.

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Frazioni

Che tipo di valore è 3.4?
Come riesci a scoprire?

::::::::::::::: soluzione

## Soluzione

È un numero in virgola mobile (spesso abbreviato "float").
È possibile scoprire utilizzando la funzione `type()`.

```python
print(type(3.4))
```

```output
<class 'float'>
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Conversione Automatica Del Tipo

Che tipo di valore è 3,25 + 4?

::::::::::::::: soluzione

## Soluzione

È un galleggiante: gli interi
vengono automaticamente convertiti in galleggianti se necessario.

```python
risultato = 3.25 + 4
print(risultato, 'is', type(result))
```

```output
7,25 è <class 'float'>
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Scegli un tipo

Quale tipo di valore (numero intero, numero in virgola mobile, o stringa di caratteri)
utilizzeresti per rappresentare ciascuno dei seguenti valori?  Cercate di trovare più di una buona risposta per ogni problema.  Ad esempio, in # 1, quando si contano i giorni con una variabile in virgola mobile hanno più senso che usare un intero?

1. Numero di giorni dall'inizio dell'anno.
2. Tempo trascorso dall'inizio dell'anno fino ad ora in giorni.
3. Numero di serie di un pezzo di attrezzatura di laboratorio.
4. Età del campione di laboratorio
5. Popolazione attuale di una città.
6. Popolazione media di una città nel tempo.

::::::::::::::: soluzione

## Soluzione

Le risposte alle domande sono:

1. Intero, poiché il numero di giorni sarebbe compreso tra 1 e 365.

2. Punto di galleggiamento, poiché sono richiesti giorni frazionati

3. Stringa di caratteri se il numero di serie contiene lettere e numeri, altrimenti interi se il numero di serie è costituito solo da numeri

4. Questo cambierà! Come definisci l'età di un esemplare? giorni interi dalla raccolta (intero)? data e ora (stringa)?

5. Scegli un punto fluttuante per rappresentare la popolazione come grandi aggregati (ad esempio milioni), o interi per rappresentare la popolazione in unità di individui.

6. Numero in virgola mobile, poiché è probabile che una media abbia una parte frazionata.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Tipi Di Divisione

In Python 3, l'operatore `//` esegue la divisione di pavimento interi (numero intero), l'operatore `/` esegue la divisione in virgola mobile
, e l'operatore `%` (o _modulo_) calcola e restituisce il resto dalla divisione intera:

```python
print('5 // 3:', 5 // 3)
print('5 / 3:', 5 / 3)
print('5 % 3:', 5 % 3)
```

```output
5 // 3: 1
5 / 3: 1.666666666666666667
5 % 3: 2
```

Se `num_subjects` è il numero di soggetti che partecipano a uno studio,
e `num_per_survey` è il numero che può partecipare a un singolo sondaggio,
scrive un'espressione che calcola il numero di sondaggi necessari
per raggiungere tutti una volta.

::::::::::::::: soluzione

## Soluzione

Vogliamo il numero minimo di indagini che raggiungono tutti una volta, che è
il valore arrotondato di `num_subjects/ num_per_survey`. Questo è
equivalente a eseguire una divisione di pavimento con `//` e aggiungendo 1. Prima di
la divisione dobbiamo sottrarre 1 dal numero di soggetti per trattare con
il caso in cui `num_subjects` è uniformemente divisibile per `num_per_survey`.

```python
num_subjects = 600
num_per_survey = 42
num_survey = (num_subjects - 1) // num_per_survey + 1

print(num_subjects, 'subjects,', num_per_survey, 'per survey:', num_surveys)
```

```output
600 soggetti, 42 per indagine: 15
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Stringhe a numeri

Laddove ragionevole, `float()` convertirà una stringa in un numero in virgola mobile,
e `int()` convertiranno un numero in virgola mobile in un numero intero:

```python
print("string to float:", float("3.4"))
print("float to int:", int(3.4))
```

```output
stringa da float: 3.4
float to int: 3
```

Se la conversione non ha senso, tuttavia, si verificherà un messaggio di errore.

```python
print("string to float:", float("Ciao mondo!"))
```

```error
---------------------------------------------------------------------------
ValueError Traceback (most recent call last)
<ipython-input-5-df3b790bf0a2> in <module>
----> 1 print("string to float:", float("Ciao mondo! ))

ValueError: impossibile convertire la stringa in float: 'Ciao mondo!'
```

Date queste informazioni, che cosa ti aspetti il seguente programma?

Che cosa fa realmente?

Perché pensi che lo faccia?

```python
print("stringa frazionaria per int:", int("3.4"))
```

::::::::::::::: soluzione

## Soluzione

Cosa ti aspetti che questo programma faccia? Non sarebbe così irragionevole aspettarsi che il comando `int` di Python 3 converti
la stringa "3. " a 3.4 e una conversione di tipo supplementare a 3. Dopo tutto, Python 3 esegue un sacco di altra magia* non è quella parte del suo fascino?

```python
int("3,4")
```

```output
---------------------------------------------------------------------------
ValueError Traceback (most recent call last)
<ipython-input-2-ec6729dfccdc> in <module>
----> 1 int("3. ")
ValoreErrore: letterale non valido per int() con base 10: '3.4'
```

Tuttavia, Python 3 lancia un errore. Perché? Per essere coerenti, possibilmente. Se si chiede a Python di eseguire due tipecast
consecutivi, è necessario convertirlo esplicitamente in codice.

```python
int(float("3.4"))
```

```output
3
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Arithmetic con diversi tipi

Quale di seguito restituirà il numero in virgola mobile `2.0`?
Nota: può esserci più di una risposta corretta.

```python
primo = 1,0
secondo = "1"
terzo = "1,1"
```

1. `first + float(second)`
2. `float(secondo) + float(third)`
3. `first + int(third)`
4. `first + int(float(third))`
5. `int(first) + int(float(third))`
6. `2.0 * secondo`

::::::::::::::: soluzione

## Soluzione

Risposta: 1 e 4

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Numeri Complessi

Python fornisce numeri complessi,
che sono scritti come `1.0+2.0j`.
Se `val` è un numero complesso,
le sue parti reali e immaginarie possono essere accessibili usando _dot notation_
come `val.real` e `val.imag`.

```python
a_complex_number = 6 + 2j
print(a_complex_number.real)
print(a_complex_number.imag)
```

```output
6,0
2,0
```

1. Perché pensi che Python utilizzi `j` invece di `i` per la parte immaginaria?
2. Cosa ti aspetti di produrre `1 + 2j + 3`?
3. Cosa ci si aspetta che sia `4j`?  Che dire di `4 j` o `4 + j`?

::::::::::::::: soluzione

## Soluzione

1. I trattamenti matematici standard usano tipicamente `i` per indicare un numero immaginario. Tuttavia, dai media riporta che
   è stata una prima convenzione stabilita dalla ingegneria elettrica che ora presenta una zona tecnicamente costosa a
   cambiamento. Stack Overflow fornisce ulteriori spiegazioni e discussioni
   .

2. `(4+2j)`

3. `4j` e `Errore di sintassi: sintassi non valida`. In questi ultimi casi, `j` è considerato una variabile e l'istruzione
   dipende da se `j` è definito e in caso affermativo, il suo valore assegnato.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Ogni valore ha un tipo.
- Usa la funzione `type` integrata per trovare il tipo di valore.
- I tipi controllano quali operazioni possono essere fatte sui valori.
- Le stringhe possono essere aggiunte e moltiplicate.
- Le stringhe hanno una lunghezza (ma i numeri non sono).
- È necessario convertire i numeri in stringhe o viceversa quando si opera su di esse.
- Puoi mescolare interi e galleggianti liberamente nelle operazioni.
- Le variabili cambiano valore solo quando è assegnato qualcosa a loro.

::::::::::::::::::::::::::::::::::::::::::::::::::
