---
title: Funzioni Scritte
teaching: 10
exercises: 15
---

::::::::::::::::::::::::::::::::::::::: objectives

- Spiegare e identificare la differenza tra la definizione delle funzioni e la chiamata delle funzioni.
- Scrivi una funzione che richiede un piccolo numero fisso di argomenti e produce un singolo risultato.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::: domande

- Come posso creare le mie funzioni?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Rompere i programmi in funzioni per renderli più facili da capire.

- Gli esseri umani possono mantenere solo alcuni elementi nella memoria di lavoro alla volta.
- Comprendere idee più grandi / più complicate comprendendo e combinando pezzi.
  - Componenti in una macchina.
  - Lemmi quando si dimostrano teoremi.
- Le funzioni servono lo stesso scopo in programmi.
  - _Encapsulate_ complessità in modo da poterla trattare come una singola "cosa".
- Abilita anche il _riutilizzo_.
  - Scrivi una volta, usa molte volte.

## Definisci una funzione usando `def` con un nome, parametri e un blocco di codice.

- Inizia la definizione di una nuova funzione con `def`.
- Seguito dal nome della funzione.
  - Deve obbedire alle stesse regole dei nomi delle variabili.
- Quindi _parametri_ tra parentesi.
  - Svuota parentesi se la funzione non richiede alcun input.
  - Ne discuteremo in dettaglio tra un attimo.
- Poi un colon.
- Poi un blocco di codice frastagliato.

```python
def print_greeting():
    print('Hello!')
    print('Il tempo è bello oggi.')
    print('Destra?')
```

## La definizione di una funzione non viene eseguita.

- La definizione di una funzione non viene eseguita.
  - Come assegnare un valore a una variabile.
- È necessario chiamare la funzione per eseguire il codice che contiene.

```python
print_greeting()
```

```output
Ciao!
```

## Gli argomenti in una chiamata di funzione sono abbinati ai suoi parametri definiti.

- Le funzioni sono più utili quando possono operare su dati diversi.
- Specifica i _parametri_ quando si definisce una funzione.
  - Queste diventano variabili quando la funzione viene eseguita.
  - Sono assegnati gli argomenti nella chiamata (cioè i valori passati alla funzione).
  - Se non si nominano gli argomenti quando li si utilizza nella chiamata, gli argomenti saranno abbinati ai parametri
    nell'ordine in cui i parametri sono definiti nella funzione.

```python
def print_date(anno, mese, giorno):
    si è unito = str(anno) + '/' + str(mese) + '/' + str(giorno)
    print(joined)

print_date(1871, 3, 19)
```

```output
1871/3/19
```

Oppure, possiamo nominare gli argomenti quando chiamiamo la funzione, che ci permette di
specificarli in qualsiasi ordine e aggiunge chiarezza al sito di chiamata; altrimenti come
si sta leggendo il codice che potrebbero dimenticare se il secondo argomento è il mese
o il giorno per esempio.

```python
print_date(mese=3, giorno=19, anno=1871)
```

```output
1871/3/19
```

