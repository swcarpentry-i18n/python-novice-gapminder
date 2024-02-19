---
title: Pandas DataFrames
teaching: 15
exercises: 15
---

::::::::::::::::::::::::::::::::::::::: objectives

- Seleziona valori individuali da un dataframe di Panda.
- Seleziona intere righe o intere colonne da un dataframe.
- Selezionare un sottoinsieme di entrambe le righe e colonne da un dataframe in una singola operazione.
- Seleziona un sottoinsieme di un dataframe con un singolo criterio booleano.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::: domande

- Come posso fare l'analisi statistica dei dati tabulari?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Nota su Pandas DataFrames/Series

A [DataFrame][pandas-dataframe] è una collezione di [Series][pandas-series];
Il DataFrame è il modo in cui Pandas rappresenta una tabella, e Series è la struttura dati
Pandas utilizzare per rappresentare una colonna.

Pandas è costruito in cima alla biblioteca [Numpy][numpy] , che in pratica significa che
la maggior parte dei metodi definiti per Numpy Arrays si applicano a Pandas Series/DataFrames.

Ciò che rende Panda così attraente è l'interfaccia potente per accedere ai singoli record
del tavolo, corretta gestione dei valori mancanti e delle operazioni relative ai database-relazioni
tra DataFrames.

## Selezione valori

Per accedere a un valore nella posizione `[i,j]` di un DataFrame, abbiamo due opzioni, a seconda di
qual è il significato di `i` in uso.
Ricorda che un DataFrame fornisce un _indice_ come modo per identificare le righe della tabella;
una riga, quindi, ha una _posizione_ all'interno della tabella e una _etichetta_, che
identifica univocamente la sua _voce_ nel DataFrame.

## Usa `DataFrame.iloc[..., ...]` per selezionare i valori in base alla loro posizione (entrata)

- Può specificare la posizione per indice numerico analogamente alla versione 2D della selezione dei caratteri nelle stringhe.

```python
import pandas as pd
data = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')
print(data.iloc[0, 0])
```

```output
1601.056136
```

## Usa `DataFrame.loc[..., ...]` per selezionare i valori con la loro etichetta (entry).

- Può specificare la posizione per riga e/o nome di colonna.

```python
print(data.loc["Albania", "gdpPercap_1952"])
```

```output
1601.056136
```

## Usa `:` da solo per significare tutte le colonne o tutte le righe.

- Proprio come la solita notazione di affettatura di Python.

```python
print(data.loc["Albania", :])
```

```output
gdpPercap_1952 1601.056136
gdpPercap_1957 1942.284244
gdpPercap_1962 2312.888958
gdpPercap_1967 2760. 96931
gdpPercap_1972 3313.422188
gdpPercap_1977 3533.003910
gdpPercap_1982 3630. 80722
gdpPercap_1987 3738.932735
gdpPercap_1992 2497.437901
gdpPercap_1997 3193. 54604
gdpPercap_2002 4604.211737
gdpPercap_2007 5937.029526
Nome: Albania, dtype: float64
```

- Otterrebbe lo stesso risultato stampando `data.loc["Albania"]` (senza un secondo indice).

```python
print(data.loc[:, "gdpPercap_1952"])
```

```output
paese
Albania 1601. 56136
Austria 6137. 76492
Belgio 8343. 05127
<unk> <unk>
Svizzera 14734. 32750
Turchia 1969. 00980
Regno Unito 9979. 08487
Nome: gdpPercap_1952, dtype: float64
```

- Otterrebbe lo stesso risultato stampando `data["gdpPercap_1952"]`
- Ottenere anche lo stesso risultato stampare `data.gdpPercap_1952` (non consigliato, perché facilmente confuso con `.` notazione per i metodi)

## Seleziona più colonne o righe usando `DataFrame.loc` e una parte con nome.

```python
print(data.loc['Italy':'Polonia', 'gdpPercap_1962':'gdpPercap_1972'])
```

```output
             gdpPercap_1962 gdpPercap_1967 gdpPercap_1972
country
Italy 8243. 82340 10022.401310 12269.273780
Montenegro 4649. 93785 5907,850937 7778. 14017
Paesi Bassi 12790.849560 15363. 51360 18794.745670
Norvegia 13450. 01510 16361.876470 18965.055510
Polonia 5338. 52143 6557.152776 8006.506993
```

