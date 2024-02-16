---
title: Per Cicli
teaching: 10
exercises: 15
---

::::::::::::::::::::::::::::::::::::::: objectives

- Spiegare che cosa per i cicli sono normalmente utilizzati per.
- Traccia l' esecuzione di un semplice ciclo (non nidificato) e indica correttamente i valori delle variabili in ogni iterazione.
- Scrivi per cicli che usano il modello Accumulatore per aggregare i valori.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::: domande

- Come posso fare un programma fare molte cose?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Un _for loop_ esegue i comandi una volta per ogni valore in una collezione.

- Fare calcoli sui valori in una lista uno per uno
  è doloroso come lavorare con `pressre_001`, `pressre_002`, ecc.
- Un _for loop_ dice a Python di eseguire alcune istruzioni una volta per ogni valore in una lista,
  una stringa di caratteri,
  o qualche altra raccolta.
- "per ogni cosa in questo gruppo, fare queste operazioni"

```python
per il numero in [2, 3, 5]:
    print(number)
```

- Questo ciclo `for` è equivalente a:

```python
print(2)
print(3)
print(5)
```

- E l'output del ciclo `for` è:

```output
2
3
5
```

## Un ciclo `for` è costituito da una collezione, una variabile loop e un corpo.

```python
per il numero in [2, 3, 5]:
    print(number)
```

- La raccolta, `[2, 3, 5]`, è ciò che il ciclo è in esecuzione.
- Il corpo, `print(number)`, specifica cosa fare per ogni valore della collezione.
- La variabile loop, `number`, è ciò che cambia per ogni _iterazione_ del ciclo.
  - La "cosa attuale".

## La prima riga del ciclo `for` deve terminare con un colon, e il corpo deve essere indentato.

- Il colon alla fine della prima riga segnala l'inizio di un _blocco_ di istruzioni.
- Python utilizza l'indentazione invece di `{}` o `begin`/`end` per mostrare _nesting_.
  - Qualsiasi indentazione coerente è legale, ma quasi tutti usano quattro spazi.

```python
per il numero in [2, 3, 5]:
print(number)
```

```error
IndentationError: atteso un blocco rientrato
```

- L'indentazione è sempre significativa in Python.

```python
firstName = "Jon"
  lastName = "Smith"
```

```error
  File "<ipython-input-7-f65f2962bf9c>", riga 2
    lastName = "Smith"
    ^
IndentationError: unexpected indent
```

- Questo errore può essere risolto rimuovendo gli spazi aggiuntivi
  all'inizio della seconda riga.

## Le variabili del ciclo possono essere chiamate qualsiasi cosa.

- Come per tutte le variabili, le variabili di ciclo sono:
  - Creato su richiesta.
  - Insignificante: i loro nomi possono essere qualsiasi cosa.

```python
per gattini in [2, 3, 5]:
    print(kitten)
```

## Il corpo di un ciclo può contenere molte dichiarazioni.

- Ma nessun ciclo dovrebbe essere più di un paio di righe lunghe.
- Difficile per gli esseri umani tenere in mente i più grandi pezzi di codice.

```python
primes = [2, 3, 5]
per p in primes:
    quadrato = p ** 2
    cubed = p ** 3
    print(p, squadrato, cubed)
```

```output
2 4 8
3 9 27
5 25 125
```

## Usa `range` per iterare su una sequenza di numeri.

