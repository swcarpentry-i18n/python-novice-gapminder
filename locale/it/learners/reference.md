---
title: Riferimento
---

## Riferimento

## [Esecuzione e uscita](episodes/01-run-quit.md)

- I file Python hanno l'estensione `.py`.
- Può essere scritto in un file di testo o in un [Jupyter Notebook][jupyter].
  - I notebook di Jupyter hanno l'estensione `.ipynb`
  - I notebook Jupyter possono essere aperti da [Anaconda](https://docs.continuum.io/anaconda/install) o tramite la riga di comando inserendo `$ jupyter notebook`
    - Markdown e HTML sono permessi nelle celle markdown per la documentazione del codice.

## [Variabili e Assegnazione](episodes/02-variables.md)

- Le variabili sono memorizzate usando `=`.
  - Le stringhe sono definite nelle citazioni `'...'`.
  - I numeri interi e in virgola mobile sono definiti senza virgolette.
- Le variabili possono contenere lettere, cifre e trattini bassi `_`.
  - Impossibile iniziare con una cifra.
  - Le variabili che iniziano con sottolineature devono essere evitate.
- Usa `print(...)` per visualizzare i valori come testo.
- Puoi usare l'indicizzazione sulle stringhe.
  - L'indicizzazione inizia a 0.
  - La posizione è data tra parentesi quadre `[position]` seguendo il nome della variabile.
  - Prendi una fetta usando `[start:stop]`. Questo fa una copia di parte della stringa originale.
    - `start` è l'indice del primo elemento.
    - `stop` è l'indice dell'elemento dopo l'ultimo elemento desiderato.
- Usa `len(...)` per trovare la lunghezza di una variabile o di una stringa.

## [Tipi di dati e Tipo di conversione](episodi/03-types-conversion.md)

- Ogni valore ha un tipo. Questo controlla ciò che si può fare con esso.
  - `int` rappresenta un numero intero
  - `float` rappresenta un numero in virgola mobile.
  - `str` rappresenta una stringa.
- Per determinare un tipo di variabili, usa la funzione `type(...)`, incluso il nome della variabile nella parentesi.
- Modifica stringhe:
  - Usa `+` per concatenare le stringhe.
  - Usa `*` per ripetere una stringa.
  - Numeri e stringhe non possono essere aggiunti su un altro.
    - Converti stringa in intero: `int(...)`.
    - Converti interi in stringa: `str(...)`.

## [Funzioni integrate e Aiuto](episodes/04-built-in.md)

- Per aggiungere un commento, posiziona `#` prima che la cosa con cui non vuoi essere eseguita.
- Funzioni incorporate comunemente usate:
  - `min()` trova il valore più piccolo.
  - `max()` trova il valore più grande.
  - `round()` completa un numero in virgola mobile.
  - `help()` mostra la documentazione per la funzione nella parentesi.
    - Altri modi per ottenere aiuto includono tenere premuto `shift` e premere `tab` nei notebook di Jupyter.

## [Libraries](episodes/06-libraries.md)

- Importazione di una libreria:
  - Usa `import ...` per caricare una libreria.
  - Fare riferimento a questa libreria usando `module_name.thing_name`.
    - `.` indica 'parte di'.
- Per importare un elemento specifico da una libreria: `da ... import ...`
- Per importare una libreria usando un alias: `import ... come ...`
- Importazione della libreria matematica: `import math`
  - Esempio di riferimento a un elemento con il nome del modulo: `math.cos(math.pi)`.
- Importazione della libreria di tracciamento come alias: `import matplotlib as mpl`

## [Reading Tabular Data into DataFrames](episodes/07-reading-tabular.md)

- Utilizzare la libreria di panda per fare statistiche sui dati delle tabelle. Carica con `import pandas come pd`.
  - Per leggere in un csv: `pd.read_csv()`, incluso il nome del percorso nella parentesi.
    - Per specificare i valori di una colonna devono essere usati come intestazioni di riga: `pd. ead_csv('path', index_col='column name')`, dove il percorso e il nome della colonna devono essere sostituiti con i valori pertinenti.
- Per ottenere maggiori informazioni su DataFrame, usa `DataFrame.info`, sostituendo `DataFrame` con il nome variabile del tuo DataFrame.
- Usa `DataFrame.columns` per visualizzare i nomi delle colonne.
- Usa `DataFrame.T` per trasporre un DataFrame.
- Usa `DataFrame.describe` per ottenere statistiche sommarie sui tuoi dati.

## [Pandas DataFrames](episodes/08-data-frames.md)

- Seleziona i dati usando `[i,j]`
  - Per selezionare per posizione di entrata: `DataFrame.iloc[..., ...]`
    - Questo è comprensivo di tutto tranne l'indice finale.
  - Per selezionare per etichetta voce: `DataFrame.loc[..., ...]`
    - Puoi selezionare più righe o colonne elencando le etichette.
    - Questo è inclusivo per entrambi i fini.
  - Usa `:` per selezionare tutte le righe o colonne.
- Puoi anche selezionare i dati in base ai valori usando `True` e `False`. Questa è una maschera booleana.
  - `mask = subset > 10000`
  - Possiamo quindi usare questo per selezionare i valori.
- Per utilizzare un'operazione select-apply-combina, utilizziamo `data.apply(lambda x: x > x. ean())` dove `mean()` può essere qualsiasi operazione che l'utente vorrebbe essere applicata a x.

## [Plotting](episodi/09-plotting.md)

- La libreria di grafici più utilizzata è `matplotlib`.
  - Di solito importato usando `import matplotlib.pyplot come plt`.
  - Per tracciare il grafico utilizziamo il comando `plt.plot(time, position)`.
  - Per creare una leggenda usa `plt.legend(['label1', 'label2'], loc='upper left')`
    - Puoi anche definire le etichette all'interno delle istruzioni del grafico usando `plt.plot(tempo, posizione, label='label')`. Per far apparire la leggenda usa `plt.legend()`
  - Per etichettare l'asse x e y `plt.xlabel('label')` e `plt.ylabel('label')` sono usati.
- I DataFrames di Pandas possono essere usati per tracciare il grafico usando `DataFrame.plot()`. Tutte le operazioni che possono essere utilizzate su DataFrame possono essere applicate durante il tracciamento.
  - Per tracciare un grafico a barre `data.plot(kind='bar')`

```python
import matplotlib.puplot as plot
plt.plot(time, position, label='label')
plt.xlabel('x axis label')
plt.ylabel('y axis label')
plt.legend()
```

## [Lists](episodi/11-lists.md)

- Definito all'interno di `[...]` e separato da `,`.
  - Una lista vuota può essere creata usando `[]`.
- Puoi usare `len(...)` per determinare quanti valori sono in una lista.
- Può indicizzare esattamente come fatto nelle lezioni precedenti.
  - L'indicizzazione può essere usata per riassegnare i valori `list_name[0] = newvalue`.
- Per aggiungere un elemento a un elenco usa `list_name.append()`, con l'elemento da aggiungere nella parentesi.
- Per combinare due liste utilizzare `list_name_1.extend(list_name_2)`.
- Per rimuovere un elemento da un elenco usa `del list_name[index]`.

## [For Loops](episodes/12-for-loops.md)

- Inizia un loop con `for numero in [1, 2, 3]:`, con le seguenti righe rientrate.
  - `[1, 2, 3]` è considerata la collezione.
  - `number` è la variabile del ciclo.
  - L'azione che segue la raccolta è il corpo.
- Per iterare su una sequenza di numeri usa `range(start, end)`

```python
for number in range(0,5):
    print(number)
```

## [Conditionals](episodi/13-conditionals.md)

- Definito allo stesso modo di un ciclo, usando `if valore condizionale variabile:`.
  - Ad esempio, `if variabile > 5:`.
- Usa `elif:` per ulteriori test.
- Usa `else:` per quando la dichiarazione non è vera.
- Puoi combinare più di una condizione usando `e` o `o`.
- Spesso usato in combinazione con per i cicli.
- Condizioni che possono essere utilizzate:
  - `==` uguale a.
  - `>=` maggiore o uguale a.
  - `<=` inferiore o uguale a.
  - `>` maggiore di.
  - `<` meno di.

```python
per m in [3, 6, 7, 2, 8]:
    if m > 5:
        print(m, 'is large')
    elif m == 5:
        print(m, 'is 5')
    else:
        print(m, 'is small)
```

## [Looping Over Data Sets](episodes/14-looping-data-sets.md)

- Usa un per il loop: `for filename in [file1, file2]:`
- Per trovare un insieme di file usando un modello usa `glob.glob`
  - È necessario importare prima usando `import glob`.
  - `*` indica "zero o più caratteri"
  - `?` indica "abbina esattamente un carattere"
    - Per esempio: `glob.glob(*.txt)` troverà tutti i file che finiscono con `.txt` nella directory corrente.
- Combina queste scrivendo un ciclo usando: `per il nome file in glob.glob(*.txt):`

```python
for filename in glob.glob(*.txt):
  data = pd.read_csv(nome file)
```

## [Writing Functions](episodes/16-writing-functions.md)

- Definisci una funzione usando `def function_name(parametri):`. Sostituisci i `parametri` con le variabili da usare quando la funzione viene eseguita.
- Esegui usando `function_name(parametri)`.
- Per restituire un risultato al chiamante usa `return ...` nella funzione.

```python
def add_numbers(a, b):
    result = a + b
    return result

add_numbers(1, 4)
```

## [Ambito Variabile](episodes/17-scope.md)

- Una variabile locale è definita in una funzione e può essere vista e utilizzata solo all'interno di quella funzione.
- Una variabile globale è definita al di fuori di una funzione e può essere vista o utilizzata ovunque dopo la definizione.

## [Stile Di Programmazione](episodes/18-style.md)

- Documenta il tuo codice.
- Usa nomi di variabili chiari e significativi.
- Segui [la guida in stile PEP8](https://www.python.org/dev/peps/pep-0008) durante la configurazione del tuo codice.
- Utilizzare le asserzioni per verificare eventuali errori interni.
- Usa docstrings per fornire aiuto.

## Glossary

Argomenti
: Valori passati alle funzioni.

Array
: Un contenitore contenente elementi dello stesso tipo.

Booleano
: Un oggetto composto da `True` e `False`.

DataFrame
: Il modo in cui Panda rappresenta una tavola; una collezione di serie.

Elemento
: Un elemento in una lista o un array. Per una stringa, questi sono i singoli caratteri.

Funzione
: Un blocco di codice che può essere chiamato e riutilizzato altrove.

Variabile globale
: Una variabile definita al di fuori di una funzione che può essere utilizzata ovunque.

Indice
: La posizione di un dato elemento.

Jupyter Notebook
: Ambiente di codifica interattivo che consente una combinazione di codice e markdown.

Libreria
: Una raccolta di file contenenti funzioni utilizzate da altri programmi.

Variabile locale
: Una variabile definita all'interno di una funzione che può essere utilizzata solo all'interno di quella funzione.

Maschera
: Un oggetto booleano utilizzato per selezionare i dati da un altro oggetto.

Metodo
: Un'azione legata a un determinato oggetto. Chiamato usando `object.method`.

Moduli
: I file all'interno di una libreria contenente funzioni utilizzate da altri programmi.

Parametri
: Variabili usate quando si esegue una funzione.

Serie
: A Pandas data structure to represent a column.

Sottostringa
: Una parte di una stringa.

Variabili
: nomi dei valori.