Nel codice di cui sopra, scopriamo che \*\*tagliare usando `loc` è inclusivo in entrambe le estremità
\*\*, che differisce da **affettare usando `iloc`**, dove affettare indica
tutto fino a ma non incluso l'indice finale.

## Il risultato dell'affettatura può essere utilizzato in ulteriori operazioni.

- Di solito non stampare solo un ritaglio.
- Tutti gli operatori statistici che lavorano su interi dataframe
  funzionano allo stesso modo su fette.
- Per esempio, calcolare il massimo di un ritaglio.

```python
print(data.loc['Italy':'Polonia', 'gdpPercap_1962':'gdpPercap_1972'].max())
```

```output
gdpPercap_1962 13450.40151
gdpPercap_1967 16361.87647
gdpPercap_1972 18965.05551
dtype: float64
```

```python
print(data.loc['Italy':'Polonia', 'gdpPercap_1962':'gdpPercap_1972'].min())
```

```output
gdpPercap_1962 4649.593785
gdpPercap_1967 5907.850937
gdpPercap_1972 7778.414017
dtype: float64
```

## Utilizzare i confronti per selezionare i dati in base al valore.

- Il confronto è applicato elemento per elemento.
- Restituisce un dataframe simile a forma di `True` e `False`.

```python
# Usa un sottoinsieme di dati per mantenere l'output leggibile. sottoinsieme
= dati. oc['Italy':'Polonia', 'gdpPercap_1962':'gdpPercap_1972']
print('Subset of data:\n', subset)

# Quali valori erano maggiori di 10000 ?
print('\nDove sono i valori grandi?\n', sottoinsieme > 10000)
```

```output
Sottoinsieme di dati:
             gdpPercap_1962 gdpPercap_1967 gdpPercap_1972
country
Italy 8243. 82340 10022.401310 12269.273780
Montenegro 4649.593785 5907. 50937 7778.414017
Paesi Bassi 12790.849560 15363. 51360 18794.745670
Norvegia 13450. 01510 16361.876470 18965.055510
Polonia 5338. 52143 6557.152776 8006. 06993

Dove sono i valori grandi?
            gdpPercap_1962 gdpPercap_1967 gdpPercap_1972
country
Italy False True True
Montenegro False False False
Netherlands True True True
Norway True True True
Polonia False False False
```

## Seleziona valori o NaN usando una maschera booleana.

- Una cornice piena di Booleani è talvolta chiamata una _maschera_ a causa di come può essere utilizzata.

```python
maschera = sottoinsieme > 10000
print(sottoinsieme[mask])
```

```output
             gdpPercap_1962 gdpPercap_1967 gdpPercap_1972
country
Italy NaN 10022. 0131 12269. 7378
Montenegro NaN NaN NaN
Paesi Bassi 12790. 4956 15363.25136 18794. 4567
Norvegia 13450.40151 16361. 7647 18965. 5551
Polonia NaN NaN NaN
```

- Ottieni il valore dove la maschera è vera, e NaN (Not a Number) dove è falso.
- Utile perché i NaN sono ignorati da operazioni come max, min, media, ecc.

```python
print(subset[subset > 10000].describe())
```

```output
       gdpPercap_1962 gdpPercap_1967 gdpPercap_1972
count 2. 00000 3.000000 3.000000
media 13120. 25535 13915.843047 16676.358320
std 466.373656 3408. 89070 3817.597015
min 12790.849560 10022. 01310 12269.273780
25% 12955.737547 12692.826335 15532. 09725
50% 13120.625535 15363.251360 18794. 45670
75% 13285.513523 15862.563915 18879. 00590
max 13450.401510 16361.876470 18965.055510
```

## Gruppo Da: split-apply-combinare

::::::::::::::::::::::::::::::::::::::::::: instructor
Gli studenti spesso lottano qui, molti potrebbero non lavorare con i dati finanziari e concetti in modo che
trovano i concetti di esempio difficile per ottenere la testa intorno. Il problema più grande
è però la linea che genera il wealth_score, questo passo deve essere discusso attraverso
attraverso:

