---
title: Librerie
teaching: 10
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- Spiega quali librerie di software sono e perché i programmatori le creano e le usano.
- Scrivi programmi che importano e utilizzano moduli dalla libreria standard di Python.
- Trovare e leggere la documentazione per la libreria standard interattivamente (nell'interprete) e online.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::: domande

- Come posso usare il software che altre persone hanno scritto?
- Come posso scoprire cosa fa quel software?

::::::::::::::::::::::::::::::::::::::::::::::::::

## La maggior parte del potere di un linguaggio di programmazione è nelle sue biblioteche.

- Una _libreria_ è una raccolta di file (chiamati _moduli_) che contiene funzioni
  da utilizzare da altri programmi.
  - Può anche contenere valori di dati (ad esempio, costanti numeriche) e altre cose.
  - I contenuti della biblioteca dovrebbero essere correlati, ma non c'è modo di applicarlo.
- La \[libreria standard] di Python[stdlib] è una vasta suite di moduli che viene fornita
  con Python stesso.
- Molte librerie aggiuntive sono disponibili da [PyPI][pypi] (il Python Package Index).
- Vedremo più tardi come scrivere nuove biblioteche.

:::::::::::::::::::::::::::::::::::::::::  callout

## Librerie e moduli

Una biblioteca è una raccolta di moduli, ma i termini sono spesso utilizzati in modo intercambiabile
, soprattutto perché molte librerie consistono solo di un singolo modulo
, quindi non preoccuparti se le mescoli.

::::::::::::::::::::::::::::::::::::::::::::::::::

## Un programma deve importare un modulo di libreria prima di utilizzarlo.

- Usa `import` per caricare un modulo libreria nella memoria di un programma.
- Quindi fare riferimento alle cose dal modulo come `module_name.thing_name`.
  - Python usa `.` per significare "parte di".
- Utilizzando `math`, uno dei moduli nella libreria standard:

```python
import math

print('pi is', math.pi)
print('cos(pi) is', math.cos(math.pi))
```

```output
pi è 3.141592653589793
cos(pi) è -1.0
```

- Devi fare riferimento a ogni elemento con il nome del modulo.
  - `math.cos(pi)` non funzionerà: il riferimento a `pi`
    non "inherit" in qualche modo il riferimento della funzione a `math`.

## Usa `help` per conoscere i contenuti di un modulo di libreria.

- Funziona come aiuto per una funzione.

```python
help(matematica)
```

```output
Aiuto sulla matematica del modulo:

NOME
    matematica

MODULO RIFERIMENTO
    http://docs.python. rg/3/library/math

    La seguente documentazione viene generata automaticamente dai file sorgente Python
    . Può essere incompleto, errato o include funzionalità che
    sono considerate dettagli di implementazione e possono variare tra le implementazioni Python
    . In caso di dubbio, consultare il riferimento del modulo nella posizione
    sopra elencata.

DESCRIZIONE
    Questo modulo è sempre disponibile. Fornisce l'accesso alle funzioni matematiche
    definite dallo standard C.

FUNZIONI
    acos(x, /)
        Restituisce il coseno d'arco (misurato in radianti) di x.
<unk> <unk> <unk>
```

## Importa elementi specifici da un modulo di libreria per abbreviare i programmi.

- Usa `da ... import ...` per caricare solo elementi specifici da un modulo di libreria.
- Quindi fare riferimento a loro direttamente senza il nome della libreria come prefisso.

```python
from math import cos, pi

print('cos(pi) is', cos(pi))
```

```output
cos(pi) è -1,0
```

## Crea un alias per un modulo di libreria quando lo importi per accorciare i programmi.

- Usa `import ... come ...` per dare a una libreria un breve _alias_ durante l'importazione.
- Quindi fare riferimento agli elementi nella libreria usando quel nome abbreviato.

```python
import math as m

print('cos(pi) is', m.cos(m.pi))
```

```output
cos(pi) è -1,0
```

- Comunemente usato per le librerie che sono usate frequentemente o hanno nomi lunghi.
  - Ad esempio, la libreria di tracciamento `matplotlib` è spesso aliased come `mpl`.
- Ma può rendere i programmi più difficili da capire,
  dal momento che i lettori devono imparare gli alias del vostro programma.

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Esplorare il modulo di matematica

1. Quale funzione del modulo `math` puoi usare per calcolare una radice quadrata
   _senza_ usando `sqrt`?
2. Dato che la libreria contiene questa funzione, perché esiste `sqrt`?

::::::::::::::: soluzione

## Soluzione

1. Utilizzando `help(math)` vediamo che abbiamo `pow(x,y)` in aggiunta a `sqrt(x)`,
   così potremmo usare `pow(x, 0.5)` per trovare una radice quadrata.

2. La funzione `sqrt(x)` è probabilmente più leggibile di `pow(x, 0.5)` quando
   implementa le equazioni. La leggibilità è una pietra angolare della buona programmazione, quindi
   ha senso fornire una funzione speciale per questo caso specifico comune.

Inoltre, il design della libreria `math` di Python ha la sua origine nello standard C,
che include sia `sqrt(x)` che `pow(x, )`, quindi un po 'della storia
della programmazione sta mostrando nei nomi delle funzioni di Python.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Individuazione del modulo destro

Selezionare un carattere casuale da una stringa:

```python
bases = 'ACTTGCTTGAC'
```

1. Quale modulo [libreria standard][stdlib] potrebbe aiutarti?
2. Quale funzione sceglieresti da quel modulo? Ci sono alternative?
3. Prova a scrivere un programma che utilizza la funzione.

::::::::::::::: soluzione

## Soluzione

Il [modulo casuale][randommod] sembra possa aiutare.

La stringa ha 11 caratteri, ciascuno con un indice di posizione da 0 a 10.
Puoi usare [`random.randrange`](https://docs.python.org/3/library/random.html#random.randrange)
o [`random.randint`](https\://docs.python. rg/3/library/random.html#random.randint) funzioni
per ottenere un numero intero casuale tra 0 e 10, quindi selezionare il carattere `bases` a quell'indice:

```python
from random import randrange

random_index = randrange(len(bases))
print(bases[random_index])
```

o più compattamente:

```python
from random import randrange

print(bases[randrange(len(bases))])
```

Forse hai trovato la funzione [`random.sample`](https://docs.python.org/3/library/random.html#random.sample)?
Permette un po 'meno tipizzazione ma potrebbe essere un po 'più difficile da capire solo leggendo:

```python
dal campione di importazione casuale

print(sample(bases, 1)[0])
```

Nota che questa funzione restituisce un elenco di valori. Impareremo le liste
in [episodio 11](11-lists.md).

La soluzione più semplice e più breve è la funzione [`random.choice`](https://docs.python.org/3/library/random.html#random.choice)
che fa esattamente quello che vogliamo:

```python
from random import choice

print(choice(bases))
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Esempio Di Programmazione Puzzle (Problema Di Parson)

Riorganizzare le seguenti affermazioni in modo che una base di DNA
casuale sia stampata e il suo indice nella stringa.
Non tutte le dichiarazioni potrebbero essere necessarie.  Sentitevi liberi di usare/aggiungere variabili intermedie
.

```python
bases="ACTTGCTTGAC"
import math
import random
___ = random.randrange(n_bases)
___ = len(bases)
print("random base ", bases[___], "base index", ___)
```

::::::::::::::: soluzione

## Soluzione

```python
import math 
import random
bases = "ACTTGCTTGAC" 
n_bases = len(bases)
idx = random. andrange(n_bases)
print("base casuale", basi[idx], "indice base", idx)
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Quando È Disponibile Aiuto?

Quando un collega dei tuoi tipi `help(math)`,
Python segnala un errore:

```error
NameError: il nome 'math' non è definito
```

Che cosa ha dimenticato il suo collega?

::::::::::::::: soluzione

## Soluzione

Importazione del modulo matematico (`import math`)

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Importazione Con Alias

1. Riempi gli spazi vuoti in modo che il programma sotto stampi `90.0`.
2. Riscrittura del programma in modo che utilizzi `import` _senza_ `as`.
3. Quale modulo trovi più facile da leggere?

```python
import math as m
angle = ____.degrees(____.pi / 2)
print(____)
```

::::::::::::::: soluzione

## Soluzione

```python
import math as m
angle = m.degrees(m.pi / 2)
print(angolo)
```

può essere scritto come

```python
import math
angle = math.degrees(math.pi / 2)
print(angolo)
```

Dal momento che hai appena scritto il codice e ne hai familiarità, potresti in realtà
trovare la prima versione più facile da leggere. Ma quando si cerca di leggere un pezzo enorme
di codice scritto da qualcun altro, o quando torna al tuo enorme pezzo
di codice dopo diversi mesi, nomi non abbreviati sono spesso più facili, tranne
dove ci sono chiare convenzioni di abbreviazione.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Ci Sono Molti Modi Per Importare Librerie!

Corrisponde alle seguenti istruzioni di stampa con le chiamate della libreria appropriate.

Comandi di stampa:

1. `print("sin(pi/2) =", sin(pi/2))`
2. `print("sin(pi/2) =", m.sin(m.pi/2))`
3. `print("sin(pi/2) =", math.sin(math.pi/2))`

Chiamate in biblioteca:

1. `from math import sin, pi`
2. `import math`
3. `import math in m`
4. `from math import *`

::::::::::::::: soluzione

## Soluzione

1. La biblioteca chiama 1 e 4. Per fare riferimento direttamente a `sin` e `pi` senza
   il nome della libreria come prefisso, è necessario utilizzare il `from ... import ...`
   statement. Mentre la libreria call 1 importa specificamente le due funzioni
   `sin` e `pi`, la libreria call 4 importa tutte le funzioni nel modulo `math`.
2. Chiamata biblioteca 3. Qui `sin` e `pi` sono riferiti con una libreria abbreviata
   nome `m` invece di `math`. La chiamata 3 della libreria fa esattamente quello usando il file
   `import ... come ...` sintassi - crea un alias per `math` nella forma di
   il nome abbreviato `m`.
3. Chiamata biblioteca 2. Qui `sin` e `pi` sono riferiti con la normale libreria
   nome `math`, quindi basta la chiamata `import ...`.

**Nota:** anche se la chiamata in biblioteca 4 funziona, l'importazione di tutti i nomi da un modulo utilizzando una wildcard
import è [non raccomandato][pep8-imports] in quanto rende non chiari quali nomi dal modulo
sono utilizzati nel codice. In generale è meglio rendere le vostre importazioni il più possibile specifiche e di
importare solo ciò che il codice utilizza. Nella chiamata della libreria 1, la dichiarazione `import` ci dice esplicitamente
che la funzione `sin` viene importata dal modulo `math`, ma la chiamata biblioteca 4 non
trasmette queste informazioni.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Importazione Di Elementi Specifici

1. Riempi gli spazi vuoti in modo che il programma sotto stampi `90.0`.
2. Trovi questa versione più facile da leggere rispetto a quella precedente?
3. Perché i programmatori _non_ usano sempre questa forma di `import`?

```python
____ math import ____, ____
angle = degrees(pi / 2)
print(angolo)
```

::::::::::::::: soluzione

## Soluzione

```python
from math import degrees, pi
angle = degrees(pi / 2)
print(angolo)
```

Molto probabilmente trovi questa versione più facile da leggere dal momento che è meno denso.
Il motivo principale per non utilizzare questa forma di importazione è quello di evitare gli scontri di nome.
Per esempio, non importerai in questo modo `degrees` se volessi anche
usare il nome `degrees` per una variabile o una funzione propria. O se tu
dovessi anche importare una funzione chiamata `degrees` da un'altra libreria.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Lettura Messaggi Di Errore

1. Leggere il codice qui sotto e cercare di identificare quali errori sono senza eseguirlo.
2. Eseguire il codice e leggere il messaggio di errore. Che tipo di errore è?

```python
from math import log
log(0)
```

::::::::::::::: soluzione

## Soluzione

```output
---------------------------------------------------------------------------
ValueError Traceback (most recent call last)
<ipython-input-1-d72e1d780bab> in <module>
      1 from math import log
----> 2 log(0)

ValueError: math domain error
```

1. Il logaritmo di `x` è definito solo per `x > 0`, quindi 0 è al di fuori del dominio
   della funzione.

2. Si ottiene un errore di tipo `ValueError`, indicando che la funzione
   ha ricevuto un valore di argomento inappropriato. Il messaggio aggiuntivo
   "errore di dominio matematico" rende più chiaro quale sia il problema.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

[stdlib]: https://docs.python.org/3/library/

[pypi]: https://pypi.python.org/pypi/

[randommod]: https://docs.python.org/3/library/random.html

[pep8-imports]: https://pep8.org/#import

:::::::::::::::::::::::::::::::::::::::: keypoints

- La maggior parte del potere di un linguaggio di programmazione è nelle sue biblioteche.
- Un programma deve importare un modulo di libreria per poterlo utilizzare.
- Usa `help` per conoscere i contenuti di un modulo di libreria.
- Importa elementi specifici da una libreria per abbreviare i programmi.
- Crea un alias per una libreria quando lo importi per accorciare i programmi.

::::::::::::::::::::::::::::::::::::::::::::::::::