- La funzione [`range`](https://docs.python.org/3/library/stdtypes.html#range) incorporata produce una sequenza di numeri.
  - _Not_ una lista: i numeri sono prodotti su richiesta
    per rendere il loop su ampie gamme più efficiente.
- `range(N)` è il numero 0..N-1
  - Esattamente gli indici giuridici di un elenco o di una stringa di caratteri di lunghezza N

```python
print('un intervallo non è una lista: range(0, 3)')
per il numero nell'intervallo (0, 3):
    print(number)
```

```output
un intervallo non è una lista: range(0, 3)
0
1
2
```

## Il modello Accumulatore trasforma molti valori in uno.

- Un modello comune nei programmi è:
  1. Inizializza una variabile _accumulator_ a zero, la stringa vuota o la lista vuota.
  2. Aggiorna la variabile con i valori di una raccolta.

```python
# Somma i primi 10 interi.
totale = 0
per il numero nell'intervallo(10):
   totale = totale + (numero + 1)
print(totale)
```

```output
55
```

- Leggi `totale = totale + (numero + 1)` come:
  - Aggiungi 1 al valore corrente della variabile loop `number`.
  - Aggiungi questo al valore corrente della variabile dell'accumulatore `total`.
  - Assegna a `total`, sostituendo il valore corrente.
- Dobbiamo aggiungere `number + 1` perché `range` produce 0..9, non 1..10.

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Classificazione Errori

Un errore di rientro è un errore di sintassi o un errore di runtime?

::::::::::::::: soluzione

## Soluzione

Un IndentationError è un errore di sintassi. I programmi con errori di sintassi non possono essere avviati.
Si avvierà un programma con un errore di runtime ma verrà lanciato un errore in determinate condizioni.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Esecuzione Tracciamento

Crea una tabella che mostra i numeri delle righe che vengono eseguite quando viene eseguito questo programma,
e i valori delle variabili dopo ogni riga viene eseguita.

```python
totale = 0
per il carattere in "stagno":
    totale = totale + 1
```

::::::::::::::: soluzione

## Soluzione

| Linea n. | Variabili                  |
| -------- | -------------------------- |
| 1        | totale = 0                 |
| 2        | totale = 0 caratteri = 't' |
| 3        | totale = 1 carattere = 't' |
| 2        | totale = 1 carattere = 'i' |
| 3        | totale = 2 caratteri = 'i' |
| 2        | totale = 2 caratteri = 'n' |
| 3        | totale = 3 caratteri = 'n' |

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Reversing a String

Riempi gli spazi vuoti nel programma sottostante in modo che stampi "nit"
(il rovescio della stringa di caratteri originale "stagno").

```python
originale = "tin"
risultato = ____
per il carattere in originale:
    risultato = ____
print(result)
```

::::::::::::::: soluzione

## Soluzione

```python
original = "tin"
result = ""
for char in original:
    result = char + result
print(result)
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Accumulazione Pratica

Compila gli spazi vuoti in ciascuno dei programmi sotto
per produrre il risultato indicato.

```python
# Lunghezza totale delle stringhe nella lista: ["rosso", "verde", "blu"] => 12
totale = 0
per parola in ["rosso", "verde", "blu"]:
    ____ = ____ + len(word)
print(totale)
```

::::::::::::::: soluzione

## Soluzione

```python
totale = 0
per la parola in ["rosso", "verde", "blu"]:
    totale = totale + lente (parola)
print(totale)
```

:::::::::::::::::::::::::

```python
# Elenco delle lunghezze delle parole: ["rosso", "verde", "blu"] => [3, 5, 4]
lengths = ____
for word in ["red", "green", "blue"]:
    lengths. ___(____)
print(lengths)
```

::::::::::::::: soluzione

## Soluzione

```python
lengths = []
for word in ["red", "green", "blue"]:
    lengths.append(len(word))
print(lengths)
```

:::::::::::::::::::::::::

```python
# Concatenare tutte le parole: ["red", "green", "blue"] => "redgreenblue"
parole = ["red", "green", "blu"]
risultato = ____
per ____ in ______:
    ____
print(result)
```

::::::::::::::: soluzione

## Soluzione

```python
words = ["red", "green", "blue"]
result = ""
for word in words:
    result = result + word
print(result)
```

:::::::::::::::::::::::::

**Crea un acronimo:** A partire dalla lista `["red", "green", "blue"]`, crea l'acronimo `"RGB"` usando
a for loop.

**Suggerimento:** Potrebbe essere necessario utilizzare un metodo di stringa per formattare correttamente l'acronimo.

::::::::::::::: soluzione

## Soluzione

```python
acronimo = ""
per la parola in ["red", "green", "blue"]:
    acronimo = acronimo + parola[0].upper()
print(acronym)
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Somma Complessiva

Riordinare e riordinare correttamente le righe di codice sotto
in modo da stampare un elenco con la somma cumulativa dei dati.
Il risultato dovrebbe essere `[1, 3, 5, 10]`.

```python
cumulativo. ppend(totale)
per il numero nei dati:
cumulativo = []
totale = totale + numero
totale = 0
print(cumulativo)
dati = [1, ,2,5]
```

::::::::::::::: soluzione

## Soluzione

```python
totale = 0 dati
= [1,2,2, ]
cumulativo = []
per il numero nei dati:
    totale = totale + numero
    cumulativo. ppend(totale)
print(cumulativo)
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Identificare Gli Errori Del Nome Della Variabile

1. Leggere il codice qui sotto e cercare di identificare quali sono gli errori
   _senza_ eseguirlo.
2. Eseguire il codice e leggere il messaggio di errore.
   Che tipo di `NameError` pensi che sia questo?
   È una stringa senza virgolette, una variabile errata o una variabile
   che avrebbe dovuto essere definita ma no?
3. Correggi l'errore.
4. Ripetere i passaggi 2 e 3, finché non si sono risolti tutti gli errori.

```python
for number in range(10):
    # use a if the number is a multiple of 3, altrimenti utilizzare b
    se (Numero % 3) == 0:
        messaggio = messaggio + a
    else:
        messaggio = messaggio + "b"
print(messaggio)
```

::::::::::::::: soluzione

## Soluzione

- I nomi delle variabili Python sono sensibili alle maiuscole e minuscole: `number` e `Number` si riferiscono a variabili diverse.
- La variabile `message` deve essere inizializzata come una stringa vuota.
- Vogliamo aggiungere la stringa `"a"` a `message`, non la variabile \`a non definita.

```python
message = ""
per il numero nell'intervallo(10):
    # use a if the number is a multiple of 3, altrimenti utilizzare b
    se (numero % 3) == 0:
        messaggio = messaggio + "a"
    else:
        messaggio = messaggio + "b"
print(messaggio)
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Errori Dell'Oggetto Identificativo

1. Leggere il codice qui sotto e cercare di identificare quali sono gli errori
   _senza_ eseguirlo.
2. Eseguire il codice e leggere il messaggio di errore. Che tipo di errore è?
3. Correggi l'errore.

```python
stagioni = ['Primavera', 'Estate', 'Autunno', 'Inverno']
print('La mia stagione preferita è ', stagioni[4])
```

::::::::::::::: soluzione

## Soluzione

Questa lista ha 4 elementi e l'indice per accedere all'ultimo elemento della lista è `3`.

```python
stagioni = ['Primavera', 'Estate', 'Autunno', 'Inverno']
print('La mia stagione preferita è ', stagioni[3])
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Un _for loop_ esegue i comandi una volta per ogni valore in una collezione.
- Un ciclo `for` è costituito da una collezione, una variabile loop e un corpo.
- La prima riga del ciclo `for` deve terminare con un colon, e il corpo deve essere indentato.
- L'indentazione è sempre significativa in Python.
- Le variabili Loop possono essere chiamate qualsiasi cosa (ma si consiglia vivamente di avere un nome significativo per la variabile looping).
- Il corpo di un ciclo può contenere molte dichiarazioni.
- Usa `range` per iterare su una sequenza di numeri.
- Il modello Accumulatore trasforma molti valori in uno.

::::::::::::::::::::::::::::::::::::::::::::::::::