- Utilizza la conversione implicita tra valori booleani e float che
  non è stato finora coperto nel corso.
- L'argomento axis=1 deve essere spiegato chiaramente.
  :::::::::::::::::::::::::::::::::::::::::::::::::

I metodi di vectorizing Pandas e le operazioni di raggruppamento sono caratteristiche che forniscono agli utenti
molta flessibilità per analizzare i loro dati.

Per esempio, diciamo che vogliamo avere una visione più chiara su come i paesi europei
si dividono in base al loro PIL.

1. Potremmo avere uno sguardo dividendo i paesi in due gruppi durante gli anni esaminati,
   coloro che hanno presentato un PIL _più alto_ della media europea e quelli con un PIL _più basso_.
2. Si stima quindi un _punteggio ricco_ basato sui valori storici (dal 1962 al 2007),
   dove contiamo quante volte un paese ha partecipato ai gruppi di PIL _inferiore_ o _superiore_

```python
mask_higher = data > data.mean()
wealth_score = mask_higher.aggregate('sum', axis=1) / len(data.columns)
print(wealth_score)
```

```output
paese
Albania 0. 00000
Austria 1. 00000
Belgio 1. 00000
Bosnia-Erzegovina 0. 00000
Bulgaria 0. 00000
Croazia 0. 00000
Repubblica Ceca 0. 00000
Danimarca 1. 00000
Finlandia 1. 00000
Francia 1. 00000
Germania 1. 00000
Grecia 0. 33333
Ungheria 0. 00000
Islanda 1. 00000
Irlanda 0. 33333
Italia 0. 00000
Montenegro 0. 00000
Paesi Bassi 1. 00000
Norvegia 1. 00000
Polonia 0. 00000
Portogallo 0. 00000
Romania 0. 00000
Serbia 0. 00000
Repubblica Slovacca 0. 00000
Slovenia 0. 33333
Spagna 0. 33333
Svezia 1. 00000
Svizzera 1. 00000
Turchia 0. 00000
Regno Unito 1.000000
dtype: float64
```

Infine, per ogni gruppo nella tabella `wealth_score`, sommiamo il loro contributo (finanziario)
nel corso degli anni intervistati utilizzando metodi incatenati:

```python
print(data.groupby(wealth_score).sum())
```

```output
          gdpPercap_1952 gdpPercap_1957 gdpPercap_1962 gdpPercap_1967 \
0. 00000 36916.854200 46110.918793 56850.065437 71324. 48786   
.333333 16790.046878 20942.456800 25744.935321 33567. 67670   
0.500000 11807.544405 14505.000150 18380.449470 21421. 46200   
1.000000 104317.277560 127332.008735 149989.154201 178000. 50040   

          gdpPercap_1972 gdpPercap_1977 gdpPercap_1982 gdpPercap_1987 \
0. 00000 88569.346898 104459.358438 113553.768507 119649. 99409   
0,333333 45277,839976 53860. 56750 59679.634020 64436.912960   
0.500000 25377.727380 29056. 45370 31914.712050 35517.678220   
1.000000 215162.343140 241143. 12730 263388.781960 296825. 31210   

          gdpPercap_1992 gdpPercap_1997 gdpPercap_2002 gdpPercap_2007 
 0. 00000 92380. 47256 103772.937598 118590.929863 149577.357928  
0.333333 67918. 93220 80876.051580 102086.795210 122803.729520  
0. 00000 36310.666080 40723.538700 45564.308390 51403.028210  
1. 00000 315238.235970 346930.926170 385109.939210 427850.333420
```

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Selezione dei singoli valori

Supponiamo che Pandas sia stato importato nel vostro taccuino
e i dati sul PIL Gapminder per l'Europa sono stati caricati:

```python
import pandas as pd

data_europe = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')
```

Scrivi un'espressione per trovare il PIL Per Capita della Serbia nel 2007.

::::::::::::::: soluzione

## Soluzione

La selezione può essere effettuata utilizzando le etichette sia per la riga ("Serbia") che per la colonna ("gdpPercap_2007"):

```python
print(data_europe.loc['Serbia', 'gdpPercap_2007'])
```

L'output è