- Via [Twitter](https://twitter.com/minisciencegirl/status/6934860889632705):
  `()` contiene gli ingredienti per la funzione
  mentre il corpo contiene la ricetta.

## Le funzioni possono restituire un risultato al loro chiamante usando `return`.

- Usa `return ...` per restituire un valore al chiamante.
- Può verificarsi ovunque nella funzione.
- Ma le funzioni sono più facili da capire se `return` si verifica:
  - All'inizio per gestire casi speciali.
  - Alla fine, con un risultato finale.

```python
def media(valori):
    if len(values) == 0:
        return Nessuno
    return sum(values) / len(values)
```

```python
a = media([1, 3, 4])
print('media dei valori effettivi:', a)
```

```output
media dei valori effettivi: 2,6666666666666665
```

```python
print('media della lista vuota:', media([]))
```

```output
media della lista vuota: Nessuno
```

- Ricorda: [ogni funzione restituisce qualcosa](04-built-in.md).
- Una funzione che non esplicitamente `restituisce` un valore restituisce automaticamente `None`.

```python
result = print_date(1871, 3, 19)
print('result of call is:', result)
```

```output
1871/3/19
risultato della chiamata è: Nessuno
```

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Identificazione Errori Di Sintassi

1. Leggere il codice qui sotto e cercare di identificare quali sono gli errori
   _senza_ eseguirlo.
2. Eseguire il codice e leggere il messaggio di errore.
   È un `SyntaxError` o un `IndentationError`?
3. Correggi l'errore.
4. Ripetere i passaggi 2 e 3 finché non si sono risolti tutti gli errori.

```python
def another_function
  print("Gli errori di sintassi sono fastidiosi. )
   print("Ma almeno python ci parla di loro!")
  print("Quindi di solito non sono troppo difficili da risolvere.")
```

::::::::::::::: soluzione

## Soluzione

```python
def another_function():
  print("Gli errori di sintassi sono fastidiosi. )
  print("Ma almeno Python ci parla di loro!")
  print("Quindi di solito non sono troppo difficili da risolvere.")
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Definizione e uso

Cosa stampa il seguente programma?

```python
def report(pressione):
    print('pressure is', pressione)

print('calling', report, 22.5)
```

::::::::::::::: soluzione

## Soluzione

```output
chiamata <function report at 0x7fd128ff1bf8> 22.5
```

Una chiamata funzione ha sempre bisogno di parentesi, altrimenti si ottiene l'indirizzo di memoria dell'oggetto funzione. Quindi, se volevamo chiamare la funzione denominata rapporto, e dargli il valore 22. per riferire su, potremmo avere la nostra funzione chiamata come segue

```python
print("calling")
report(22.5)
```

```output
chiamare la pressione
è 22.5
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Ordine delle operazioni

1. Cosa c'è di sbagliato in questo esempio?

```python
risultato = print_time(11, 37, 59)

def print_time(hour, minute, second):
   time_string = str(hour) + ':' + str(minuto) + ':' + str(secondo)
   print(time_string)
```

2. Dopo aver risolto il problema sopra, spiegare perché eseguire questo codice di esempio:

```python
result = print_time(11, 37, 59)
print('result of call is:', result)
```

dà questo output:

```output
11:37:59 Il risultato della chiamata
è: Nessuno
```

3. Perché il risultato della chiamata `None`?

::::::::::::::: soluzione

## Soluzione

1. Il problema con l'esempio è che la funzione `print_time()` è definita _dopo_ la chiamata alla funzione è fatta. Python
   non sa come risolvere il nome `print_time` poiché non è ancora stato definito e solleverà un `NameError` e. .,
   `NameError: name 'print_time' non è definito`

2. La prima riga di output `11:37:59` è stampata dalla prima riga di codice, `result = print_time(11, 37, 59)` che lega il valore
   restituito invocando `print_time` alla variabile `result`. La seconda riga è dalla seconda chiamata di stampa per stampare il contenuto
   della variabile `result`.

3. `print_time()` non esplicitamente `return` un valore, quindi restituisce automaticamente `None`.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Incapsulamento

Compila gli spazi vuoti per creare una funzione che richiede un singolo nome di file come argomento,
carica i dati nel file chiamato dall'argomento,
e restituisce il valore minimo in quei dati.

```python
import panda as pd

def min_in_data(____):
    data = ____
    return ____
```

::::::::::::::: soluzione

## Soluzione

```python
importa panda come pd

def min_in_data(nome file):
    data = pd.read_csv(nome file)
    return data.min()
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Trova il primo

Compila gli spazi vuoti per creare una funzione che prende un elenco di numeri come argomento
e restituisce il primo valore negativo nella lista.
Cosa fa la tua funzione se la lista è vuota? Cosa succede se la lista non ha numeri negativi?

```python
def first_negative(values):
    for v in ______:
        if ____:
            return ____
```

::::::::::::::: soluzione

## Soluzione

```python
def first_negative(values):
    for v in values:
        if v < 0:
            return v
```

Se una lista vuota o una lista con tutti i valori positivi vengono passati a questa funzione, restituisce `None`:

```python
my_list = []
print(first_negative(my_list))
```

```output
Nessuno
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Chiamata per nome

In precedenza abbiamo visto questa funzione:

```python
def print_date(anno, mese, giorno):
    si unisce = str(anno) + '/' + str(mese) + '/' + str(giorno)
    print(joined)
```

Abbiamo visto che possiamo chiamare la funzione usando _argomenti chiamati_, così:

```python
print_date(giorno=1, mese=2, anno=2003)
```

1. Cosa fa `print_date(day=1, month=2, year=2003)` print?
2. Quando hai visto una funzione chiamata come questa prima?
3. Quando e perché è utile chiamare le funzioni in questo modo?

::::::::::::::: soluzione

## Soluzione

1. `2003/2/1`

2. Abbiamo visto esempi di utilizzo di _argomenti denominati_ quando si lavora con la libreria pandas. Ad esempio, quando si legge in un dataset
   usando `data = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')`, l'ultimo argomento `index_col` è un argomento chiamato
   .

3. L'uso di argomenti chiamati può rendere il codice più leggibile poiché si può vedere dalla funzione chiamata quale nome hanno i diversi argomenti
   all'interno della funzione. Può anche ridurre le possibilità di passare gli argomenti nell'ordine sbagliato, poiché utilizzando gli argomenti
   di nome l'ordine non importa.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Incapsulamento di un blocco If/Stampa

Il codice sottostante verrà eseguito su una stampante per etichette per uova di pollo.  Una scala digitale riferirà una massa di uova di pollo (in grammi)
al computer e poi il computer stamperà un'etichetta.

```python
import random
for i in range(10):

    # simulando la massa di un uovo di pollo
    # la massa (casuale) sarà 70 +/- 20 grammi
    massa = 70 + 20. * (2.0 * random.random() - 1. )

    print(massa)

    # macchine per il dimensionamento dell'uovo stampa un'etichetta
    se massa >= 85:
        print("jumbo")
    massa dell'elif >= 70:
        print("large")
    massa dell'elif < 70 e massa >= 55:
        print("medium")
    else:
        print("small")
```

Il blocco if, che classifica le uova, potrebbe essere utile in altre situazioni,
per evitare di ripeterla, potremmo piegarla in una funzione, `get_egg_label()`.
Rivedere il programma per utilizzare la funzione ci darebbe questo:

```python
# versione rivista
import random
for i in range(10):

    # simulando la massa di un uovo di pollo
    # la massa (casuale) sarà 70 +/- 20 grammi
    massa = 70 + 20. * (2.0 * random.random() - 1.0)

    print(mass, get_egg_label(mass))

```

1. Crea una definizione di funzione per `get_egg_label()` che funzionerà con il programma rivisto sopra.  Nota che il valore di ritorno della funzione `get_egg_label()` sarà importante. L'output di esempio dal programma di cui sopra sarebbe `71.23 large`.
2. Un uovo sporco potrebbe avere una massa superiore a 90 grammi, e un uovo rovinato o rotto probabilmente avrà una massa che è inferiore a 50 grammi.  Modifica la tua funzione `get_egg_label()` per tenere conto di queste condizioni di errore. L'uscita del campione potrebbe essere `25 troppo leggera, probabilmente viziata`.

::::::::::::::: soluzione

## Soluzione

```python
def get_egg_label(massa):
    # il dimensionamento dell'uovo stampa un'etichetta
    l'etichetta = "Unlabelled"
    if mass >= 90:
        egg_label = "warning: egg may be dirty"
    elif mass >= 85:
        egg_label = "jumbo"
    elif mass >= 70:
        egg_label = "large"
    elif massa < 70 e massa >= 55:
        egg_label = "medium"
    elif massa < 50:
        egg_label = "too light, probabilmente viziato"
    altro:
        egg_label = "small"
    restituire egg_label
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Analisi Dei Dati Incapsulante

Supponiamo che sia stato eseguito il seguente codice:

```python
import pandas as pd

data_asia = pd.read_csv('data/gapminder_gdp_asia.csv', index_col=0)
japan = data_asia.loc['Japan']
```

1. Completare le dichiarazioni di seguito riportate per ottenere il PIL medio per il Giappone
   nel corso degli anni indicati per gli anni '80.

```python
anno = 1983
gdp_decade = 'gdpPercap_' + str(year // ____)
avg = (japan.loc[gdp_decade + ___] + japan.loc[gdp_decade + ___]) / 2
```

2. Riassume il codice sopra in una singola funzione.

```python
def avg_gdp_in_decade(country, continent, year):
    data_countries = pd.read_csv('data/gapminder_gdp_'+___+'.csv',delimiter=',',index_col=0)
    ____
    ____
    ____
    return avg
```

3. Come generalizzare questa funzione
   se non sapeste in anticipo quali anni specifici si sono verificati come colonne dei dati?
   Ad esempio, se avessimo anche dati da anni che terminano in 1 e 9 per ogni decennio?
   (Suggerimento: usa le colonne per filtrare quelle che corrispondono al decennio,
   invece di enumerarle nel codice.)

::::::::::::::: soluzione

## Soluzione

1. Il PIL medio del Giappone negli anni '80 è calcolato con:

```python
anno = 1983
gdp_decade = 'gdpPercap_' + str(anno // 10)
avg = (japan.loc[gdp_decade + '2'] + japan.loc[gdp_decade + '7']) / 2
```

2. Tale codice come funzione è:

```python
def avg_gdp_in_decade(country, continent, year):
    data_countries = pd.read_csv('data/gapminder_gdp_' + continente + '.csv', index_col=0)
    c = data_country. oc[country]
    gdp_decade = 'gdpPercap_' + str(year // 10)
    avg = (c. oc[gdp_decade + '2'] + c.loc[gdp_decade + '7'])/2
    return avg
```

3. Per ottenere la media per gli anni pertinenti, abbiamo bisogno di loop su di loro:

```python
def avg_gdp_in_decade(country, continent, year):
    data_countries = pd.read_csv('data/gapminder_gdp_' + continent + '. sv', index_col=0)
    c = data_country. oc[country]
    gdp_decade = 'gdpPercap_' + str(anno // 10)
    totale = 0.
    num_years = 0
    per yr_header in c. ndex: # c's index contiene gli anni segnalati
        se yr_header. tartswith(gdp_decade):
            totale = totale + c. oc[yr_header]
            num_years = num_years + 1
    rendimento totale/num_years
```

La funzione può ora essere chiamata da:

```python
avg_gdp_in_decade('Japan','asia',1983)
```

```output
20880.023800000003
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Simulazione di un sistema dinamico

In matematica, un [sistema dinamico](https://en.wikipedia.org/wiki/Dynamical_system) è un sistema
in cui una funzione descrive la dipendenza temporale di un punto in uno spazio geometrico. Un esempio canonico
di un sistema dinamico è la [mappa logistica](https\://en.wikipedia. rg/wiki/Logistic_map),
un modello di crescita che calcola una nuova densità di popolazione (tra 0 e 1) basata sulla densità
attuale. Nel modello, il tempo richiede valori discreti 0, 1, 2, ...

1. Definire una funzione chiamata `logistic_map` che richiede due input: `x`, che rappresenta la popolazione corrente
   (al tempo `t`), e un parametro `r = 1`. Questa funzione dovrebbe restituire un valore
   che rappresenta lo stato del sistema (popolazione) al momento `t + 1`, utilizzando la funzione di mappatura:

`f(t+1) = r * f(t) * [1 - f(t)]`

2. Usando un ciclo `for` o `while`, iterate la funzione `logistic_map` definita nella parte 1, iniziando
   da una popolazione iniziale di 0. , per un periodo di tempo `t_final = 10`. Memorizza il risultato intermedio
   in una lista in modo che dopo la fine del ciclo hai accumulato una sequenza di valori
   che rappresenta lo stato della mappa logistica a volte `t = [0,1,. .,t_final]` (11 valori in totale).
   Stampa questa lista per vedere l'evoluzione della popolazione.

3. Incapsulare la logica del tuo ciclo in una funzione chiamata `iterate` che prende la popolazione iniziale
   come primo input, il parametro `t_final` come secondo input e il parametro
   `r` come terzo input. La funzione dovrebbe restituire l'elenco dei valori che rappresentano lo stato di
   la mappa logistica a volte `t = [0,1,...,t_final]`. Eseguire questa funzione per periodi `t_final = 100`
   e `1000` e stampare alcuni dei valori. La popolazione sta tendendo verso uno stato stabile?

::::::::::::::: soluzione

## Soluzione

1. ```python
   ```

def logistic_map(x, r):
return r \* x \* (1 - x)

````

2. ```python
initial_population = 0.5
t_final = 10
r = 1.
popolazione = [initial_population]
per t in range(t_final):
    population.append( logistic_map(popolazione[t], r) )
````

3. ```python
   ```

def iterate(initial_population t_final, r):
population = [initial_population]
for t in range(t_final):
population.append( logistic_map(population[t], r)
return population

for period in (10, 100, 1000):
population = iterate(0.5, period, 1)
print(population[-1])

```

``output
0.06945089389714401
0.009395779870614648
0.0009913908614406382
```

La popolazione sembra avvicinarsi a zero.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## Utilizzando funzioni con condizionali in Panda

Le funzioni spesso contengono condizionali.  Ecco un breve esempio che
indicherà in quale quartile l'argomento si basa sui valori
codificati a mano per i punti di taglio del quartile.

```python
def calculate_life_quartile(exp):
    if exp < 58. 1:
        # Questa osservazione è nel primo quartile
        return 1
    elif exp >= 58. 1 ed exp < 67. 5:
        # Questa osservazione è nel secondo quartile
       restituisce 2
    exp elif >= 67. 5 ed exp < 71. 0:
        # Questa osservazione è nel terzo quartile
       restituisce 3
    elif exp >= 71. 0:
        # Questa osservazione è nel quarto quartile
       return 4
    else:
        # Questa osservazione ha dati errati
       return Nessuno

calculate_life_quartile(62.5)
```

```output
2
```

Questa funzione sarebbe tipicamente utilizzata all'interno di un ciclo `for`, ma Pandas ha
un diverso, modo più efficiente di fare la stessa cosa, e cioè da
_applicando_ una funzione a un dataframe o una parte di un dataframe.  Qui
è un esempio, usando la definizione qui sopra.

```python
data = pd.read_csv('data/gapminder_all.csv')
data['life_qrtl'] = data['lifeExp_1952'].apply(calculate_life_quartile)
```

C'è molto in quella seconda linea, quindi prendiamolo pezzo per pezzo.
Sul lato destro del `=` iniziamo con `data['lifeExp']`, che è la colonna
nel dataframe chiamato `data` con l'etichetta `lifExp`.  Usiamo il `apply()`
per fare quello che dice, applica il `calculate_life_quartile` al valore
di questa colonna per ogni riga del dataframe.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Rompere i programmi in funzioni per renderli più facili da capire.
- Definisci una funzione usando `def` con un nome, parametri e un blocco di codice.
- La definizione di una funzione non viene eseguita.
- Gli argomenti in una chiamata di funzione sono abbinati ai suoi parametri definiti.
- Le funzioni possono restituire un risultato al loro chiamante usando `return`.

::::::::::::::::::::::::::::::::::::::::::::::::::
