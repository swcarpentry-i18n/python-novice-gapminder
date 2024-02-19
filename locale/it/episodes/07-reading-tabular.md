---
title: Lettura dei dati tabulari nei DataFrame
teaching: 10
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- Importa la libreria Pandas.
- Usa Panda per caricare un semplice set di dati CSV.
- Ottieni alcune informazioni di base su un DataFrame.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::: domande

- Come posso leggere i dati delle tabelle?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Utilizzare la libreria di Pandas per fare statistiche sui dati tabellari.

- [Pandas](https://pandas.pydata.org/) è una libreria Python ampiamente utilizzata per le statistiche, in particolare sui dati tabulari.
- Prende in prestito molte caratteristiche dai dataframes di R.
  - Una tabella bidimensionale le cui colonne hanno nomi
    e potenzialmente hanno diversi tipi di dati.
- Carica Panda con `import pandas come pd`. L'alias `pd` è comunemente usato per fare riferimento alla libreria di Pandas nel codice.
- Leggi un file di dati Comma Separated Values (CSV) con `pd.read_csv`.
  - Argomento è il nome del file da leggere.
  - Restituisce un dataframe che puoi assegnare a una variabile

```python
import panda as pd

data_oceania = pd.read_csv('data/gapminder_gdp_oceania.csv')
print(data_oceania)
```

```output
       country gdpPercap_1952 gdpPercap_1957 gdpPercap_1962 \
0 Australia 10039. 9564 10949.64959 12217. 2686
1 Nuova Zelanda 10556.57566 12247. 9532 13175. 7800

   gdpPercap_1967 gdpPercap_1972 gdpPercap_1977 gdpPercap_1982 \
0 14526. 2465 16788.62948 18334.19751 19477.00928
1 14463. 1893 16046.03728 16233.71770 17632. 1040

   gdpPercap_1987 gdpPercap_1992 gdpPercap_1997 gdpPercap_2002 \
0 21888. 8903 23424,76683 26997. 3657 30687.75473
1 19007. 9129 18363.32494 21050.41377 23189. 0135

   gdpPercap_2007
0 34435.36744
1 25185.00911
```

- Le colonne in un dataframe sono le variabili osservate e le righe sono le osservazioni.
- Pandas utilizza backslash `\` per mostrare le linee a capo quando l'output è troppo largo per adattarsi allo schermo.
- L'utilizzo di nomi descrittivi di dataframe ci aiuta a distinguere tra più dataframe in modo da non sovrascrivere accidentalmente un dataframe o leggere da quello sbagliato.

:::::::::::::::::::::::::::::::::::::::::  callout

## File Non Trovato

Le nostre lezioni memorizzano i loro file di dati in una sottodirectory `data`,
ed è per questo che il percorso del file è `data/gapminder_gdp_oceania.csv`.
Se dimentichi di includere `data/`,
o se lo includi, ma la tua copia del file è altrove,
otterrai un [errore di runtime](04-built-in. d)
che termina con una riga come questa:

```error
FileNotFoundError: [Errno 2] No such file or directory: 'data/gapminder_gdp_oceania.csv'
```

::::::::::::::::::::::::::::::::::::::::::::::::::

## Usa `index_col` per specificare che i valori di una colonna devono essere usati come intestazioni di riga.

- Le voci della riga sono numeri (0 e 1 in questo caso).
- Davvero vuole indicizzare per paese.
- Passa il nome della colonna a `read_csv` come parametro `index_col` per farlo.
- Naming the dataframe `data_oceania_country` ci dice quale regione i dati includono (`oceania`) e come sono indicizzati (`country`).

```python
data_oceania_country = pd.read_csv('data/gapminder_gdp_oceania.csv', index_col='country')
print(data_oceania_country)
```

```output
             gdpPercap_1952 gdpPercap_1957 gdpPercap_1962 gdpPercap_1967 \
country
Australia 10039. 9564 10949.64959 12217.22686 14526.12465
Nuova Zelanda 10556. 7566 12247.39532 13175.67800 14463. 1893

             gdpPercap_1972 gdpPercap_1977 gdpPercap_1982 gdpPercap_1987 \
country
Australia 16788. 2948 18334.19751 19477.00928 21888.88903
Nuova Zelanda 16046. 3728 16233.71770 17632.41040 19007. 9129

             gdpPercap_1992 gdpPercap_1997 gdpPercap_2002 gdpPercap_2007
country
Australia 23424. 6683 26997.93657 30687.75473 34435.36744
Nuova Zelanda 18363. 2494 21050.41377 23189.80135 25185.00911
```

## Usa il metodo `DataFrame.info()` per saperne di più su un dataframe.

```python
data_oceania_country
```

```output
<class 'pandas.core.frame.DataFrame'>
Index: 2 entries, Australia to New Zealand
Data columns (total 12 columns):
gdpPercap_1952    2 non-null float64
gdpPercap_1957    2 non-null float64
gdpPercap_1962    2 non-null float64
gdpPercap_1967    2 non-null float64
gdpPercap_1972    2 non-null float64
gdpPercap_1977    2 non-null float64
gdpPercap_1982    2 non-null float64
gdpPercap_1987    2 non-null float64
gdpPercap_1992    2 non-null float64
gdpPercap_1997    2 non-null float64
gdpPercap_2002    2 non-null float64
gdpPercap_2007    2 non-null float64
dtypes: float64(12)
memory usage: 208.0+ bytes
```

- Questo è un `DataFrame`
- Due righe denominate `'Australia'` e `'Nuova Zelanda'`
- Dodici colonne, ognuna delle quali ha due valori reali in virgola mobile a 64 bit.
  - Parleremo più tardi di valori nulli, che sono usati per rappresentare le osservazioni mancanti.
- Utilizza 208 byte di memoria.

## La variabile `DataFrame.columns` memorizza informazioni sulle colonne del dataframe.

- Si noti che questo è un dato _non_ un metodo.  (Non ha parentesi.)
  - Come `math.pi`.
  - Quindi non usare `()` per provare a chiamarlo.
- Chiamato un _membro variabile_, o semplicemente _membro_.

```python
print(data_oceania_country.columns)
```

```output
Indice(['gdpPercap_1952', 'gdpPercap_1957', 'gdpPercap_1962', 'gdpPercap_1967',
       'gdpPercap_1972', 'gdpPercap_1977', 'gdpPercap_1982', 'gdpPercap_1987',
       'gdpPercap_1992', 'gdpPercap_1997', 'gdpPercap_2002', 'gdpPercap_2007'],
      dtype='object')
```

## Usa `DataFrame.T` per trasporre un dataframe.

- A volte vogliono trattare le colonne come righe e viceversa.
- Transpose (scritto `.T`) non copia i dati, ma cambia la vista del programma.
- Come `columns`, è una variabile membro.

```python
print(data_oceania_country.T)
```

```output
paese Australia Nuova Zelanda
gdpPercap_1952 10039.59564 10556. 7566
gdpPercap_1957 10949.64959 12247.39532
gdpPercap_1962 12217. 2686 13175.67800
gdpPercap_1967 14526.12465 14463.91893
gdpPercap_1972 16788.62948 16046.03728
gdpPercap_1977 18334. 9751 16233.71770
gdpPercap_1982 19477.00928 17632.41040
gdpPercap_1987 21888.88903 19007.19129
gdpPercap_1992 23424.76683 18363. 2494
gdpPercap_1997 26997.93657 21050.41377
gdpPercap_2002 30687.75473 23189.80135
gdpPercap_2007 34435.36744 25185.00911
```

## Usa `DataFrame.describe()` per ottenere statistiche sommarie sui dati.

`DataFrame.describe()` ottiene le statistiche di sintesi solo delle colonne che hanno dati numerici.
Tutte le altre colonne vengono ignorate, a meno che non si utilizzi l'argomento `include='all'`.

```python
print(data_oceania_country.describe())
```

```output
       gdpPercap_1952 gdpPercap_1957 gdpPercap_1962 gdpPercap_1967 \
count 2. 00000 2.000000 2. 00000 2.000000
media 10298.085650 11598.522455 12696. 52430 14495.021790
std 365.560078 917. 44806 677,727301 43. 86086
min 10039.595640 10949. 49590 12217.226860 14463.918930
25% 10168. 40645 11274.086022 12456.839645 14479.470360
50% 10298. 85650 11598.522455 12696.452430 14495. 21790
75% 10427.330655 11922.958888 12936.065215 14510. 73220
max 10556,575660 12247,395320 13175. 78000 14526. 24650

       gdpPercap_1972 gdpPercap_1977 gdpPercap_1982 gdpPercap_1987 \
count 2. 0000 2.000000 2.000000 2. 00000
media 16417. 3338 17283.957605 18554.709840 20448. 40160
std 525.09198 1485.263517 1304. 28377 2037.668013
min 16046.03728 16233. 17700 17632.410400 19007.191290
25% 16231.68533 16758. 37652 18093.560120 19727.615725
50% 16417. 3338 17283.957605 18554.709840 20448.040160
75% 16602. 8143 17809.077557 19015.859560 21168. 64595
max 16788.62948 18334.197510 19477.009280 21888. 89030

       gdpPercap_1992 gdpPercap_1997 gdpPercap_2002 gdpPercap_2007
count 2. 00000 2.000000 2.000000 2. 00000
media 20894. 45885 24024.175170 26938.778040 29810.188275
std 3578. 79883 4205.533703 5301.853680 6540. 91104
min 18363.324940 21050.413770 23189.801350 25185. 09110
25% 19628.685413 22537.294470 25064. 89695 27497.598692
50% 20894.045885 24024. 75170 26938.778040 29810.188275
75% 22159. 06358 25511.055870 28813.266385 32122.777857
max 23424. 66830 26997.936570 30687.754730 34435.367440
```

- Non particolarmente utile con solo due record,
  ma molto utile quando ci sono migliaia.

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Lettura Altri Dati

Leggi i dati in `gapminder_gdp_americas.csv`
(che dovrebbero essere nella stessa directory di `gapminder_gdp_oceania. sv`)
in una variabile chiamata `data_americas`
e visualizza le statistiche sommarie.

::::::::::::::: soluzione

## Soluzione

Per leggere in un CSV, usiamo `pd.read_csv` e passiamo il file `'data/gapminder_gdp_americas.csv'` ad esso.
Anche noi passiamo nuovamente il nome della colonna `'country'` al parametro `index_col` per indicizzare per paese.
Le statistiche di riepilogo possono essere visualizzate con il metodo `DataFrame.describe()`.

```python
data_americas = pd.read_csv('data/gapminder_gdp_americas.csv', index_col='country')
data_americas.describe()
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Dati Di Ispezione

Dopo aver letto i dati per le Americhe,
usa `help(data_americas.head)` e `help(data_americas.tail)`
per scoprire cosa fanno `DataFrame.head` e `DataFrame.tail`.

1. Quale metodo di chiamata mostrerà le prime tre righe di questi dati?
2. Quale metodo di chiamata mostrerà le ultime tre colonne di questi dati?
   (Hint: potrebbe essere necessario modificare la tua opinione dei dati.)

::::::::::::::: soluzione

## Soluzione

1. Possiamo controllare le prime cinque righe di `data_americas` eseguendo `data_americas.head()`
   che ci permette di visualizzare l'inizio del DataFrame. Possiamo specificare il numero di righe che desideriamo vedere
   specificando il parametro `n` nella nostra chiamata a `data_americas.head()`.
   Per visualizzare le prime tre righe, eseguire:

```python
data_americas.head(n=3)
```

```output
          continente gdpPercap_1952 gdpPercap_1957 gdpPercap_1962 \
country
Argentina Americas 5911. 15053 6856. 56212 7133.166023
Bolivia Americas 2677.326347 2127. 86326 2180.972546
Brasile Americas 2108.944355 2487. 65989 3336. 85802

          gdpPercap_1967 gdpPercap_1972 gdpPercap_1977 gdpPercap_1982 \
country
Argentina 8052. 53021 9443.038526 10079.026740 8997.897412
Bolivia 2586. 86053 2980.331339 3548.097832 3156. 10452
Brasile 3429. 64357 4985.711467 6660.118654 7030. 35878

           gdpPercap_1987 gdpPercap_1992 gdpPercap_1997 gdpPercap_2002 \
country
Argentina 9139. 71389 9308.418710 10967.281950 8797.640716
Bolivia 2753. 91490 2961.699694 3326.143191 3413. 62690
Brasile 7807. 95818 6950.283021 7957.980824 8131. 12843

           gdpPercap_2007
paese
Argentina 12779. 79640
Bolivia 3822.137084
Brasile 9065.800825
```

2. Per controllare le ultime tre righe di `data_americas`, useremmo il comando,
   `americas.tail(n=3)`, analogo a `head()` usato sopra. Tuttavia, qui vogliamo guardare
   le ultime tre colonne quindi dobbiamo cambiare la nostra vista e quindi utilizzare `tail()`. Per farlo,
   creiamo un nuovo DataFrame in cui sono commutate righe e colonne:

```python
americas_flipped = data_americas.T
```

Possiamo quindi visualizzare le ultime tre colonne di `americas` visualizzando le ultime tre righe
di `americas_flipped`:

```python
americas_flipped.tail(n=3)
```

```output
paese Argentina Bolivia Brasile Canada Cile Colombia \
gdpPercap_1997 10967. 3326,14 7957,98 28954,9 10118,1 6117. 6
gdpPercap_2002 8797,64 3413,26 8131,21 33329 10778,8 5755. 6
gdpPercap_2007 12779,4 3822,14 9065,8 36319,2 13171,6 7006. 8

paese Costa Rica Cuba Repubblica Dominicana Ecuador ... \
gdpPercap_1997 6677. 5 5431.99 3614.1 7429.46 . .
gdpPercap_2002 7723,45 6340. 5 4563.81 5773.04 ...
gdpPercap_2007 9645.06 8948. 6025.37 6873.26 ...

Paese Messico Nicaragua Panama Paraguay Perù Portorico \
gdpPercap_1997 9767. 2253,02 7113,69 4247,4 5838,35 16999.
gdpPercap_2002 10742,4 2474,55 7356,03 3783,67 5909,02 18855.
gdpPercap_2007 11977,6 2749,32 9809,19 4172,84 7408. 1 19328.

paese Trinidad e Tobago Stati Uniti Uruguay Venezuela
gdpPercap_1997 8792. 7 35767,4 9230,24 10165.
gdpPercap_2002 11460. 39097.1 7727 8605. 5
gdpPercap_2007 18008. 42951,7 10611,5 11415,8
```

Questo mostra i dati che vogliamo, ma potremmo preferire visualizzare tre colonne invece di tre righe,
così possiamo capovolgerlo indietro:

```python
americas_flipped.tail(n=3).T    
```

**Nota:** avremmo potuto fare quanto sopra in una singola riga di codice con 'chaining' i comandi:

```python
data_americas.T.tail(n=3).T
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Lettura di file in altre directory

I dati del progetto corrente sono memorizzati in un file chiamato `microbes.csv`,
che si trova in una cartella chiamata `field_data`.
Stai facendo analisi in un notebook chiamato `analysis.ipynb`
in una cartella sorella chiamata `thesis`:

```output
your_home_directory
+-- field_data/
<unk> +-- microbes.csv
+-- thesis/
    +-- analysis.ipynb
```

Quali valori dovresti passare a `read_csv` per leggere `microbes.csv` in `analysis.ipynb`?

::::::::::::::: soluzione

## Soluzione

Dobbiamo specificare il percorso del file di interesse nella chiamata a `pd.read_csv`. Abbiamo prima bisogno di 'saltare' fuori da
la cartella `thesis` usando '../' e poi nella cartella `field_data` usando 'field_data/'. Quindi possiamo specificare il nome del file \`microbes.csv.
Il risultato è il seguente:

```python
data_microbes = pd.read_csv('../field_data/microbes.csv')
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Scrittura Dati

Oltre alla funzione `read_csv` per leggere i dati da un file,
Pandas fornisce una funzione `to_csv` per scrivere i dataframe sui file.
Applicando ciò che hai imparato a leggere dai file,
scrive uno dei tuoi dataframe in un file chiamato `processed.csv`.
Puoi usare `help` per ottenere informazioni su come usare `to_csv`.

::::::::::::::: soluzione

## Soluzione

Per scrivere il file `data_americas` DataFrame in un file chiamato `processed.csv`, eseguire il seguente comando:

```python
data_americas.to_csv('processed.csv')
```

Per aiuto su `read_csv` o `to_csv`, puoi eseguire, per esempio:

```python
help(data_americas.to_csv)
help(pd.read_csv)
```

Nota che `help(to_csv)` o `help(pd.to_csv)` genera un errore! Ciò è dovuto al fatto che `to_csv` non è una funzione globale di Pandas, ma
una funzione membro di DataFrames. Questo significa che puoi chiamarlo solo su un'istanza di DataFrame
ad esempio, `data_americas.to_csv` o `data_oceania.to_csv`

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Utilizzare la libreria di Panda per ottenere statistiche di base dai dati tabulari.
- Usa `index_col` per specificare che i valori di una colonna devono essere usati come intestazioni di riga.
- Usa `DataFrame.info` per saperne di più su un dataframe.
- La variabile `DataFrame.columns` memorizza informazioni sulle colonne del dataframe.
- Usa `DataFrame.T` per trasporre un dataframe.
- Usa `DataFrame.describe` per ottenere statistiche sommarie sui dati.

::::::::::::::::::::::::::::::::::::::::::::::::::