```output
9786.534714
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Estensione del lacciamento

1. Le due affermazioni seguenti producono lo stesso output?
2. Sulla base di questo,
   quale regola governa ciò che è incluso (o meno) in fette numeriche e fette denominate in Pandas?

```python
print(data_europe.iloc[0:2, 0:2])
print(data_europe.loc['Albania':'Belgium', 'gdpPercap_1952':'gdpPercap_1962'])
```

::::::::::::::: soluzione

## Soluzione

No, non producono lo stesso output! L'output della prima istruzione è:

```output
        gdpPercap_1952 gdpPercap_1957
country                                
Albania 1601.056136 1942.284244
Austria 6137.076492 8842.598030
```

La seconda dichiarazione reca:

```output
        gdpPercap_1952 gdpPercap_1957 gdpPercap_1962
country                                                
Albania 1601.056136 1942.284244 2312.888958
Austria 6137.076492 8842.598030 10750.721110
Belgio 8343.105127 9714.960623 10991.206760
```

Chiaramente, la seconda dichiarazione produce una colonna aggiuntiva e una riga aggiuntiva rispetto alla prima dichiarazione.\
Quale conclusione possiamo trarre? Vediamo che una parte numerica, 0:2, _omits_ l'indice finale (es. indice 2)
nell'intervallo fornito,
mentre una slice, 'gdpPercap_1952':'gdpPercap_1962', _include_ l'elemento finale.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Ricostruire I Dati

Spiega cosa fa ogni riga nel seguente breve programma:
cosa c'è in `first`, `second`, ecc.?

```python
first = pd.read_csv('data/gapminder_all.csv', index_col='country')
second = first[first['continent'] == 'Americas']
third = second.drop('Puerto Rico')
fourth = third.drop('continent', axis = 1)
fourth.to_csv('result.csv')
```

::::::::::::::: soluzione

## Soluzione

Passiamo attraverso questo pezzo di codice linea per riga.

```python
primo = pd.read_csv('data/gapminder_all.csv', index_col='country')
```

Questa linea carica il set di dati contenente i dati del PIL da tutti i paesi in un dataframe chiamato
`first`. Il parametro `index_col='country'` seleziona quale colonna usare come etichette delle righe
nel dataframe.

```python
second = first[first['continent'] == 'Americas']
```

Questa riga fa una selezione: solo quelle righe di `first` per le quali la colonna 'continente' corrisponde a
'Americas' sono estratte. Nota come l'espressione booleana all'interno delle parentesi,
`first['continent'] == 'Americas'`, viene usata per selezionare solo quelle righe dove l'espressione è vera.
Prova a stampare questa espressione! Puoi stampare anche i suoi singoli elementi True/False?
(suggerimento: prima assegna l'espressione a una variabile)

```python
terzo = secondo.drop('Puerto Rico')
```

Come suggerisce la sintassi, questa riga scende dalla riga `secondo` dove l'etichetta è 'Puerto Rico'. Il dataframe `third` risultante da
ha una riga inferiore al dataframe `secondo`.

```python
quarto = terzo.drop('continente', asse = 1)
```

Ancora una volta applichiamo la funzione di caduta, ma in questo caso stiamo cadendo non una riga ma un'intera colonna.
Per ottenere questo risultato, dobbiamo specificare anche il parametro `axis` (vogliamo eliminare la seconda colonna
che ha indice 1).

```python
fourth.to_csv('result.csv')
```

Il passo finale è quello di scrivere i dati su cui abbiamo lavorato in un file csv. Panda rende questo facile
con la funzione `to_csv()`. L'unico argomento richiesto alla funzione è il nome del file. Nota che il file
sarà scritto nella directory da cui hai iniziato la sessione di Jupyter o Python.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Selezione Indici

Spiega in termini semplici cosa fanno `idxmin` e `idxmax` nel programma breve qui sotto.
Quando usereste questi metodi?

```python
data = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')
print(data.idxmin())
print(data.idxmax())
```

::::::::::::::: soluzione

## Soluzione

Per ogni colonna in `data`, `idxmin` restituirà il valore dell'indice corrispondente al minimo di ogni colonna;
`idxmax` farà di conseguenza lo stesso per il valore massimo di ogni colonna.

È possibile utilizzare queste funzioni quando si desidera ottenere l'indice di riga del valore minimo/massimo e non il valore minimo/massimo effettivo.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Pratica con la selezione

Supponiamo che Pandas sia stato importato e che i dati sul PIL Gapminder per l'Europa siano stati caricati.
Scrivi un'espressione per selezionare ciascuno dei seguenti elementi:

1. PIL pro capite per tutti i paesi nel 1982.
2. PIL pro capite della Danimarca per tutti gli anni.
3. PIL pro capite per tutti i paesi per anni _dopo_ 1985.
4. GDP per capita for each country in 2007 as a multiple of
   GDP per capita for that country in 1952.

::::::::::::::: soluzione

## Soluzione

1:

```python
data['gdpPercap_1982']
```

2:

```python
data.loc['Danimarca',:]
```

3:

```python
data.loc[:,'gdpPercap_1985':]
```

I panda sono abbastanza intelligenti da riconoscere il numero alla fine dell'etichetta della colonna e non ti danno un errore, anche se non esiste una colonna chiamata `gdpPercap_1985`. Questo è utile se nuove colonne vengono aggiunte al file CSV più tardi.

4:

```python
data['gdpPercap_2007']/data['gdpPercap_1952']
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Molti modi di accesso

