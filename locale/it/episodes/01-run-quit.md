---
title: Esecuzione e uscita
teaching: 15
exercises: 0
---

::::::::::::::::::::::::::::::::::::::::::::::: obiettivi

- Avvia il server di JupyterLab.
- Create a new Python script.
- Crea un taccuino di Giove.
- Spegni il server di JupyterLab.
- Comprendere la differenza tra uno script Python e un notebook di Giove.
- Crea celle Markdown in un taccuino.
- Crea ed esegui celle Python in un notebook.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::: domande

- Come posso eseguire programmi Python?

::::::::::::::::::::::::::::::::::::::::::::::::::

Per eseguire Python, useremo \[Jupyter Notebooks]\[jupyter] via [JupyterLab][jupyterlab] per il resto di questo workshop. I notebook Jupyter sono comuni nella scienza dei dati e nella visualizzazione e servono come una comoda esperienza di denominatore comune per eseguire il codice Python interattivamente, dove possiamo facilmente visualizzare e condividere i risultati del nostro codice Python.

Ci sono altri modi per modificare, gestire e eseguire il codice. Gli sviluppatori di software spesso usano un ambiente di sviluppo integrato (IDE) come [PyCharm](https\://www\.jetbrains. om/pycharm/) o [Visual Studio Code](https://code.visualstudio.com/), o editor di testo come Vim o Emacs, per creare e modificare i loro programmi Python. Dopo aver modificato e salvato i programmi Python è possibile eseguire quei programmi all'interno dell'IDE stesso o direttamente sulla riga di comando. Al contrario, Jupyter notebook ci permette di eseguire e visualizzare i risultati del nostro codice Python immediatamente all'interno del notebook.

JupyterLab ha diverse altre caratteristiche utili:

- Puoi facilmente digitare, modificare e copiare e incollare blocchi di codice.
- La scheda completa ti permette di accedere facilmente ai nomi delle cose che stai usando
  e di saperne di più.
- Ti permette di annotare il tuo codice con link, testo di diverse dimensioni, proiettili, ecc.
  per renderlo più accessibile a te e ai tuoi collaboratori.
- Ti permette di visualizzare le figure accanto al codice che le produce
  per raccontare una storia completa dell'analisi.

Ogni notebook contiene una o più celle che contengono codice, testo o immagini.

## Per iniziare con JupyterLab

JupyterLab è un server di applicazioni con un'interfaccia utente web da [Project Jupyter][jupyter] che
consente di lavorare con documenti e attività come i notebook di Jupyter, editor di testo, terminali,
e persino componenti personalizzati in modo flessibile, integrato ed estensibile. JupyterLab richiede un browser
ragionevolmente aggiornato (idealmente una versione corrente di Chrome, Safari o Firefox); Internet
Le versioni 9 e seguenti di Explorer sono _non_ supportate.

JupyterLab è incluso nella distribuzione di Anaconda Python. Se non hai già installato
la distribuzione Anaconda Python, vedi [le istruzioni di installazione](../learners/setup.md)
per le istruzioni di installazione.

In questa lezione eseguiremo JupyterLab localmente sulle nostre macchine in modo che non richieda una connessione internet oltre ad
la connessione iniziale per scaricare e installare Anaconda e JupyterLab

- Avvia il server JupyterLab sul tuo computer
- Usa un browser web per aprire uno speciale URL localhost che si connette al tuo server JupyterLab
- Il server JupyterLab fa il lavoro e il browser web rende il risultato
- Digitare il codice nel browser e vedere i risultati dopo che il server JupyterLab ha finito di eseguire il codice

:::::::::::::::::::::::::::::::::::::::::  callout

## JupyterLab? Che dire di Jupyter notebooks?

JupyterLab è la [prossima tappa dell'evoluzione del Notebook Jupyter](https://jupyterlab.readthedocs.io/en/stable/getting_started/overview.html#overview).
Se avete esperienza di lavoro precedente con i taccuini di Giove, allora avrete una buona idea di cosa aspettarsi da JupyterLab.

Gli utenti esperti dei notebook di Jupyter interessati a una discussione più dettagliata delle somiglianze e differenze
tra le interfacce utente del notebook di JupyterLab e di Jupyter possono trovare maggiori informazioni nella
[documentazione dell'interfaccia utente di JupyterLab][jupyterlab-ui].

::::::::::::::::::::::::::::::::::::::::::::::::::

## Avvio JupyterLab

È possibile avviare il server JupyterLab attraverso la riga di comando o attraverso un'applicazione chiamata
`Anaconda Navigator`. Anaconda Navigator è incluso come parte della distribuzione Anaconda Python.

### macOS - Linea di comando

Per avviare il server JupyterLab è necessario accedere alla riga di comando attraverso il terminale.
Ci sono due modi per aprire il terminale su Mac.

1. Nella cartella Applicazioni, apri Utilità e fai doppio clic sul terminale
2. Premi <kbd>Comando</kbd> + <kbd>barra spaziatrice</kbd> per avviare Spotlight. Digita `Terminal` e poi
   fai doppio clic sul risultato della ricerca o premi <kbd>Inserisci</kbd>

Dopo aver avviato il Terminal, digitare il comando per avviare il server JupyterLab.

```bash
$ jupyter lab
```

### Utenti Windows - Linea Di Comando

Per avviare il server JupyterLab è necessario accedere al Prompt di Anaconda.

Premere <kbd>Windows Logo Key</kbd> e cercare `Anaconda Prompt`, fare clic sul risultato o premere Invio.

Dopo aver lanciato il Prompt di Anaconda, digitare il comando:

```bash
$ jupyter lab
```

### Anaconda Navigator

Per avviare un server JupyterLab da Anaconda Navigator devi prima [avviare Anaconda Navigator (clicca per istruzioni dettagliate su macOS, Windows e Linux)](https://docs.anaconda.com/free/navigator/getting-started/#navigator-starting-navigator). Puoi cercare Anaconda Navigator tramite Spotlight su macOS (<kbd>Command</kbd> + <kbd>spacebar</kbd>), la funzione di ricerca di Windows (<kbd>Windows Logo Key</kbd>) o l'apertura di una shell di terminale ed esecuzione dell'eseguibile `anaconda-navigator` dalla riga di comando.

Dopo aver lanciato Anaconda Navigator, clicca sul pulsante `Launch` sotto JupyterLab. Potresti aver bisogno di
per scorrere verso il basso per trovarlo.

Ecco una schermata di una pagina Anaconda Navigator simile a quella che dovrebbe aprire su macOS
o Windows.

<p align='center'>
  <img alt="Anaconda Navigator landing page" src="fig/0_anaconda_navigator_landing_page.png" width="750"/>
</p>

Ed ecco uno screenshot di una landing page di JupyterLab che dovrebbe essere simile a quella che si apre nel tuo browser web predefinito
dopo aver avviato il server JupyterLab su macOS o Windows.

<p align='center'>
  <img alt="JupyterLab landing page" src="fig/0_jupyterlab_landing_page.png" width="750"/>
</p>

## Interfaccia JupyterLab

JupyterLab ha molte caratteristiche presenti negli ambienti di sviluppo integrati tradizionali (IDES), ma
è focalizzato sulla fornitura di moduli flessibili per il calcolo interattivo e esplorativo.

L'[Interfaccia JupyterLab][jupyterlab-ui]
è costituita dalla barra dei menu, una barra laterale sinistra pieghevole, e l'area di lavoro principale che contiene le schede
di documenti e attività.

### Barra Dei Menu

La barra dei menu nella parte superiore di JupyterLab ha i menu di primo livello che espongono varie azioni
disponibili in JupyterLab insieme alle loro scorciatoie da tastiera (se applicabile). I seguenti menu
sono inclusi per impostazione predefinita.

- **File:** Azioni relative a file e directory come _New_, _Open_, _Close_, _Salva_, ecc. Il menu _File_ include anche l'azione _Shut Down_ usata per arrestare il server di JupyterLab.
- **Modifica:** Azioni relative alla modifica di documenti e altre attività come _Annulla_, _Taglia_, _Copia_, _Incolla_, ecc.
- **Vista:** Azioni che alterano l'aspetto di JupyterLab.
- **Esegui:** Azioni per l'esecuzione di codice in attività diverse come notebook e console di codice (discussa di seguito).
- **Kernel:** Azioni per la gestione dei kernel. I kernel in Jupyter saranno spiegati più dettagliatamente di seguito.
- **Schede:** Un elenco dei documenti aperti e delle attività nell'area di lavoro principale.
- **Impostazioni:** Le impostazioni comuni di JupyterLab possono essere configurate utilizzando questo menu. C'è anche un'opzione _Advanced Settings Editor_ nel menu a discesa che fornisce un controllo più preciso delle impostazioni di JupyterLab e delle opzioni di configurazione.
- **Aiuto:** Un elenco di link di aiuto JupyterLab e kernel.

:::::::::::::::::::::::::::::::::::::::::  callout

## Cernoli

Il JupyterLab [docs](https://jupyterlab.readthedocs.io/en/stable/user/documents_kernels.html)
definisce i kernel come "processi separati avviati dal server che esegue il tuo codice in diversi linguaggi di programmazione e ambienti."
Quando apriamo un Notebook Jupyter, che avvia un kernel - un processo - che sta per eseguire il codice.
In questa lezione, useremo il kernel ipython Jupyter che ci permette di eseguire il codice Python 3 interattivamente.

Usare altri [kernel Jupyter per altri linguaggi di programmazione](https\://github. om/jupyter/jupyter/wiki/Jupyter-kernels) ci lascerebbe
scrivere ed eseguire il codice in altri linguaggi di programmazione nella stessa interfaccia JupyterLab, come R, Java, Julia, Ruby, JavaScript, Fortran,
ecc.

::::::::::::::::::::::::::::::::::::::::::::::::::

Una schermata della barra dei menu predefinita è fornita di seguito.

<p align='center'>   <img alt="JupyterLab Menu Bar" src="fig/0_jupyterlab_menu_bar.png" width="750"/>
</p>

### Left Sidebar

La barra laterale sinistra contiene un certo numero di schede comunemente usate, ad esempio un file browser (che mostra i contenuti
della directory in cui è stato lanciato il server JupyterLab), un elenco di kernel
e terminali, la tavolozza dei comandi e un elenco di schede aperte nell'area di lavoro principale. Una schermata di
la barra laterale sinistra predefinita è fornita di seguito.

<p align='center'>   <img alt="JupyterLab Left Side Bar" src="fig/0_jupyterlab_left_side_bar.png" width="250"/>
</p>

La barra laterale sinistra può essere ridotta o espansa selezionando "Mostra barra laterale sinistra" nel menu Visualizza o
facendo clic sulla scheda della barra laterale attiva.

### Area Di Lavoro Principale

L'area di lavoro principale in JupyterLab consente di organizzare documenti (notebook, file di testo, ecc.)
e altre attività (terminali, console di codice, ecc.) in pannelli di schede che possono essere ridimensionati o
suddivisi. Di seguito viene fornita una schermata dell'area di lavoro principale predefinita.

Se non vedi la scheda Launcher, fai clic sul segno più blu sotto i menu "File" e "Modifica" e apparirà.

<p align='center'>   <img alt="JupyterLab Main Work Area" src="fig/0_jupyterlab_main_work_area.png" width="750"/>
</p>

Trascina una scheda al centro di un pannello delle schede per spostare la scheda al pannello. Suddividi un pannello di schede per
trascinando una scheda a sinistra, a destra, in alto o in basso del pannello. L'area di lavoro ha una singola attività corrente
. La scheda per l'attività corrente è contrassegnata con un bordo superiore colorato (blu per impostazione predefinita).

## Creazione di uno script Python

- Per iniziare a scrivere un nuovo programma Python, fare clic sull'icona File di testo sotto l'intestazione _Altro_ nella scheda Launcher dell'area di lavoro principale.
  - È inoltre possibile creare un nuovo file di testo semplice selezionando il _Nuovo -> File di testo_ dal menu _File_ nella barra dei menu.
- Per convertire questo file di testo semplice in un software Python, selezionare l'azione _Salva file come_ dal menu _File_ nella barra dei menu e dare al nuovo file di testo un nome che termina con il `. y` estensione.
  - L'estensione `.py` permette a tutti (compreso il sistema operativo) di sapere che questo file di testo è un programma Python.
  - Si tratta di una convenzione, non di un requisito.

## Creare un taccuino di Jupyter

Per aprire un nuovo taccuino fare clic sull'icona Python 3 sotto l'intestazione _Notebook_ nella scheda Launcher in
l'area di lavoro principale. Puoi anche creare un nuovo taccuino selezionando _Nuovo -> Notebook_ dal menu _File_ nella barra dei menu.

Note aggiuntive sui taccuini di Giove.

- I file notebook hanno l'estensione `.ipynb` per distinguerli dai programmi Python di testo semplice.
- I notebook possono essere esportati come script Python che possono essere eseguiti dalla riga di comando.

Di seguito è riportata una schermata di un notebook di Jupyter in esecuzione all'interno di JupyterLab. Se siete interessati a
più dettagli, quindi vedere la [documentazione ufficiale taccuino][jupyterlab-notebook-docs].

<p align='center'>   <img alt="Example Jupyter Notebook" src="fig/0_jupyterlab_notebook_screenshot.png" width="750"/>
</p>

:::::::::::::::::::::::::::::::::::::::::  callout

## Come È Conservato

- Il file del notebook è memorizzato in un formato chiamato JSON.
- Proprio come una pagina web, ciò che è salvato sembra diverso da quello che vedi nel tuo browser.
- Ma questo formato permette a Jupyter di mescolare codice sorgente, testo e immagini, tutto in un unico file.

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Organizzare documenti in gruppi di schede

Nell'area di lavoro principale di JupyterLab è possibile organizzare i documenti in pannelli di schede. Ecco un esempio
della [documentazione ufficiale][jupyterlab].

<p align='center'>   <img alt="Multi-panel JupyterLab" src="fig/0_multipanel_jupyterlab_screenshot.png" width="750"/>
</p>

Innanzitutto, crea un file di testo, una console Python e una finestra di terminale e li organizza in tre pannelli
nell'area di lavoro principale. Successivamente, creare un notebook, finestra del terminale e file di testo e
organizzarli in tre pannelli nell'area di lavoro principale. Infine, crea la tua combinazione di pannelli
e schede. Quale combinazione di pannelli e schede pensi sarà più utile per il tuo flusso di lavoro
?

::::::::::::::: soluzione

## Soluzione

Dopo aver creato le schede necessarie, puoi trascinare una delle schede al centro di un pannello in
spostare la scheda nel pannello; accanto puoi suddividere un pannello di schede trascinando una scheda a sinistra,
a destra, in alto o in basso del pannello.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## Codice vs. Testo

Jupyter mescola codice e testo in diversi tipi di blocchi, chiamati celle. Spesso usiamo il termine
"codice" per significare "il codice sorgente del software scritto in una lingua come Python".
Una "cella di codice" in un notebook è una cella che contiene software;
una "cella di testo" è quella che contiene la prosa ordinaria scritta per gli esseri umani.

::::::::::::::::::::::::::::::::::::::::::::::::::

## Il notebook ha modalità di comando e modifica.

- Se premi alternativamente <kbd>Esc</kbd> e <kbd>Restituzione</kbd> , il bordo esterno della cella del codice cambierà da grigio a blu.
- Queste sono le modalità **Comando** (grigio) e **Modifica** (blu) del tuo taccuino.
- La modalità di comando consente di modificare le funzionalità a livello notebook, e la modalità di modifica cambia il contenuto delle celle.
- Quando in modalità comando (esc/grigio),
  - Il tasto <kbd>b</kbd> farà una nuova cella sotto la cella attualmente selezionata.
  - La chiave <kbd>a</kbd> ne farà una sopra.
  - La chiave <kbd>x</kbd> eliminerà la cella corrente.
  - La chiave <kbd>z</kbd> annullerà la tua ultima operazione di cella (che potrebbe essere una cancellazione, creazione, ecc).
- Tutte le azioni possono essere fatte usando i menu, ma ci sono un sacco di scorciatoie da tastiera per velocizzare le cose.

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Comando Vs. Modifica

Nella pagina del notebook di Jupyter sei attualmente in modalità Comando o Modifica?\
Passa tra le modalità.
Usa le scorciatoie per generare una nuova cella.
Utilizzare le scorciatoie per eliminare una cella.
Utilizzare le scorciatoie per annullare l'ultima operazione di cella eseguita.

::::::::::::::: soluzione

## Soluzione

La modalità comando ha un bordo grigio e la modalità Modifica ha un bordo blu.
Usa <kbd>Esc</kbd> e <kbd>Return</kbd> per passare da una modalità all'altra.
Devi essere in modalità Comando (Invia <kbd>Esc</kbd> se la tua cella è blu).  Digita <kbd>b</kbd> or <kbd>a</kbd>.
Devi essere in modalità Comando (Invia <kbd>Esc</kbd> se la tua cella è blu).  Type <kbd>x</kbd>.
Devi essere in modalità Comando (Invia <kbd>Esc</kbd> se la tua cella è blu).  Type <kbd>z</kbd>.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

### Utilizzare la tastiera e il mouse per selezionare e modificare le celle.

- Premendo il tasto <kbd>Invio</kbd> si trasforma il bordo blu e si attiva la modalità di modifica, che consente a
  di digitare all'interno della cella.
- Perché vogliamo essere in grado di scrivere molte righe di codice in una singola cella,
  premendo il tasto <kbd>Restituisce</kbd> quando in modalità Modifica (blu) sposta il cursore alla riga
  successiva nella cella come in un editor di testo.
- Abbiamo bisogno di un altro modo per dire al notebook che vogliamo eseguire ciò che è nella cella.
- Premendo <kbd>Maiusc</kbd>+<kbd>Restituzione</kbd> insieme eseguirà il contenuto della cella.
- Notate che i tasti <kbd>Return</kbd> e <kbd>Shift</kbd> sulla destra della tastiera sono
  proprio accanto all'altro.

### Il notebook trasformerà Markdown in una bella documentazione stampata.

- I taccuini possono anche rendere [Markdown][markdown].
  - Un semplice formato di testo semplice per scrivere elenchi, link,
    e altre cose che potrebbero entrare in una pagina web.
  - Allo stesso modo, un sottoinsieme di HTML che assomiglia a quello che invii in un vecchio stile di email.
- Trasforma la cella corrente in una cella Markdown entrando nella modalità Comando (<kbd>Esc</kbd>/gray)
  e premi il tasto <kbd>M</kbd>.
- `In [ ]:` scomparirà per mostrare che non è più una cella di codice e sarai in grado di scrivere in
  Markdown.
- Trasforma la cella corrente in una cella Codice entrando nella modalità Comando (<kbd>Esc</kbd>/gray) e
  premi il tasto <kbd>y</kbd>.

### Markdown fa la maggior parte di ciò che fa HTML.

<div class="row">

  <div class="col-md-6" markdown="1">

```
* Usa gli asterischi
* per creare
* liste proiettili.
```

  

  <div class="col-md-6" markdown="1">

- Usa asterischi
- per creare
- elenchi di proiettili.

  </div>

</div>

<div class="row">

  <div class="col-md-6" markdown="1">

```
1. Usa i numeri
1. per creare
1. elenchi numerati.
```

  

  <div class="col-md-6" markdown="1">

1. Usa numeri
2. per creare
3. liste numerate.

  

</div>

<div class="row">

  <div class="col-md-6" markdown="1">

```
* È possibile utilizzare i indenti
	<unk> * Per creare sublisti 
	<unk> * dello stesso tipo
* O sublisti
	<unk> 1. Di diversi tipi di
	<unk> 1.
```

  

  <div class="col-md-6" markdown="1">

- È possibile utilizzare i rientri
  - Per creare sublist
  - dello stesso tipo
- O sublisti

  1. Di diverse
  2. tipi

  </div>

</div>

<div class="row">

  <div class="col-md-6" markdown="1">

```
# Intestazione Livello -1
```

  

  <div class="col-md-6" markdown="1">

## A Livello-1 Titolo

  

</div>

<div class="row">

  <div class="col-md-6" markdown="1">

```
## Intestazione A Livello 2 (ecc.)
```

  

  <div class="col-md-6" markdown="1">

## Titolo A Livello 2 (ecc.)

  

</div>

<div class="row">

  <div class="col-md-6" markdown="1">

```
Line breaks
don't matter.

But blank lines
create new paragraphs.
```

  

  <div class="col-md-6" markdown="1">

Le interruzioni di linea
non importano.

Ma le righe vuote
creano nuovi paragrafi.

  

</div>

<div class="row">

  <div class="col-md-6" markdown="1">

```
[Crea collegamenti](http://software-carpentry.org) con `[...](...)`.
Oppure usa [named links][data_carpentry].

[data_carpentry]: http://datacarpentry.org
```

  

  <div class="col-md-6" markdown="1">

[Crea collegamenti](https://software-carpentry.org) con `[...](...)`.
Oppure usa [link nominati][data_carpentry].

  

</div>

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Creare liste in Markdown

Crea un elenco annidato in una cella Markdown in un taccuino che assomiglia a questo:

1. Ricevi finanziamenti.
2. Fate lavoro.

- Esperimento di design.
- Raccogliere dati.
- Analizza.

3. Scrivetela.
4. Pubblica.

::::::::::::::: soluzione

## Soluzione

Questa sfida integra sia la lista numerata che la lista proiettile.
Si noti che l'elenco dei proiettili è indentato 2 spazi in modo che sia in linea con gli elementi dell'elenco numerato.

```
1. Ottieni finanziamenti.
2. Fai lavoro.
    * Esperimento design.
    * Raccogliere dati.
    * Analizza.
3. Scrivere
4. Pubblica.
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Più Matematica

Cosa viene visualizzato quando viene eseguita una cella Python in un taccuino
che contiene diversi calcoli?
Ad esempio, cosa succede quando questa cella viene eseguita?

```python
7 * 3
2 + 1
```

::::::::::::::: soluzione

## Soluzione

Python restituisce l'output dell'ultimo calcolo.

```python
3
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Cambia una cella esistente da codice a Markdown

Cosa succede se scrivi un po' di Python in una cella di codice
e poi lo passi a una cella Markdown?
Ad esempio,
mette quanto segue in una cella di codice:

```python
x = 6 * 7 + 12
print(x)
```

E poi eseguilo con <kbd>Shift</kbd>+<kbd>Return</kbd> per essere sicuro che funzioni come una cella di codice.
Ora torna alla cella e usa <kbd>Esc</kbd> quindi <kbd>m</kbd> per cambiare la cella su Markdown
e "eseguirla" con <kbd>Maiusc</kbd>+<kbd>Restituzione</kbd>.
Cosa è successo e come potrebbe essere utile?

::::::::::::::: soluzione

## Soluzione

Il codice Python viene trattato come testo Markdown.
Le righe appaiono come se facessero parte di un paragrafo contiguo.
Questo potrebbe essere utile per attivare temporaneamente e disattivare le celle nei notebook che vengono utilizzati per molteplici scopi.

```python
x = 6 * 7 + 12 print(x)
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Equazioni

Markdown standard (come stiamo usando per queste note) non visualizzerà le equazioni,
ma il notebook lo farà.
Crea una nuova cella Markdown
e inserisci quanto segue:

```
$\sum_{i=1}^{N} 2^{-i} \approx 1$
```

(Probabilmente è più facile copiare e incollare.)
Che cosa mostra?
Che cosa pensi che il underscore, `_`, circumflex, `^`, e il segno del dollaro, `$`, fa?

::::::::::::::: soluzione

## Soluzione

Il notebook mostra l'equazione come sarebbe resa dalla sintassi di equazione LaTeX.
Il segno del dollaro, `$`, è usato per dire Markdown che il testo in mezzo è una equazione LaTeX.
Se non hai familiarità con LaTeX, underscore, `_`, è usato per gli abbonamenti e circumflex, `^`, è usato per gli superscript.
Un paio di parentesi graffe, `{` e `}`, è usato per raggruppare il testo insieme in modo che l'espressione `i=1` diventi il pedice e `N` diventi il superscript.
Allo stesso modo, `-i` è nelle parentesi graffe per rendere l'intera dichiarazione l'apice per `2`.
`\sum` e `\approx` sono comandi LaTeX per i simboli "sum over" e "approximate".

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

## Chiusura JupyterLab

- Dalla barra dei menu selezionare il menu "File" e quindi scegliere "Shut Down" nella parte inferiore del menu a discesa. Ti verrà chiesto di confermare che desideri spegnere il server JupyterLab (non dimenticare di salvare il tuo lavoro!). Fare clic su "Shut Down" per spegnere il server di JupyterLab.
- Per riavviare il server JupyterLab è necessario eseguire nuovamente il seguente comando da una shell.

```
$ jupyter lab
```

::::::::::::::::::::::::::::::::::::::::::::: challenge

## Chiusura JupyterLab

Pratica la chiusura e il riavvio del server di JupyterLab.

::::::::::::::::::::::::::::::::::::::::::::::::::

[jupyterlab]: https://jupyterlab.readthedocs.io/en/stable/

[jupyterlab-ui]: https://jupyterlab.readthedocs.io/en/stable/user/interface.html

[jupyterlab-notebook-docs]: https://jupyterlab.readthedocs.io/en/stable/user/notebook.html

[markdown]: https://en.wikipedia.org/wiki/Markdown

[data_carpentry]: https://datacarpentry.org

:::::::::::::::::::::::::::::::::::::::: keypoints

- Gli script Python sono file di testo semplice.
- Usa il notebook Jupyter per modificare ed eseguire Python.
- Il notebook ha modalità di comando e modifica.
- Utilizzare la tastiera e il mouse per selezionare e modificare le celle.
- Il notebook trasformerà Markdown in una bella documentazione stampata.
- Markdown fa la maggior parte di ciò che fa HTML.

::::::::::::::::::::::::::::::::::::::::::::::::::
