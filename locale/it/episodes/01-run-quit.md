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

### Main Work Area

The main work area in JupyterLab enables you to arrange documents (notebooks, text files, etc.)
and other activities (terminals, code consoles, etc.) into panels of tabs that can be resized or
subdivided. A screenshot of the default Main Work Area is provided below.

If you do not see the Launcher tab, click the blue plus sign under the "File" and "Edit" menus and it will appear.

<p align='center'>   <img alt="JupyterLab Main Work Area" src="fig/0_jupyterlab_main_work_area.png" width="750"/>
</p>

Drag a tab to the center of a tab panel to move the tab to the panel. Subdivide a tab panel by
dragging a tab to the left, right, top, or bottom of the panel. The work area has a single current
activity. The tab for the current activity is marked with a colored top border (blue by default).

## Creating a Python script

- To start writing a new Python program click the Text File icon under the _Other_ header in the Launcher tab of the Main Work Area.
  - You can also create a new plain text file by selecting the _New -> Text File_ from the _File_ menu in the Menu Bar.
- To convert this plain text file to a Python program, select the _Save File As_ action from the _File_ menu in the Menu Bar and give your new text file a name that ends with the `.py` extension.
  - The `.py` extension lets everyone (including the operating system) know that this text file is a Python program.
  - This is convention, not a requirement.

## Creating a Jupyter Notebook

To open a new notebook click the Python 3 icon under the _Notebook_ header in the Launcher tab in
the main work area. You can also create a new notebook by selecting _New -> Notebook_ from the _File_ menu in the Menu Bar.

Additional notes on Jupyter notebooks.

- Notebook files have the extension `.ipynb` to distinguish them from plain-text Python programs.
- Notebooks can be exported as Python scripts that can be run from the command line.

Below is a screenshot of a Jupyter notebook running inside JupyterLab. If you are interested in
more details, then see the [official notebook documentation][jupyterlab-notebook-docs].

<p align='center'>   <img alt="Example Jupyter Notebook" src="fig/0_jupyterlab_notebook_screenshot.png" width="750"/>
</p>

:::::::::::::::::::::::::::::::::::::::::  callout

## How It's Stored

- The notebook file is stored in a format called JSON.
- Just like a webpage, what's saved looks different from what you see in your browser.
- But this format allows Jupyter to mix source code, text, and images, all in one file.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Arranging Documents into Panels of Tabs

In the JupyterLab Main Work Area you can arrange documents into panels of tabs. Here is an
example from the [official documentation][jupyterlab].

<p align='center'>   <img alt="Multi-panel JupyterLab" src="fig/0_multipanel_jupyterlab_screenshot.png" width="750"/>
</p>

First, create a text file, Python console, and terminal window and arrange them into three
panels in the main work area. Next, create a notebook, terminal window, and text file and
arrange them into three panels in the main work area. Finally, create your own combination of
panels and tabs. What combination of panels and tabs do you think will be most useful for your
workflow?

:::::::::::::::  solution

## Solution

After creating the necessary tabs, you can drag one of the tabs to the center of a panel to
move the tab to the panel; next you can subdivide a tab panel by dragging a tab to the left,
right, top, or bottom of the panel.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## Code vs. Text

Jupyter mixes code and text in different types of blocks, called cells. We often use the term
"code" to mean "the source code of software written in a language such as Python".
A "code cell" in a Notebook is a cell that contains software;
a "text cell" is one that contains ordinary prose written for human beings.

::::::::::::::::::::::::::::::::::::::::::::::::::

## The Notebook has Command and Edit modes.

- If you press <kbd>Esc</kbd> and <kbd>Return</kbd> alternately, the outer border of your code cell will change from gray to blue.
- These are the **Command** (gray) and **Edit** (blue) modes of your notebook.
- Command mode allows you to edit notebook-level features, and Edit mode changes the content of cells.
- When in Command mode (esc/gray),
  - The <kbd>b</kbd> key will make a new cell below the currently selected cell.
  - The <kbd>a</kbd> key will make one above.
  - The <kbd>x</kbd> key will delete the current cell.
  - The <kbd>z</kbd> key will undo your last cell operation (which could be a deletion, creation, etc).
