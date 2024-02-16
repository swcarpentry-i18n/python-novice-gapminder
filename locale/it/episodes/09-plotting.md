---
title: Tracciamento
teaching: 15
exercises: 15
---

::::::::::::::::::::::::::::::::::::::: objectives

- Crea un grafico di serie temporale che mostri un singolo set di dati.
- Crea un grafico a dispersione che mostra la relazione tra due set di dati.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::: domande

- Come posso tracciare i miei dati?
- Come posso salvare la mia trama per la pubblicazione?

::::::::::::::::::::::::::::::::::::::::::::::::::

## [`matplotlib`](https://matplotlib.org/) è la libreria di grafici scientifici più utilizzata in Python.

- Usa comunemente una sub-libreria chiamata [`matplotlib.pyplot`](https\://matplotlib.org/stable/tutorials/introduction ory/pyplot.html).
- Il notebook di Jupyter visualizzerà i grafici in linea di default.

```python
import matplotlib.pyplot as plt
```

- I grafici semplici sono quindi (equamente) semplici da creare.

```python
tempo = [0, 1, 2, 3]
posizione = [0, 100, 200, 300]

plt.plot(tempo, posizione)
plt.xlabel('Time (hr)')
plt.ylabel('Position (km)')
```

![](fig/9_simple_position_time_plot.svg){alt='Simple Position-Time Plot'}

:::::::::::::::::::::::::::::::::::::::::  callout

## Mostra Tutte Le Figure Aperte

Nel nostro esempio di Jupyter Notebook, l'esecuzione della cella dovrebbe generare la figura direttamente sotto il codice.
La figura è anche inclusa nel documento del notebook per la visione futura.
Tuttavia, altri ambienti Python come una sessione interattiva Python avviata da un terminale
o uno script Python eseguito dalla riga di comando richiedono un comando aggiuntivo per visualizzare la figura.

Istruisci `matplotlib` per mostrare una figura:

```python
plt.show()
```

Questo comando può essere usato anche all'interno di un notebook - per esempio, per visualizzare più figure
se più sono creati da una singola cella.

::::::::::::::::::::::::::::::::::::::::::::::::::

## Traccia i dati direttamente da un [`Pandas dataframe`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html).

- Possiamo anche tracciare [Pandas dataframes](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.html).
- Prima di tracciare, convertiamo le intestazioni delle colonne da un tipo di dati `string` a `integer`, poiché rappresentano valori numerici,
  usando [str.replace()](https\://pandas.pydata.org/docs/reference/api/pandas.Series.str.replace. tml) per rimuovere il prefisso `gpdPercap_`
  e poi [astype(int)](https\://pandas.pydata.org/docs/reference/api/pandas.Series.astype. tml)
  per convertire la serie di valori di stringa (`['1952', '1957', ..., '2007']`) in una serie di interi: `[1925, 1957, ..., 2007]`.

```python
import panda as pd

data = pd.read_csv('data/gapminder_gdp_oceania. sv', index_col='country')

# Estrai anno dagli ultimi 4 caratteri di ogni colonna nome
# I nomi delle colonne attuali sono strutturati come 'gdpPercap_(anno)', 
# quindi vogliamo mantenere la parte (anno) solo per chiarezza quando si tracciano PIL vs. anni
# Per fare questo usiamo sostituire(), che rimuove dalla stringa i caratteri indicati nell'argomento
# Questo metodo funziona sulle stringhe, quindi usiamo replace() da Pandas Series. tr funzioni di stringhe vettorializzate

anni = dati. olumns.str.replace('gdpPercap_', '')

# Converti i valori dell'anno in interi, salvando i risultati torna al dataframe

data.columns = years.astype(int)

data.loc['Australia'].plot()
```

![](fig/9_gdp_australia.svg){alt='GDP plot for Australia'}

## Selezionare e trasformare i dati, quindi tracciarli.

- Per impostazione predefinita, [`DataFrame.plot`](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.plot.html#pandas.DataFrame.plot) traccia con le righe come asse X.
- Possiamo trasporre i dati al fine di tracciare più serie.

```python
data.T.plot()
plt.ylabel('PIL pro capite')
```

![](fig/9_gdp_australia_nz.svg){alt='GDP plot for Australia and New Zealand'}

## Molti stili di trama sono disponibili.

- Per esempio, fai un grafico a barre usando uno stile più sofisticato.

```python
plt.style.use('ggplot')
data.T.plot(kind='bar')
plt.ylabel('PIL pro capite')
```

![](fig/9_gdp_bar.svg){alt='GDP barplot for Australia'}

## I dati possono anche essere tracciati chiamando direttamente la funzione `matplotlib` `plot`.

- Il comando è `plt.plot(x, y)`
- Il colore e il formato dei marcatori possono anche essere specificati come un argomento opzionale aggiuntivo e. ., `b-` è una linea blu, `g--` è una linea tratteggiata verde.

## Ottieni dati Australia dal dataframe

```python
anni = data.columns
gdp_australia = data.loc['Australia']

plt.plot(anni, gdp_australia, 'g--')
```

![](fig/9_gdp_australia_formatted.svg){alt='GDP formatted plot for Australia'}

## Può tracciare molti set di dati insieme.

```python
# Seleziona due paesi' di dati.
gdp_australia = data.loc['Australia']
gdp_nz = data.loc['Nuova Zelanda']

# Trama con indicatori di colore diverso.
plt. lot(years, gdp_australia, 'b-', label='Australia')
plt.plot(years, gdp_nz, 'g-', label='Nuova Zelanda')

# Create legend.
plt.legend(loc='upper left')
plt.xlabel('Year')
plt.ylabel('GDP pro capite ($)')
```

:::::::::::::::::::::::::::::::::::::::::  callout

## Aggiungere una leggenda

Spesso quando si tracciano più set di dati sulla stessa figura è auspicabile avere
una leggenda che descriva i dati.

Questo può essere fatto in `matplotlib` in due fasi:

- Fornire un'etichetta per ogni set di dati nella figura:

```python
plt.plot(years, gdp_australia, label='Australia')
plt.plot(years, gdp_nz, label='Nuova Zelanda')
```

- Costruisci `matplotlib` per creare la leggenda.

```python
plt.legend()
```

Per impostazione predefinita, matplotlib tenterà di posizionare la leggenda in una posizione adatta. Se
preferisce specificare una posizione che può essere fatta con l'argomento `loc=`, e. per posizionare
la legenda nell'angolo in alto a sinistra del grafico, specificare `loc='in alto a sinistra'`

::::::::::::::::::::::::::::::::::::::::::::::::::

![](fig/9_gdp_australia_nz_formatted.svg){alt='GDP formatted plot for Australia and New Zealand'}

- Tracciare una trama disperdente correlando il PIL dell'Australia e della Nuova Zelanda
- Usa `plt.scatter` o `DataFrame.plot.scatter`

```python
plt.scatter(gdp_australia, gdp_nz)
```

![](fig/9_gdp_correlation_plt.svg){alt='Correlazione PIL usando plt.scatter'}

```python
data.T.plot.scatter(x = 'Australia', y = 'Nuova Zelanda')
```

![](fig/9_gdp_correlation_data.svg){alt='Correlazione PIL utilizzando data.T.plot.scatter'}

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Minima e Maxima

Compilare gli spazi vuoti sottostanti per tracciare il PIL minimo pro capite nel tempo
per tutti i paesi europei.
Modificarlo nuovamente per tracciare il PIL massimo pro capite nel tempo per l'Europa.

```python
data_europe = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')
data_europe.____.plot(label='min')
data_europe.____
plt.legend(loc='best')
plt.xticks(rotation=90)
```

::::::::::::::: soluzione

## Soluzione

```python
data_europe = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')
data_europe.min().plot(label='min')
data_europe.max().plot(label='max')
plt.legend(loc='best')
plt.xticks(rotation=90)
```

![](fig/9_minima_maxima_solution.png){alt='Minima Maxima Solution'}

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Correlazioni

Modificare l'esempio nelle note per creare un grafico a dispersione che mostri
il rapporto tra il PIL minimo e il PIL massimo pro capite
tra i paesi asiatici per ogni anno nel set di dati.
Che rapporto vedete (se ce ne sono)?

::::::::::::::: soluzione

## Soluzione

```python
data_asia = pd.read_csv('data/gapminder_gdp_asia.csv', index_col='country')
data_asia.describe().T.plot(kind='scatter', x='min', y='max')
```

![](fig/9_correlations_solution1.svg){alt='Correlations Solution 1'}

Nessuna correlazione particolare può essere vista tra i valori gdp minimi e massimi
anno su anno. Sembra che le fortune dei paesi asiatici non salgano e cadano insieme.

:::::::::::::::::::::::::

Si potrebbe notare che la variabilità nel massimo è molto superiore a
quella del minimo.  Dai un'occhiata agli indici massimi e massimi:

```python
data_asia = pd.read_csv('data/gapminder_gdp_asia.csv', index_col='country')
data_asia.max().plot()
print(data_asia.idxmax())
print(data_asia.idxmin())
```

::::::::::::::: soluzione

## Soluzione

![](fig/9_correlations_solution2.png){alt='Correlations Solution 2'}

Sembra che la variabilità di questo valore sia dovuta ad un brusco calo dopo il 1972.
Forse qualche geopolitica in gioco? Data la posizione dominante dei paesi produttori di petrolio,
forse l'indice di greggio Brent farebbe un confronto interessante?
Mentre il Myanmar ha costantemente il gdp più basso, la nazione gdb più alta ha variato
in particolare.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Più Correlazioni

Questo breve programma crea una trama che mostra
la correlazione tra PIL e speranza di vita per il 2007,
normalizzando la dimensione marker per popolazione:

```python
data_all = pd.read_csv('data/gapminder_all.csv', index_col='country')
data_all.plot(kind='scatter', x='gdpPercap_2007', y='lifeExp_2007',
              s=data_all['pop_2007']/1e6)
```

Utilizzando l'aiuto online e altre risorse,
spiega cosa fa ogni argomento a `plot`.

::::::::::::::: soluzione

## Soluzione

![](fig/9_more_correlations_solution.svg){alt='More Correlations Solution'}

Un buon posto da guardare è la documentazione per la funzione grafico -
help(data_all.plot).

tipo - Come visto già questo determina il tipo di trama da disegnare.

x e y - Un nome o indice di colonna che determina quali dati saranno
posizionati sugli assi x e y della trama

s - I dettagli per questo si trovano nella documentazione di plt.scatter.
Un unico numero o un valore per ogni punto di dati. Determina la dimensione
dei punti tracciati.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## Salvataggio del grafico in un file

Se sei soddisfatto della trama che vedi potresti voler salvare in un file,
forse per includerlo in una pubblicazione. C'è una funzione nel modulo
matplotlib.pyplot che realizza questo:
[savefig](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.savefig.html).
Chiamare questa funzione, ad esempio con

```python
plt.savefig('my_figure.png')
```

salverà la figura corrente nel file `my_figure.png`. Il formato di file
verrà automaticamente dedotto dall'estensione del nome del file (gli altri formati
sono pdf, ps, eps e svg).

Nota che le funzioni in `plt` si riferiscono a una variabile globale di figura
e dopo che una figura è stata visualizzata sullo schermo (e. . with `plt.show`) Il matplotlib
farà riferimento a questa variabile ad una nuova figura vuota.
Pertanto, assicurati di chiamare `plt.savefig` prima che il grafico sia visualizzato su
lo schermo, altrimenti potresti trovare un file con un grafico vuoto.

Quando si utilizzano dataframe, i dati vengono spesso generati e tracciati sullo schermo in una riga.
Oltre a usare `plt.savefig`, possiamo salvare un riferimento alla figura attuale
in una variabile locale (con `plt. cf`) e chiama il metodo di classe `savefig` da
quella variabile per salvare la figura su file.

```python
data.plot(kind='bar')
fig = plt.gcf() # ottieni la figura corrente
fig.savefig('my_figure.png')
```

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## Rendere i tuoi appezzamenti accessibili

Ogni volta che si generano grafici per andare in una carta o una presentazione, ci sono alcune cose che puoi fare per assicurarsi che tutti possano capire i tuoi lotti.

- Assicurati sempre che il tuo testo sia abbastanza grande da leggere. Usa il parametro `fontsize` in `xlabel`, `ylabel`, `title`, e `legend`, e [`tick_params` con `labelsize`](https://matplotlib.org/stable/api/_as_gen/matplotlib.axes.Axes.tick_params.html) per aumentare la dimensione del testo dei numeri sui tuoi assi.
- Allo stesso modo, si dovrebbe rendere il grafico elementi facile da vedere. Usa `s` per aumentare la dimensione dei tuoi marcatori di scatterplot e `linewidth` per aumentare le dimensioni delle tue linee di trama.
- Usando il colore (e nient'altro) per distinguere tra diversi elementi della trama renderà i tuoi grafici illeggibili a chiunque sia colorcieco, o che capita di avere una stampante ufficio in bianco e nero. Per le righe, il parametro `linestyle` ti permette di utilizzare diversi tipi di linee. Per scatterplot, `marker` ti permette di cambiare la forma dei tuoi punti. Se non sei sicuro dei tuoi colori, puoi usare [Coblis](https\://www\.color-blindness. om/coblis-color-blindness-simulator/) o [Color Oracle](https://colororacle.org/) per simulare quello che i tuoi grafici assomiglierebbero a quelli con la cecità del colore.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- [`matplotlib`](https://matplotlib.org/) è la libreria di grafici scientifici più utilizzata in Python.
- Tracciare i dati direttamente da un dataframe Pandas.
- Selezionare e trasformare i dati, quindi tracciarli.
- Sono disponibili molti stili di trama: vedi la [Python Graph Gallery](https://python-graph-gallery.com/matplotlib/) per ulteriori opzioni.
- Può tracciare molti set di dati insieme.

::::::::::::::::::::::::::::::::::::::::::::::::::
