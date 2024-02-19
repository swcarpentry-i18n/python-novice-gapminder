---
title: Stile Di Programmazione
teaching: 15
exercises: 15
---

::::::::::::::::::::::::::::::::::::::: objectives

- Fornire valide giustificazioni per le regole di base dello stile di codifica.
- Refactor one-page programmi per renderli più leggibili e giustificare i cambiamenti.
- Usa gli standard di codifica della comunità Python (PEP-8).

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::: domande

- Come posso rendere i miei programmi più leggibili?
- Come la maggior parte dei programmatori formattano il loro codice?
- Come possono i programmi controllare la propria operazione?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Coding style

Uno stile di codifica coerente aiuta gli altri (compreso il nostro futuro se stessi) a leggere e capire il codice più facilmente. Il codice è letto molto più spesso di quanto sia scritto, e come lo [Zen of Python](https://www.python.org/dev/peps/pep-0020) dichiara, "Readability counts".
Python ha proposto uno stile standard attraverso una delle sue prime proposte di miglioramento Python (PEP), [PEP8](https://www.python.org/dev/peps/pep-0008).

Alcuni punti meritano di essere evidenziati:

- documenta il tuo codice e assicurati che le ipotesi, gli algoritmi interni, gli input attesi, gli output attesi, ecc., siano chiari
- usa nomi di variabili chiari e semanticamente significativi
- utilizzare le schede di spazio bianco, _non_, per indentare le righe (le schede possono causare problemi tra diversi editor di testo, sistemi operativi e sistemi di controllo delle versioni)

## Segui lo stile standard di Python nel tuo codice.

- [PEP8](https\://www\.python. rg/dev/peps/pep-0008):
  una guida di stile per Python che discute argomenti come come il nome delle variabili,
  come inserire il tuo codice,
  come strutturare le tue istruzioni `import`,
  ecc.
  L'adesione a PEP8 rende più facile per gli altri sviluppatori di Python leggere e capire il tuo codice, e per capire come dovrebbero essere i loro contributi.
- Per verificare la conformità del tuo codice con PEP8, puoi utilizzare [pycodestyle application](https://pypi.org/project/pycodestyle/) e strumenti come [black code formatter](https\://github. om/psf/black) può formattare automaticamente il tuo codice in modo da essere conforme a PEP8 e pycodestyle (un formato del notebook di Jupyter esiste anche [nb_black](https://github.com/dnanhkhoa/nb_black)).
- Alcuni gruppi e organizzazioni seguono diverse linee guida di stile oltre a PEP8. Ad esempio, la [guida in stile Google su Python](https://google.github.io/styleguide/pyguide.html) contiene raccomandazioni leggermente diverse. Google ha scritto un'applicazione che può aiutarti a formattare il tuo codice in uno stile o in PEP8 chiamato [yapf](https://github.com/google/yapf/).
- Per quanto riguarda lo stile di codifica, la chiave è _consistenza_. Scegli uno stile per il tuo progetto sia PEP8, lo stile Google, o qualcos'altro e fare del vostro meglio per garantire che tu e chiunque altro si sta collaborando con bastoncini ad esso. La coerenza all'interno di un progetto è spesso più efficace dello stile particolare utilizzato. Uno stile coerente renderà il vostro software più facile da leggere e capire per gli altri e per il vostro futuro se stesso.

## Utilizzare le asserzioni per verificare eventuali errori interni.

Le rappresentazioni sono un metodo semplice ma potente per assicurarsi che il contesto in cui il codice è in esecuzione sia quello che ci si aspetta.

```python
def calc_bulk_density(massa, volume):
    '''Restituisce massa secca = massa in polvere / volume in polvere.'''
    asserisce il volume > 0
    restituisce massa / volume
```

Se l'asserzione è `False`, l'interprete Python solleva un'eccezione di esecuzione `AssertionError`. Il codice sorgente per l'espressione che non è riuscita verrà visualizzato come parte del messaggio di errore. Per ignorare le asserzioni nel tuo codice esegui l'interprete con l'interruttore '-O' (ottimizza). Le rappresentazioni dovrebbero contenere solo controlli semplici e non cambiare mai lo stato del programma. Per esempio, un'affermazione non dovrebbe mai contenere un incarico.

## Usa docstrings per fornire un aiuto integrato.

Se la prima cosa in una funzione è una stringa di caratteri che non è assegnata direttamente a una variabile, Python lo collega alla funzione, accessibile tramite la funzione di aiuto integrata. Questa stringa che fornisce la documentazione è anche conosciuta come _docstring_.

```python
def media(valori):
    "Restituisce la media dei valori, o Nessuno se non vengono forniti valori.

    if len(values) == 0:
        return Nessuno
    return sum(values) / len(values)

help(avere)
```

```output
Aiuto sulla media della funzione nel modulo __main__:

media(valori)
    Restituisce la media dei valori, o Nessuno se non vengono forniti valori.
```

:::::::::::::::::::::::::::::::::::::::::  callout

## Stringhe Multiline

Spesso usa _stringhe multiline_ per la documentazione.
Questi iniziano e terminano con tre caratteri di quotazione (singoli o doppi)
e terminano con tre caratteri corrispondenti.

```python
"""Questa stringa si estende su
linee multiple.

Le righe vuote sono permesse."""
```

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Cosa Verrà Mostrato?

Evidenziare le righe nel codice sottostante che saranno disponibili come aiuto online.
Ci sono linee che dovrebbero essere messe a disposizione, ma non sarà?
Alcune righe produrranno un errore di sintassi o un errore di runtime?

```python
"Trova la distanza massima di modifica tra sequenze multiple."
# Questo trova la distanza massima tra tutte le sequenze.

def overall_max(sequences):
    '''Determinare la distanza massima complessiva di modifica. ''

    più alto = 0
    per sinistra in sequenze:
        per destra in sequenze:
            '''Evita la sequenza di controllo contro se stessa. ''
            se rimasto! right:
                this = edit_distance(left, destra)
                più alto = massimo (più alto, this)

    # Relazione.
    ritorno più alto
```

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Documento Questo

Utilizzare i commenti per descrivere e aiutare gli altri a comprendere le sezioni
potenzialmente non intuitive o singole righe di codice. They are especially useful to whoever
may need to understand and edit your code in the future, including yourself.

Utilizzare docstrings per documentare gli input accettabili e gli output attesi di un metodo
o classe, il suo scopo, le ipotesi e il comportamento previsto. Le stringhe di documenti sono visualizzate
quando un utente invoca il metodo `help` incorporato sul tuo metodo o classe.

Trasforma il commento nella seguente funzione in una docstring
e controlla che `help` lo mostri correttamente.

```python
def middle(a, b, c):
    # Restituisce il valore medio di tre.
    # Suppone che i valori possano essere effettivamente confrontati.
    values = [a, b, c]
    values.sort()
    return values[1]
```

::::::::::::::: soluzione

## Soluzione

```python
def middle(a, b, c):
    ''''Restituisce il valore medio di tre.
    Suppone che i valori possano essere effettivamente confrontati. Valori ''
    = [a, b, c]
    . ort()
    restituisce i valori[1]
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Pulisci Questo Codice

1. Leggi questo breve programma e prova a predire quello che fa.
2. Eseguilo: quanto era accurata la tua previsione?
3. Refactor il programma per renderlo più leggibile.
   Ricordati di eseguirlo dopo ogni modifica per assicurarsi che il suo comportamento non sia cambiato.
4. Confronta la riscrittura con quella del tuo vicino.
   Cos'hai fatto lo stesso?
   Cosa avete fatto in modo diverso e perché?

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

::::::::::::::: soluzione

## Soluzione

Ecco una soluzione.

```python
def string_machine(input_string, iterazioni):
    """
    Prende input_string e genera una nuova stringa con -'s e *'s
    corrispondente a caratteri che hanno identici caratteri adiacenti
    o no, rispettivamente. Itera attraverso questa procedura con le stringhe
    risultanti per il numero di iterazioni fornite.
    """
    print(input_string)
    input_string_length = len(input_string)
    old = input_string
    for i in range(iterations):
        new = ''
        # iterate through characters in previous string
        for j in range(input_string_length):
            left = j-1
            right = (j+1) % input_string_length # ensure right index wraps around
            if old[left] == old[right]:
                new = new + '-'
            else:
                new + '*'
        print(new)
        # store new
        = new     

string_machine', 10)
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

- Segui lo stile standard di Python nel tuo codice.
- Usa docstrings per fornire un aiuto integrato.

::::::::::::::::::::::::::::::::::::::::::::::::::