Ci sono almeno due modi per accedere a un valore o a una fetta di un DataFrame: per nome o indice.
Tuttavia, ce ne sono molti altri. Ad esempio, è possibile accedere a una singola colonna o riga come `DataFrame`
o come oggetto `Series`.

Suggerisci diversi modi di eseguire le seguenti operazioni su DataFrame:

1. Accedi a una singola colonna
2. Accedi a una singola riga
3. Accedi a un singolo elemento DataFrame
4. Accedi a più colonne
5. Accedi a più righe
6. Accedi a un sottoinsieme di righe e colonne specifiche
7. Accedi a un sottoinsieme di intervalli di righe e colonne

::::::::::::::: soluzione

## Soluzione

1\. Accedi a una singola colonna:

```python
# per nome
data["col_name"] # come dati della Serie
[["col_name"]] # come DataFrame

# per nome usando i dati .loc
. .loc["col_name"] # come dati serie
. T.loc[["col_name"].T # come DataFrame

# Notazione punto (Series)
dati. ol_name

# per indice (iloc)
data.iloc[:, col_index] # come dati della Serie
. loc[:, [col_index]] # come DataFrame

# usando una maschera
data.T[data.T.index == "col_name"].T
```

2\. Accedi a una singola riga:

```python
# per nome usando .loc
data.loc["row_name"] # come dati della Serie
. oc[["row_name"]] # come DataFrame

# per nome
data.T["row_name"] # come dati serie
.T[["row_name"]]. # come DataFrame

# per indice
data.iloc[row_index]   # come dati della Serie
. loc[[row_index]] # come DataFrame

# usando la maschera
data[data.index == "row_name"]
```

3\. Accedi a un singolo elemento Dataframe:

```python
# per colonna/nomi di righe
data["column_name"]["row_name"] # come dati della serie

[["col_name"]]. oc["row_name"] # come dati serie
[["col_name"]].loc[["row_name"]] # come dati DataFrame

. oc["row_name"]["col_name"] # come valore
data.loc[["row_name"]["col_name"] # come dati serie
.loc[["row_name"]["col_name"]["col_name"]] # come dati DataFrame

. oc["row_name", "col_name"] # come valore
data.loc[["row_name"], "col_name"] # come serie. Conserva l'indice. Il nome della colonna viene spostato in `.name`.
data.loc["row_name", ["col_name"]] # come serie. L'indice viene spostato in `. ame.` Imposta l'indice del nome della colonna.
dati. oc[["row_name"], ["col_name"]] # come DataFrame (preserva l'indice originale e il nome della colonna)

# per i nomi di colonna/riga: Notazione punto
data.col_name. ow_name

# per colonna/riga indices
data.iloc[row_index, col_index] # come valore
dati. loc[[row_index], col_index] # come serie. Preserva l'indice. Il nome della colonna viene spostato in `.name`
data.iloc[row_index, [col_index]] # come serie. L'indice viene spostato in `.name.` Imposta l'indice nel nome della colonna.
dati. loc[[row_index], [col_index]] # come DataFrame (conserva l'indice originale e il nome della colonna)

# nome della colonna + indice della riga
dati["col_name"][row_index]
dati. ol_name[row_index]
data["col_name"].iloc[row_index]

# indice colonna + nome riga
dati. loc[:, [col_index]].loc["row_name"] # come dati della serie
. loc[:, [col_index]].loc[["row_name"]] # come DataFrame

# usando le maschere
data[data.index == "row_name"].T[data.T.index == "col_name"].T
```