- All actions can be done using the menus, but there are lots of keyboard shortcuts to speed things up.

:::::::::::::::::::::::::::::::::::::::  challenge

## Command Vs. Edit

In the Jupyter notebook page are you currently in Command or Edit mode?\
Switch between the modes.
Use the shortcuts to generate a new cell.
Use the shortcuts to delete a cell.
Use the shortcuts to undo the last cell operation you performed.

:::::::::::::::  solution

## Solution

Command mode has a grey border and Edit mode has a blue border.
Use <kbd>Esc</kbd> and <kbd>Return</kbd> to switch between modes.
You need to be in Command mode (Press <kbd>Esc</kbd> if your cell is blue).  Type <kbd>b</kbd> or <kbd>a</kbd>.
You need to be in Command mode (Press <kbd>Esc</kbd> if your cell is blue).  Type <kbd>x</kbd>.
You need to be in Command mode (Press <kbd>Esc</kbd> if your cell is blue).  Type <kbd>z</kbd>.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

### Use the keyboard and mouse to select and edit cells.

- Pressing the <kbd>Return</kbd> key turns the border blue and engages Edit mode, which allows
  you to type within the cell.
- Because we want to be able to write many lines of code in a single cell,
  pressing the <kbd>Return</kbd> key when in Edit mode (blue) moves the cursor to the next line
  in the cell just like in a text editor.
- We need some other way to tell the Notebook we want to run what's in the cell.
- Pressing <kbd>Shift</kbd>+<kbd>Return</kbd> together will execute the contents of the cell.
- Notice that the <kbd>Return</kbd> and <kbd>Shift</kbd> keys on the right of the keyboard are
  right next to each other.

### The Notebook will turn Markdown into pretty-printed documentation.

- Notebooks can also render [Markdown][markdown].
  - A simple plain-text format for writing lists, links,
    and other things that might go into a web page.
  - Equivalently, a subset of HTML that looks like what you'd send in an old-fashioned email.
- Turn the current cell into a Markdown cell by entering the Command mode (<kbd>Esc</kbd>/gray)
  and press the <kbd>M</kbd> key.
- `In [ ]:` will disappear to show it is no longer a code cell and you will be able to write in
  Markdown.
- Turn the current cell into a Code cell by entering the Command mode (<kbd>Esc</kbd>/gray) and
  press the <kbd>y</kbd> key.

### Markdown does most of what HTML does.

<div class="row">

  <div class="col-md-6" markdown="1">

```
*   Use asterisks
*   to create
*   bullet lists.
```

  

  <div class="col-md-6" markdown="1">

- Use asterisks
- to create
- bullet lists.

  </div>

</div>

<div class="row">

  <div class="col-md-6" markdown="1">

```
1.  Use numbers
1.  to create
1.  numbered lists.
```

  

  <div class="col-md-6" markdown="1">

1. Use numbers
2. to create
3. numbered lists.

  

</div>

<div class="row">

  <div class="col-md-6" markdown="1">

```
*  You can use indents
	*  To create sublists 
	*  of the same type
*  Or sublists
	1. Of different
	1. types
```

  

  <div class="col-md-6" markdown="1">

- You can use indents
  - To create sublists
  - of the same type
- Or sublists

  1. Of different
  2. types

  </div>

</div>

<div class="row">

  <div class="col-md-6" markdown="1">

```
# A Level-1 Heading
```

  

  <div class="col-md-6" markdown="1">

## A Level-1 Heading

  

</div>

<div class="row">

  <div class="col-md-6" markdown="1">

```
## A Level-2 Heading (etc.)
```

  

  <div class="col-md-6" markdown="1">

## A Level-2 Heading (etc.)

  

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

Line breaks
don't matter.

But blank lines
create new paragraphs.

  

</div>

<div class="row">

  <div class="col-md-6" markdown="1">

```
[Create links](http://software-carpentry.org) with `[...](...)`.
Or use [named links][data_carpentry].

[data_carpentry]: http://datacarpentry.org
```

  

  <div class="col-md-6" markdown="1">

