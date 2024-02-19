---
title: Looping Over Data Set
teaching: 5
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- Essere in grado di leggere e scrivere espressioni globbing che corrispondono a insiemi di file.
- Usa il globo per creare elenchi di file.
- Scrivi per i loop per eseguire operazioni sui file dati i loro nomi in un elenco.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::: domande

- Come posso elaborare molti set di dati con un singolo comando?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Usa un ciclo `for` per elaborare i file dato un elenco dei loro nomi.

- Un nome file è una stringa di caratteri.
- E le liste possono contenere stringhe di caratteri.

```python
importa panda come pd
per il nome file in ['data/gapminder_gdp_africa.csv', 'data/gapminder_gdp_asia.csv']:
    data = pd.read_csv(filename, index_col='country')
    print(filename, data.min())
```

```output
data/gapminder_gdp_africa.csv gdpPercap_1952 298.846212
gdpPercap_1957 335.997115
gdpPercap_1962 355.203227
gdpPercap_1967 412. 77514
<unk> <unk> <unk>
gdpPercap_1997 312.188423
gdpPercap_2002 241.165877
gdpPercap_2007 277. 51859
dtype: float64
data/gapminder_gdp_asia. sv gdpPercap_1952 331
gdpPercap_1957 350
gdpPercap_1962 388
gdpPercap_1967 349
<unk> <unk> <unk>
gdpPercap_1997 415
gdpPercap_2002 611
gdpPercap_2007 944
dtype: float64
```

## Usa [`glob.glob`](https://docs.python.org/3/library/glob.html#glob.glob) per trovare insiemi di file i cui nomi corrispondono a un modello.

- In Unix, il termine "globbing" significa "abbinare un insieme di file con un modello".
- I modelli più comuni sono:
  - `*` significa "corrispondere a zero o più caratteri"
  - `?` significa "abbinare esattamente un carattere"