4\. Accedi a più colonne:

```python
# per nome
data[["col1", "col2", "col3"]]
data.loc[:, ["col1", "col2", "col3"]]

# per indice
data.iloc[:, [col1_index, col2_index, col3_index]]
```

5\. Accedi a più righe

```python
# per nome
data.loc[["row1", "row2", "row3"]]

# per indice
data.iloc[[row1_index, row2_index, row3_index]]
```

6\. Accedi a un sottoinsieme di righe e colonne specifiche

```python
# per i nomi
data.loc[["row1", "row2", "row3"], ["col1", "col2", "col3"]]

# per i dati degli indici
. loc[[[row1_index, row2_index, row3_index], [col1_index, col2_index, col3_index]]

# nomi di colonne + indici di riga
data[["col1", "col2", "col2", "col3"]]. loc[[[row1_index, row2_index, row3_index]]

# indici di colonna + nomi di righe
data.iloc[:, [col1_index, col2_index, col3_index]].loc[["row1", "row2", "row3"]]
```

7\. Accedi a un sottoinsieme di intervalli di righe e colonne

```python
# per nome
data.loc["row1":"row2", "col1":"col2"]

# per indice
data.iloc[row1_index:row2_index, col1_index:col2_index]

# nomi di colonne + dati degli indici di riga
. oc[:, "col1_name":"col2_name"].iloc[row1_index:row2_index]

# indici di colonna + nomi di righe
data.iloc[:, col1_index:col2_index].loc["row1":"row2"]
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Esplorare i metodi disponibili usando la funzione `dir()`

Python include una funzione `dir()` che può essere utilizzata per visualizzare tutti i metodi disponibili (funzioni) che sono integrati in un oggetto dati.  In Episodio 4, abbiamo usato alcuni metodi con una stringa. Ma possiamo vedere molti altri sono disponibili usando `dir()`:

```python
my_string = 'Ciao mondo!' # creazione di una stringa object 
dir(my_string)
```

Questo comando restituisce:

```python
['__add__',
...
'__subclasshook__',
'capitalize',
'casefold',
'center',
...
'upper',
'zfill']
```

Puoi usare `help()` o <kbd>Shift</kbd>+<kbd>Tab</kbd> per ottenere maggiori informazioni su cosa fanno questi metodi.

Supponiamo che Pandas sia stato importato e che i dati del PIL Gapminder per l'Europa siano stati caricati come `data`.  Quindi, utilizzare `dir()`
per trovare la funzione che stampa il PIL pro capite mediano in tutti i paesi europei per ogni anno che le informazioni sono disponibili.

::::::::::::::: soluzione

## Soluzione

Tra molte scelte, `dir()` elenca la funzione `median()` come una possibilità.  Così,

```python
data.median()
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Interpretazione

I confini della Polonia sono stabili dal 1945,
ma sono cambiati più volte negli anni precedenti.
Come si potrebbe gestire questo se si stava creando una tabella del PIL pro capite per la Polonia
per tutto il XX secolo?

::::::::::::::::::::::::::::::::::::::::::::::::::

[pandas-dataframe]: https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.html

[pandas-series]: https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.html

[numpy]: https://www.numpy.org/

:::::::::::::::::::::::::::::::::::::::: keypoints

- Usa `DataFrame.iloc[..., ...]` per selezionare i valori per posizione intera.
- Usa `:` da solo per significare tutte le colonne o tutte le righe.
- Seleziona più colonne o righe usando `DataFrame.loc` e una parte con nome.
- Il risultato dell'affettatura può essere utilizzato in ulteriori operazioni.
- Utilizzare i confronti per selezionare i dati in base al valore.
- Seleziona valori o NaN usando una maschera booleana.

::::::::::::::::::::::::::::::::::::::::::::::::::