[Create links](https://software-carpentry.org) with `[...](...)`.
Or use [named links][data_carpentry].

  

</div>

:::::::::::::::::::::::::::::::::::::::  challenge

## Creating Lists in Markdown

Create a nested list in a Markdown cell in a notebook that looks like this:

1. Get funding.
2. Do work.

- Design experiment.
- Collect data.
- Analyze.

3. Write up.
4. Publish.

:::::::::::::::  solution

## Solution

This challenge integrates both the numbered list and bullet list.
Note that the bullet list is indented 2 spaces so that it is inline with the items of the numbered list.

```
1.  Get funding.
2.  Do work.
    *   Design experiment.
    *   Collect data.
    *   Analyze.
3.  Write up.
4.  Publish.
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## More Math

What is displayed when a Python cell in a notebook
that contains several calculations is executed?
For example, what happens when this cell is executed?

```python
7 * 3
2 + 1
```

:::::::::::::::  solution

## Solution

Python returns the output of the last calculation.

```python
3
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Change an Existing Cell from Code to Markdown

What happens if you write some Python in a code cell
and then you switch it to a Markdown cell?
For example,
put the following in a code cell:

```python
x = 6 * 7 + 12
print(x)
```

And then run it with <kbd>Shift</kbd>+<kbd>Return</kbd> to be sure that it works as a code cell.
Now go back to the cell and use <kbd>Esc</kbd> then <kbd>m</kbd> to switch the cell to Markdown
and "run" it with <kbd>Shift</kbd>+<kbd>Return</kbd>.
What happened and how might this be useful?

:::::::::::::::  solution

## Solution

The Python code gets treated like Markdown text.
The lines appear as if they are part of one contiguous paragraph.
This could be useful to temporarily turn on and off cells in notebooks that get used for multiple purposes.

```python
x = 6 * 7 + 12 print(x)
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Equations

Standard Markdown (such as we're using for these notes) won't render equations,
but the Notebook will.
Create a new Markdown cell
and enter the following:

```
$\sum_{i=1}^{N} 2^{-i} \approx 1$
```

(It's probably easier to copy and paste.)
What does it display?
What do you think the underscore, `_`, circumflex, `^`, and dollar sign, `$`, do?

:::::::::::::::  solution

## Solution

The notebook shows the equation as it would be rendered from LaTeX equation syntax.
The dollar sign, `$`, is used to tell Markdown that the text in between is a LaTeX equation.
If you're not familiar with LaTeX,  underscore, `_`, is used for subscripts and circumflex, `^`, is used for superscripts.
A pair of curly braces, `{` and `}`, is used to group text together so that the statement `i=1` becomes the subscript and `N` becomes the superscript.
Similarly, `-i` is in curly braces to make the whole statement the superscript for `2`.
`\sum` and `\approx` are LaTeX commands for "sum over" and "approximate" symbols.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

## Closing JupyterLab

- From the Menu Bar select the "File" menu and then choose "Shut Down" at the bottom of the dropdown menu. You will be prompted to confirm that you wish to shutdown the JupyterLab server (don't forget to save your work!). Click "Shut Down" to shutdown the JupyterLab server.
- To restart the JupyterLab server you will need to re-run the following command from a shell.

```
$ jupyter lab
```

:::::::::::::::::::::::::::::::::::::::  challenge

## Closing JupyterLab

Practice closing and restarting the JupyterLab server.

::::::::::::::::::::::::::::::::::::::::::::::::::

[jupyterlab]: https://jupyterlab.readthedocs.io/en/stable/

[jupyterlab-ui]: https://jupyterlab.readthedocs.io/en/stable/user/interface.html

[jupyterlab-notebook-docs]: https://jupyterlab.readthedocs.io/en/stable/user/notebook.html

[markdown]: https://en.wikipedia.org/wiki/Markdown

[data_carpentry]: https://datacarpentry.org

:::::::::::::::::::::::::::::::::::::::: keypoints

- Python scripts are plain text files.
- Use the Jupyter Notebook for editing and running Python.
- The Notebook has Command and Edit modes.
- Use the keyboard and mouse to select and edit cells.
- The Notebook will turn Markdown into pretty-printed documentation.
- Markdown does most of what HTML does.

::::::::::::::::::::::::::::::::::::::::::::::::::
