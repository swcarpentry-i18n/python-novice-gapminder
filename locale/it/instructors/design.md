---
title: Lezione Design
---

:::::::::::::::::::::::::::::::::::::::::  callout

## Aiuto Desiderato

\*\*Stiamo compilando gli esercizi [below](#stage-3-learning-plan)
per rendere il piano di lezione più concreto.
I contributi (sia sotto forma di richieste di pull con esercizi completi,
e commenti su esercizi specifici, ordinazioni e tempi) sono molto apprezzati.

::::::::::::::::::::::::::::::::::::::::::::::::::

## Processo Usato

> Il consiglio di Michael Pollan se ha insegnato R o Python programmazione:
>
> 1. Scrivi codice.
> 2. Non troppo.
> 3. Principalmente trama.
>
> — [Michael Koontz](https://twitter.com/_mikoontz/status/758021742078025728)
> {: .quotation}

Questa lezione è stata sviluppata utilizzando una variante snellita del processo "Understanding by Design".
Le sezioni principali sono:

1. Ipotesi su pubblico, tempo, ecc.
   (l'attuale progetto include anche alcune conclusioni e decisioni in questa sezione* che dovrebbero essere rifatte.)

2. Risultati desiderati:
   obiettivi generali, valutazioni sommarie alla granularità di mezza giornata, ciò che gli studenti
   saranno in grado di fare, ciò che gli studenti sapranno.

3. Piano di apprendimento:
   ogni episodio ha un titolo che riassume ciò che sarà coperto,
   poi stima il tempo che sarà speso per l'insegnamento e per gli esercizi,
   mentre gli esercizi sono dati come punti.

## Fase 1: Ipotesi

- Pubblico
  - Studenti laureati in discipline numerate dalla cosmologia all'archeologia
  - Chi ha manipolato i dati in fogli di calcolo e con strumenti interattivi come SAS
  - Ma _non_ hanno programmato oltre CPD (copia-pasta-disperazione)
- Vincoli
  - Un giorno intero 09:00-16:30
    - 06:15 tempo di lezione
    - 0:45 pranzo
    - 0:30 totale per due pause caffè
  - Gli studenti utilizzano installazioni native sulle proprie macchine
    - Può utilizzare VM o risorse cloud a discrezione degli insegnanti
    - Ma deve mantenere l'installazione locale nativa come opzione
  - Nessuna dipendenza da altri moduli di carpenteria
    - In particolare, non richiede la conoscenza del controllo della shell o della versione
  - Usa il taccuino di Jupyter
    - Strumento autentico utilizzato da molti istruttori
    - Non c'è davvero un'alternativa
    - E significa che anche le persone che hanno visto un po' di Python prima di
      probabilmente impareranno qualcosa
- Esempio Motivante
  - Creazione di lotti 2D adatti per l'inclusione in carte
  - Appelli a quasi tutti
  - Rende la lezione utilizzabile da entrambi i Carpentries
    - E significa che anche le persone che hanno visto un po' di Python prima di
      probabilmente impareranno qualcosa
- Dati
  - Usa i dati gapminder in tutto
  - Ma rompere in più file per continente
    - Per rendere la visualizzazione di output da esempi tidier
      (ad esempio, utilizzare Australia/Nuova Zelanda, che è solo due righe)
    - E consentire esempi che mostrano l'uso di più set di dati
- Concentrati su Panda invece di NumPy
  - Rende la lezione utilizzabile sia da carpenteria dati che da carpenteria software
  - È probabile che i veri novizi vogliano l'analisi dei dati
  - E le persone con qualche esperienza precedente:
    - accetterà l'analisi dei dati come compito autentico,
    - ed è improbabile che abbiano incontrato Pandas,
      così avranno ancora qualcosa di utile dalla lezione
- Le sfide per lo più _non_ saranno "scrivi questo codice da zero"
  - Vuole un sacco di esercizi brevi che possono essere attendibilmente finiti in tempo assegnato
  - Quindi utilizzare MCQs, fill-in-the-blanks, Parsons Problems, "modificare questo codice", ecc.

## Fase 2: Risultati Desiderati

### Domande

Come faccio io...

- ...leggi i dati delle tabelle?
- ...tracciare un singolo vettore di valori?
- ...creare una trama di serie temporale?
- ...creare un grafico per ciascuno di più set di dati?
- ...ottenere dati extra da un singolo set di dati per il tracciato?
- ...scrivere programmi che posso leggere e riutilizzare in futuro?

### Abilità

Io posso...

- ...scrivi script brevi usando loop e condizionali.
- ...scrivere funzioni con un numero fisso di parametri che restituiscono un singolo risultato.
- ...importa le librerie usando gli alias e fai riferimento al contenuto delle librerie.
- ...fare semplice estrazione di dati e formattazione utilizzando Pandas.

### Concetti

Lo so...

- ...che un programma è un pezzo di attrezzatura di laboratorio che implementa un'analisi
  - Deve essere convalidato/calibrato prima/durante l’uso
  - Rende l'analisi riproducibile, revisionabile, condivisibile
- ...che i programmi sono scritti per le persone, non per i computer
  - Nomi di variabili significativi
  - Modularità per la leggibilità e il riutilizzo
  - Nessuna duplicazione
  - Scopo del documento e uso
- ...che non c'è magia: i programmi che usano non sono in linea di principio
  diversi da quelli che costruiscono
- ...come assegnare i valori alle variabili
- ...quali interi, floats, stringhe, array NumPy e frame dati Pandas sono
- ...come tracciare l'esecuzione di un ciclo `for`
- ...come tracciare l'esecuzione delle istruzioni `if`/`else`
- ...come creare ed elencare gli indici
- ...come creare e indicizzare array NumPy
- ...come creare e indicizzare i frame dei dati di Pandas
- ...come creare grafici serie temporali
- ...la differenza tra la definizione e la chiamata di una funzione
- ...dove trovare la documentazione sulle librerie standard
- ...come scoprire cosa offre Python scientifico

## Fase 3: Piano Di Apprendimento

### Valutazione Sommaria

- Midpoint: crea un grafico in serie temporali per ogni file in una directory.
- Finale: estrarre i dati da Pandas dataframe
  e creare il grafico comparativo multi-linea serie temporale.

### [Eseguire e uscire interattivamente](../episodes/01-run-quit.md) (9:00)

- Insegnamento: 15 min (perché problemi di configurazione)
  - Avviare il notebook di Giove, creare nuovi notebook ed uscire dal notebook.
  - Crea celle Markdown in un taccuino.
  - Crea ed esegui celle Python in un notebook.
- Sfide: 0 min (contabilizzato nel tempo di insegnamento - nessun esercizio separato)
  - Creare liste in Markdown
  - Cosa viene visualizzato quando diverse espressioni sono messe in una singola cella?
  - Cambia una cella esistente da codice a Markdown
  - Rendering equazioni stile LaTeX

### [Variabili e Assegnazione](../episodes/02-variables.md) (9:15)

- Insegnamento: 10 min
  - Scrivi programmi che assegnano valori scalari alle variabili ed eseguono calcoli con questi valori.
  - Tracciare correttamente i cambiamenti di valore nei programmi che utilizzano l'assegnazione scalare.
- Sfide: 10 min
  - Traccia l'esecuzione dello scambio di codice di due valori usando una variabile intermedia.
  - Prevedere i valori finali delle variabili dopo più assegnazioni.
  - Cosa succede se provi a indicizzare un numero?
  - Quale è un nome di variabile migliore, `m`, `min`, o `minuti`?
  - Cosa producono le seguenti espressioni di fessura?

### [Tipi di dati e Conversione di tipo](../episodes/03-types-conversion.md) (09:35)

- Insegnamento: 10 min
  - Spiega le differenze chiave tra numeri interi e numeri in virgola mobile.
  - Spiega le differenze tra numeri e stringhe di caratteri.
  - Usa le funzioni integrate per convertire tra numeri interi, numeri in virgola mobile e stringhe.
- Sfide: 10 min
  - Che tipo di valore è 3.4?
  - Che tipo di valore è 3,25 + 4?
  - Quale tipo di valore si userebbe per rappresentare:
    - Numero di giorni dall'inizio dell'anno.
    - Tempo trascorso dall'inizio dell'anno.
    - Ecc.
  - Come puoi usare `//` (divisione intera) e `%` (modulo)?
  - Cosa fa `int("3.4")`?
  - Dati questi valori di float, int, e stringa, quali espressioni stamperanno un risultato particolare?
  - Che cosa ti aspetti `1+2j + 3` per produrre?

### [Funzioni integrate e Aiuto](../episodes/04-built-in.md) (09:55)

- Insegnamento: 15 min
  - Spiegare lo scopo delle funzioni.
  - Chiamare correttamente le funzioni Python integrate.
  - Nidi correttamente le chiamate alle funzioni integrate.
  - Utilizzare l'aiuto per visualizzare la documentazione per le funzioni integrate.
  - Descrivere correttamente le situazioni in cui si verificano SyntaxError e NameError.
- Sfide: 10 min
  - Spiegare l'ordine delle operazioni nella seguente espressione complessa.
  - Cosa produrrà ogni combinazione annidata di chiamate `min` e `max`?
  - Perché non `max` e `min` restituiscono `None` quando non viene dato alcun argomento?
  - Dato quello che abbiamo visto finora,
    quale espressione indice otterrà l'ultimo carattere in una stringa?

### [Coffee](../episodes/05-coffee.md): 15 min (10:20)

### [Libraries](../episodes/06-libraries.md) (10:35)

- Insegnamento: 10 min
  - Spiega quali librerie di software sono e perché i programmatori le creano e le usano.
  - Scrivi programmi che importano e usano librerie dalla libreria standard di Python.
  - Trovare e leggere la documentazione per le librerie standard interattivamente (nell'interprete) e online.
- Sfide: 10 min
  - Quale funzione della libreria matematica standard si potrebbe utilizzare per calcolare una radice quadro?
  - Quale libreria useresti per selezionare un valore casuale dai dati?
  - Se `help(math)` produce un errore, cosa hai dimenticato di fare?
  - Inserisci gli spazi vuoti nel codice qui sotto in modo che la dichiarazione di importazione e il programma siano eseguiti.

### [Reading Tabular Data](../episodes/07-reading-tabular.md) (10:55)

- Insegnamento: 10 min
  - Importa la libreria Pandas.
  - Usa Panda per caricare un semplice set di dati CSV.
  - Ottieni alcune informazioni di base su un DataFrame.
- Sfide: 10 min
  - Leggi i dati per le Americhe e visualizza le sue statistiche sommarie.
  - Cosa fanno `.head` e `.tail`?
  - Quali stringhe dovresti passare a `read_csv` per leggere i file da altre directory?
  - Come puoi _scrivere_ i dati CSV?

### [DataFrames](../episodes/08-data-frames.md) (11:15)

- Insegnamento: 15 min
  - Seleziona valori individuali da un dataframe di Panda.
  - Seleziona intere righe o intere colonne da un dataframe.
  - Selezionare un sottoinsieme di entrambe le righe e colonne da un dataframe in una singola operazione.
  - Seleziona un sottoinsieme di un dataframe con un singolo criterio booleano.
- Sfide: 15 min
  - Scrivi un'espressione per trovare il PIL Per Capita della Serbia nel 2007.
  - Quale regola governa ciò che è (o non è) incluso in fette numeriche e denominate in Pandas?
  - Che cosa fa ogni riga nel seguente breve programma?
  - Cosa fanno `idxmin` e `idxmax`?
  - Scrivere espressioni per ottenere il PIL pro capite per tutti i paesi nel 1982,
    per tutti i paesi \*dopo \* 1985,
    ecc.
  - Dato il modo in cui le sue frontiere sono cambiate dal 1900,
    cosa fareste se chiedete di creare una tabella del PIL pro capite per la Polonia
    per il XX secolo?

### [Plotting](../episodes/09-plotting.md) (11:45)

- Insegnamento: 15 min
  - Crea un grafico di serie temporale che mostri un singolo set di dati.
  - Crea un grafico a dispersione che mostra la relazione tra due set di dati.
- Esercizio: 15 min
  - Compilare gli spazi vuoti per tracciare il PIL minimo pro capite nel tempo per i paesi europei.
  - Modificare l'esempio per creare una dispersione del PIL pro capite nei paesi asiatici.
  - Spiega cosa fa ogni argomento a `plot` nell'esempio seguente.

### [Lunch](../episodes/10-lunch.md) (12:15): 45 min

### [Lists](../episodes/11-lists.md) (13:00)

- Insegnamento: 10 min
  - Spiega perché i programmi hanno bisogno di collezioni di valori.
  - Scrivere programmi che creano liste piatte, indicizzarli, tagliarli e modificarli attraverso l'assegnazione e le chiamate di metodo.
- Sfide: 10 min
  - Riempire gli spazi vuoti in modo che il programma produca l'output mostrato.
  - Quanto sono grandi le seguenti fette?
  - Cosa stampano le espressioni dell'indice negativo?
  - Che cosa fa un "passo" in una fetta?
  - Come le fette trattano i confini fuori gamma?
  - Quali sono le differenze tra l'ordinamento di questi due modi?
  - Qual è la differenza tra `new = old` e `new = old[:]`?

### [Loops](../episodes/12-for-loops.md) (13:20)

- Insegnamento: 10 min
  - Spiegare che cosa per i cicli sono normalmente utilizzati per.
  - Traccia l' esecuzione di un semplice ciclo (non nidificato) e indica correttamente i valori delle variabili in ogni iterazione.
  - Scrivi per cicli che usano il modello Accumulatore per aggregare i valori.
- Sfide: 15 min
  - Un errore di rientro è un errore di sintassi o un errore di runtime?
  - Traccia quali linee di questo programma vengono eseguite in quale ordine.
  - Riempi gli spazi vuoti in questo programma in modo che inverti una stringa.
  - Compila gli spazi vuoti di questa serie di esempi per ottenere valori di accumulazione della pratica.
  - Riordinare e riordinare queste righe per calcolare la somma cumulativa dei valori dell'elenco.

### [Looping Over Data Sets](13-looping-data-sets) (13:45)

- Insegnamento: 5 min
  - Essere in grado di leggere e scrivere espressioni globbing che corrispondono a insiemi di file.
  - Usa il globo per creare elenchi di file.
  - Scrivi per i loop per eseguire operazioni sui file dati i loro nomi in un elenco.
- Sfide: 10 min
  - Quali nomi di file _non_ sono abbinati a questa espressione globo?
  - Modificare questo programma in modo che stampi il numero di record nel file più breve.
  - Scrivi un programma che legge e traccia tutti i set di dati regionali.

### [Funzioni Di Scrittura](14-Scrittura-Funzioni) (14:00)

- Insegnamento: 10 min
  - Spiegare e identificare la differenza tra la definizione delle funzioni e la chiamata delle funzioni.
  - Scrivi una funzione che richiede un piccolo numero fisso di argomenti e produce un singolo risultato.
- Sfide: 15 min
  - Questo codice definisce e chiama una funzione: cosa stampa quando viene eseguito?
  - Spiega perché questo breve programma stampa le cose nell'ordine che fa.
  - Compila gli spazi vuoti per creare una funzione che trova il valore minimo in un file di dati.
  - Compila gli spazi vuoti per creare una funzione che trova il primo valore negativo in una lista.
    Cosa fa la tua funzione se la lista è vuota?
  - Perché a volte è utile passare argomenti nominando i parametri corrispondenti?
  - Compila gli spazi vuoti e trasforma questo breve pezzo di codice in una funzione.

### [Ambito Variabile](15-Ampiezza) (14:25)

- Insegnamento: 10 min
  - Identificare le variabili locali e globali.
  - Identificare i parametri come variabili locali.
  - Leggi una traceback e determina il file, la funzione e il numero di riga su cui si è verificato l'errore.
- Sfide: 10 min
  - Tracciare i cambiamenti ai valori in questo programma,
    facendo attenzione a distinguere i valori locali dai valori globali.

### [Coffee](16-caffè) (14:45): 15 min

### [Conditionals](17-condizionali) (15:00)

- Insegnamento: 10 min
  - Correttamente scrivi programmi che usano se e altrimenti affermazioni e semplici espressioni booleane (senza operatori logici).
  - Traccia l'esecuzione di condizioni non nidificate e condizionali all'interno cappi.
- Sfide: 15 min
  - Traccia l'esecuzione di questa istruzione condizionale.
  - Riempi gli spazi vuoti in modo che questa funzione sostituisca i valori negativi con gli zeri.
  - Modificare questo programma in modo che elabori solo file con meno di 50 record.
  - Modificare questo programma in modo che trovi sempre i valori più grandi e più piccoli in una lista
    non importa quali siano i valori della lista.

### [Stile Di Programmazione](../episodes/18-style.md) (15:25)

- Insegnamento: 15 min
  - Come posso rendere i miei programmi più leggibili?
  - Come la maggior parte dei programmatori formattano il loro codice?
  - Come possono i programmi controllare la propria operazione?
- Sfide: 15 min
  - Quali linee in questo codice saranno disponibili come aiuto online?
  - Trasforma i commenti in questo programma in docstrings.
  - Rewrite this short program to be more readable.

### [Wrap-Up](../episodes/19-wrap.md) (15:55)

- Insegnamento: 20 min
  - Nome e localizza siti scientifici della comunità Python per software, workshop e aiuto.
- Sfide: 0 min
  - Nessuno.

### [Feedback](../episodes/20-feedback.md) (16:15)

- Insegnamento: 0 min
- Sfide: 15 min
  - Raccogli feedback

### Termina (16:30)