- La libreria standard di Python contiene il modulo [`glob`](https://docs.python.org/3/library/glob.html) per fornire funzionalità di corrispondenza dei modelli
- Il modulo [`glob`](https://docs.python.org/3/library/glob.html) contiene una funzione chiamata anche `glob` per abbinare i modelli di file
- Ad esempio, `glob.glob('*.txt')` corrisponde a tutti i file nella directory corrente
  i cui nomi terminano con `.txt`.
- Il risultato è un elenco (forse vuoto) di stringhe di caratteri.

```python
import glob
print('all csv files in data directory:', glob.glob('data/*.csv'))
```

```output
tutti i file csv nella directory dei dati: ['data/gapminder_all.csv', 'data/gapminder_gdp_africa.csv', \
'data/gapminder_gdp_americas.csv', 'data/gapminder_gdp_asia.csv', 'data/gapminder_gdp_europe.csv', \
'data/gapminder_gdp_oceania.csv']
```

```python
print('tutti i file PDB:', glob.glob('*.pdb'))
```

```output
tutti i file PDB: []
```

## Usa `glob` e `per` per elaborare lotti di file.

- Aiuta molto se i file sono nominati e memorizzati in modo sistematico e coerente
  in modo che semplici modelli troveranno i dati giusti.

```python
for filename in glob.glob('data/gapminder_*.csv'):
    data = pd.read_csv(filename)
    print(filename, data['gdpPercap_1952'].min())
```

```output
data/gapminder_all.csv 298.8462121
data/gapminder_gdp_africa.csv 298.8462121
data/gapminder_gdp_americas.csv 1397.717137
data/gapminder_gdp_asia.csv 331.0
data/gapminder_gdp_europe.csv 973.5331948
data/gapminder_gdp_oceania.csv 10039.59564
```

- Questo include tutti i dati, così come i dati per regione.
- Utilizzare un modello più specifico negli esercizi per escludere l'intero set di dati.
- Ma si noti che il minimo dell'intero set di dati è anche il minimo di uno dei set di dati,
  che è un bel controllo sulla correttezza.

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Determinazione Delle Partite

Quale di questi file è _non_ abbinato all'espressione `glob.glob('data/*as*.csv')`?

1. `data/gapminder_gdp_africa.csv`
2. `data/gapminder_gdp_americas.csv`
3. `data/gapminder_gdp_asia.csv`

::::::::::::::: soluzione

## Soluzione

1 non è abbinato dal globo.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Dimensione Minima File

Modificare questo programma in modo che stampi il numero di record in
il file che ha i record più deboli.

```python
import glob
import pandas as pd
fewest = ____
for filename in glob.glob('data/*.csv'):
    dataframe = pd. ___(nome file)
    fewest = min(____, dataframe.shape[0])
print('il file più piccolo ha', minore, 'records')
```

Nota che il metodo [`DataFrame.shape()`][shape-method]
restituisce una tupla con il numero di righe e colonne del quadro dati.

::::::::::::::: soluzione

## Soluzione

```python
import glob
import pandas as pd
fewest = float('Inf')
for filename in glob.glob('data/*.csv'):
    dataframe = pd. ead_csv(nome file)
    fewest = min(fewest, dataframe.shape[0])
print('smallest file has', fewest, 'records')
```

Potresti aver scelto di inizializzare la variabile `fewest` con un numero maggiore dei numeri
che hai a che fare, ma questo potrebbe portare a problemi se si riutilizza il codice con numeri più grandi.
Python ti permette di usare l'infinito positivo, che funzionerà non importa quanto siano grandi i tuoi numeri.
Quali altre stringhe speciali riconosce la funzione [`float`][float-function]?

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Confronto Dei Dati

Scrivi un programma che legge nei set di dati regionali
e traccia il PIL medio pro capite per ogni regione nel tempo
in un unico grafico.

::::::::::::::: soluzione

## Soluzione

Questa soluzione costruisce una legenda utile usando il [metodo `split`][split-method] per
estrarre la `region` dal percorso 'data/gapminder\_gdp\_a\_specific\_region.csv'.

```python
import glob
import pandas as pd
import matplotlib.pyplot as plt
fig, ax = plt.subplots(1,1)
for filename in glob.glob('data/gapminder_gdp*. sv'): dataframe
    = pd. ead_csv(nomefile)
    # estrae <region> dal nome del file, che dovrebbe essere nel formato 'data/gapminder_gdp_<region>.csv'.
    # divideremo la stringa usando il metodo di split e `_` come nostro separatore,
    # recupera l'ultima stringa nella lista che divide restituisce (`<region>. sv`), 
    # e quindi rimuovere `. sv` estensione da quella stringa.
    regione = nomefile.split('_')[-1][:-4] 
    frame dati. ean().plot(ax=ax, label=regione)
plt.legend()
plt.show()
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## Gestire i percorsi dei file

Il modulo [`pathlib`][pathlib-module] fornisce utili astrazioni per la manipolazione del file e del percorso come
restituendo il nome di un file senza l'estensione del file. Questo è molto utile quando si carica sopra i file e le directory
. Nell'esempio qui sotto, creiamo un oggetto `Path` e ispezioniamo i suoi attributi.

```python
from pathlib import Path

p = Path("data/gapminder_gdp_africa.csv")
print(p.parent), print(p.stem), print(p.suffix)
```

```output
dati
gapminder_gdp_africa
.csv
```

**Suggerimento:** È possibile controllare tutti gli attributi e i metodi disponibili sull'oggetto `Path` con la funzione `dir()`
!

::::::::::::::::::::::::::::::::::::::::::::::::::

[shape-method]: https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.shape.html

[float-function]: https://docs.python.org/3/library/functions.html#float

[split-method]: https://docs.python.org/3/library/stdtypes.html#str.split

[pathlib-module]: https://docs.python.org/3/library/pathlib.html

:::::::::::::::::::::::::::::::::::::::: keypoints

- Usa un ciclo `for` per elaborare i file dato un elenco dei loro nomi.
- Usa `glob.glob` per trovare insiemi di file i cui nomi corrispondono a un modello.
- Usa `glob` e `per` per elaborare lotti di file.

::::::::::::::::::::::::::::::::::::::::::::::::::
