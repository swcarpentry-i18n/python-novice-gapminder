---
title: Запуск та завершення роботи
teaching: 15
exercises: 0
---

::::::::::::::::::::::::::::::::::::::: objectives

- Запуск серверу JupyterLab.
- Створення нового скрипту Python.
- Створення блокноту Jupyter.
- Завершення роботи сервера JupyterLab.
- Розуміння різниці між скриптом Python і блокнотом Jupyter.
- Створення в блокноті комірок типу Markdown.
- Створення та виконання в блокноті комірок Python.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- Як запустити програми Python?

::::::::::::::::::::::::::::::::::::::::::::::::::

Для роботи з Python, протягом цього семінару ми будемо використовувати \[блокноти Jupyter]\[jupyter] у середовищі [JupyterLab][jupyterlab]. Блокноти Jupyter широко застосовуються з метою аналізу та візуалізації даних, а також є зручним інструментальним засобом для запуску коду на Python в інтерактивному режимі, де ми можемо легко переглядати результати його виконання, та ділитися нашим кодом з іншими.

Існують й інші способи редагування, організації та виконання коду. Розробники програмного забезпечення часто використовують інтегроване середовище розробки (IDE), подібне до [PyCharm](https://www.jetbrains. om/pycharm/) або [Visual Studio Code](https://code.visualstudio.com/) або текстові редактори такі як Vim або Emacs, щоб створити та відредагувати свої програми Python. Після редагування та збереження ваших програм Python ви можете виконувати ці програми в самому IDE або безпосередньо в командному рядку. На відміну від цього, блокноти Jupyter дозволяють відразу переглянути результати нашого Python коду.

JupyterLab має декілька інших зручних функцій:

- Ви можете легко вводити, редагувати, копіювати та вставляти блоки коду.
- Автодоповнення за допомогою клавіші Tab дозволяє легко отримувати доступ до назв об'єктів, які ви використовуєте.
- Дозволяє легко доповнювати свій код посиланнями, текстом різного розміру, маркерами тощо, щоб зробити його доступнішим для вас і ваших колег.
- Дозволяє розміщувати графічні елементи безпосередньо поруч із кодом, який їх створює,
  щоб продемонструвати повну історію аналізу даних.

Кожен блокнот містить одну або кілька комірок, що містять код, текст або зображення.

## Початок роботи з JupyterLab

JupyterLab є сервером застосунків із вебінтерфейсом користувача від [Project Jupyter][jupyter], що
дозволяє працювати з документами та іншими застосунками, такими як блокноти Jupyter, текстові редактори, термінали, і навіть спеціальні компоненти, гнучким, інтегрованим і розширюваним способом. JupyterLab потребує досить сучасний браузер (в ідеалі – поточна версія Chrome, Safari або Firefox); Internet Explorer версії 9 і нижче _не_ підтримується.

JupyterLab є частиною інсталяційного пакета Anaconda Python. Якщо ви не встановили дистрибутив Anaconda Python, дивіться інструкції щодо процесу інсталяції [тут](../learners/setup.md).

На цьому уроці ми запустимо JupyterLab локально на наших власних пристроях, тому для цього підключення до Інтернету буде потрібно лише на початку для завантаження та встановлення середовищ розробки Anaconda та JupyterLab

- Запустіть сервер JupyterLab на вашому комп'ютері
- Використовуйте веббраузер для відкриття спеціальної локальної URL-адреси для з'єднання з сервером JupyterLab
- The JupyterLab server does the work and the web browser renders the result
- Type code into the browser and see the results after your JupyterLab server has finished executing your code

:::::::::::::::::::::::::::::::::::::::::  callout

## JupyterLab? А чому не Jupyter Notebook?

JupyterLab є [подальшим кроком в еволюції Jupyter Notebook](https://jupyterlab.readthedocs.io/en/stable/getting_started/overview.html#overview).
Якщо ви використовували Jupyter Notebook раніше, то ви добре зрозумієте діапазон можливостей JupyterLab.

Досвідчені користувачі блокнотів Jupyter, зацікавлені у більш детальному обговоренні схожостей і відмінностей між інтерфейсами JupyterLab і Jupyter Notebook, можуть знайти більше інформації у [документації з інтерфейсу користувача JupyterLab][jupyterlab-ui].

::::::::::::::::::::::::::::::::::::::::::::::::::

## Початок роботи з JupyterLab

Ви можете запустити сервер JupyterLab через командний рядок або через застосунок, що має назву 'Anaconda Navigator'. JupyterLab є частиною інсталяційного пакета Anaconda Python.

### macOS - командний рядок

Для запуску сервера JupyterLab вам потрібно отримати доступ до командного рядка через Terminal.
Існує два способи відкрити термінал на Mac.

1. In your Applications folder, open Utilities and double-click on Terminal
2. Натисніть <kbd>Command</kbd> + <kbd>spacebar</kbd> для запуску Spotlight. Введіть `Terminal`, а потім двічі клацніть на результаті пошуку або натисніть <kbd>Enter</kbd>

Після запуску Terminal введіть команду для запуску сервера JupyterLab.

```bash
$ jupyter lab
```

### Користувачі Windows - Командний рядок

Для запуску сервера JupyterLab вам потрібен застосунок Anaconda Prompt.

Press <kbd>Windows Logo Key</kbd> and search for `Anaconda Prompt`, click the result or press enter.

Після запуску Anaconda Prompt введіть команду:

```bash
$ jupyter lab
```

### Anaconda Navigator

Для запуску серверу JupyterLab з Anaconda Navigator ви маєте спочатку [запустити Anaconda Navigator (натисніть для докладних інструкцій з macOS, Windows та Linux)](https://docs.anaconda.com/free/navigator/getting-started/#navigator-starting-navigator). Ви можете виконати пошук Anaconda Navigator через Spotlight на macOS (<kbd>Command</kbd> + <kbd>spacebar</kbd>), скористатися функцією пошуку Windows (<kbd>ключ Windows Logo</kbd>) або відкривши термінал та виконавши команду `anaconda-navigator` у командному рядку.

Після того, як ви запустили Anaconda Navigator, натисніть кнопку `Launch` під JupyterLab. Можливо, вам знадобиться продивитись список донизу, аби знайти її.

Нижче наведено скриншот сторінки Anaconda Navigator, схожої на ту, яка має відкриватися для macOS або Windows.

<p align='center'>
  <img alt="Anaconda Navigator landing page" src="fig/0_anaconda_navigator_landing_page.png" width="750"/>
</p>

Нижче наведено скриншот екрана стартової сторінки JupyterLab, схожої на ту, яка має відкритися у вашому веббраузері за замовчуванням після запуску сервера JupyterLab в операційній системі macOS або Windows.

<p align='center'>
  <img alt="JupyterLab landing page" src="fig/0_jupyterlab_landing_page.png" width="750"/>
</p>

## Інтерфейс JupyterLab

JupyterLab має багато функцій, які можна знайти в традиційних інтегрованих середовищах розробки (IDE), але його особливістю є забезпечення гнучких "будівельних блоків" для інтерактивних дослідницьких обчислень.

[Інтерфейс JupyterLab][jupyterlab-ui] складається з панелі меню, лівої бічної панелі (що згортається за потреби), і основної робочої області, яка містить вкладки з документами та різними застосунками JupyterLab.

### Панель меню

Панель меню у верхній частині вікна JupyterLab містить меню верхнього рівня, яке зображує різні дії доступні в JupyterLab разом із їхніми комбінаціями клавіш (де це можливо). Наступні пункти меню наявні за замовчуванням.

- **File:** Дії, пов’язані з файлами та каталогами, такі як _New_, _Open_, _Close_, _Save_ тощо. Меню _File_ також містить дію _Shut Down_, яка застосовується для завершення роботи сервера JupyterLab.
- **Edit:** Дії, пов’язані з редагуванням документів та іншими видами діяльності, такими як _Undo_, _Cut_, _Copy_, _Paste_ тощо.
- **View:** Дії, які змінюють зовнішній вигляд інтерфейсу JupyterLab.
- **Run:** Дії для запуску коду в різних застосунках, таких як Jupyter Notebook та командний рядок (розглянуто нижче).
- \*\* Kernel:\*\* Дії щодо управління ядрами. Ядра у Jupyter будуть детально описані нижче.
- **Tabs:** Список відкритих документів та застосунків у робочій області.
- **Settings:** За допомогою цього меню можна налаштувати загальні параметри JupyterLab. Окрім того, у ньому також є опція _Advanced Settings Editor_, яка забезпечує більш детальний контроль параметрів і опцій для конфігурації JupyterLab.
- **Help:** Список посилань на довідку JupyterLab та інші ресурси.

:::::::::::::::::::::::::::::::::::::::::  callout

## Ядра

The JupyterLab [docs](https://jupyterlab.readthedocs.io/en/stable/user/documents_kernels.html)
define kernels as "separate processes started by the server that runs your code in different programming languages and environments."
When we open a Jupyter Notebook, that starts a kernel - a process - that is going to run the code.
In this lesson, we'll be using the Jupyter ipython kernel which lets us run Python 3 code interactively.

Using other Jupyter [kernels for other programming languages](https://github.com/jupyter/jupyter/wiki/Jupyter-kernels) would let us
write and execute code in other programming languages in the same JupyterLab interface, like R, Java, Julia, Ruby, JavaScript, Fortran,
etc.

::::::::::::::::::::::::::::::::::::::::::::::::::

A screenshot of the default Menu Bar is provided below.

<p align='center'>   <img alt="JupyterLab Menu Bar" src="fig/0_jupyterlab_menu_bar.png" width="750"/>
</p>

### Ліва бічна панель

The left sidebar contains a number of commonly used tabs, such as a file browser (showing the
contents of the directory where the JupyterLab server was launched), a list of running kernels
and terminals, the command palette, and a list of open tabs in the main work area. A screenshot of
the default Left Side Bar is provided below.

<p align='center'>   <img alt="JupyterLab Left Side Bar" src="fig/0_jupyterlab_left_side_bar.png" width="250"/>
</p>

The left sidebar can be collapsed or expanded by selecting "Show Left Sidebar" in the View menu or
by clicking on the active sidebar tab.

### Основна робоча область

Основна робоча область в JupyterLab дозволяє упорядковувати документи (блокноти, текстові файли та ін.)
and other activities (terminals, code consoles, etc.) на панелях вкладок, які можуть бути змінені або
розділені. A screenshot of the default Main Work Area is provided below.

Якщо Ви не бачите вкладку Launcher на панелі запуску, натисніть синій плюс під знаком "Файл" та "Редагувати", і ця вкладка з'явиться.

<p align='center'>   <img alt="JupyterLab Main Work Area" src="fig/0_jupyterlab_main_work_area.png" width="750"/>
</p>

Drag a tab to the center of a tab panel to move the tab to the panel. Розділіть панель вкладок за допомогою перетягування вкладки ліворуч, праворуч, до верху або до низу панелі. Робоча панель має одну поточну дію. Вкладка для поточної дії позначена кольоровою верхньою рамкою (за замовчуванням - синьою).

## Creating a Python script

- To start writing a new Python program click the Text File icon under the _Other_ header in the Launcher tab of the Main Work Area.
  - You can also create a new plain text file by selecting the _New -> Text File_ from the _File_ menu in the Menu Bar.
- To convert this plain text file to a Python program, select the _Save File As_ action from the _File_ menu in the Menu Bar and give your new text file a name that ends with the `.py` extension.
  - The `.py` extension lets everyone (including the operating system) know that this text file is a Python program.
  - Це умовність, а не вимога.

## Створення Jupyter Notebook

To open a new notebook click the Python 3 icon under the _Notebook_ header in the Launcher tab in
the main work area. You can also create a new notebook by selecting _New -> Notebook_ from the _File_ menu in the Menu Bar.

Додаткові зауваження щодо Jupyter notebooks.

- Файли, створені в Jupiter Notebook, мають розширення `.ipynb`, щоб відрізнити їх від програм на Python, створених як звичайний текстовий файл.
- Notebooks can be exported as Python scripts that can be run from the command line.

Нижче наведено скриншот екрана Jupyter Notebook, який працює в JupyterLab. If you are interested in
more details, then see the [official notebook documentation][jupyterlab-notebook-docs].

<p align='center'>   <img alt="Example Jupyter Notebook" src="fig/0_jupyterlab_notebook_screenshot.png" width="750"/>
</p>

:::::::::::::::::::::::::::::::::::::::::  callout

## Як це зберігається

- Файл блокноту зберігається у форматі JSON.
- Подібно до вебсторінки, те, що зберігається, відрізняється від того, що ви бачите у своєму браузері.
- Але формат JSON дозволяє Jupyter змішувати вихідний код, текст і зображення в одному файлі.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Упорядкування документів в панелях вкладок

У головній робочій області JupyterLab ви можете впорядковувати документи на панелі вкладок. Here is an
example from the [official documentation][jupyterlab].

<p align='center'>   <img alt="Multi-panel JupyterLab" src="fig/0_multipanel_jupyterlab_screenshot.png" width="750"/>
</p>

First, create a text file, Python console, and terminal window and arrange them into three
panels in the main work area. Next, create a notebook, terminal window, and text file and
arrange them into three panels in the main work area. Finally, create your own combination of
panels and tabs. What combination of panels and tabs do you think will be most useful for your
workflow?

:::::::::::::::  solution

## Рішення

After creating the necessary tabs, you can drag one of the tabs to the center of a panel to
move the tab to the panel; next you can subdivide a tab panel by dragging a tab to the left,
right, top, or bottom of the panel.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## Код проти тексту

Jupyter дозволяє змішувати код і текст у різних типах блоків, які називаються комірками. We often use the term
"code" to mean "the source code of software written in a language such as Python".
A "code cell" in a Notebook is a cell that contains software;
a "text cell" is one that contains ordinary prose written for human beings.

::::::::::::::::::::::::::::::::::::::::::::::::::

## The Notebook has Command and Edit modes.

- If you press <kbd>Esc</kbd> and <kbd>Return</kbd> alternately, the outer border of your code cell will change from gray to blue.
- These are the **Command** (gray) and **Edit** (blue) modes of your notebook.
- Command mode allows you to edit notebook-level features, and Edit mode changes the content of cells.
- В командному режимі (esc/сірий),
  - The <kbd>b</kbd> key will make a new cell below the currently selected cell.
  - The <kbd>a</kbd> key will make one above.
  - The <kbd>x</kbd> key will delete the current cell.
  - The <kbd>z</kbd> key will undo your last cell operation (which could be a deletion, creation, etc).
- Усі дії можна виконувати за допомогою меню, але є багато комбінацій клавіш для прискорення процесу.

:::::::::::::::::::::::::::::::::::::::  challenge

## Command Vs. Edit

In the Jupyter notebook page are you currently in Command or Edit mode?\
Switch between the modes.
Use the shortcuts to generate a new cell.
Use the shortcuts to delete a cell.
Use the shortcuts to undo the last cell operation you performed.

:::::::::::::::  solution

## Рішення

Рішення Командний режим має сіру рамку, а режим редагування — синю.
Use <kbd>Esc</kbd> and <kbd>Return</kbd> to switch between modes.
You need to be in Command mode (Press <kbd>Esc</kbd> if your cell is blue).  Введіть <kbd>b</kbd> або <kbd>a</kbd>.
You need to be in Command mode (Press <kbd>Esc</kbd> if your cell is blue).  Введіть <kbd>x</kbd>.
You need to be in Command mode (Press <kbd>Esc</kbd> if your cell is blue).  Введіть <kbd>z</kbd>.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

### Use the keyboard and mouse to select and edit cells.

- Якщо натиснути клавішу <kbd>Return</kbd>, рамка стане синьою та ввімкнеться режим редагування, що дозволяє введення команди в комірку.
- Because we want to be able to write many lines of code in a single cell,
  pressing the <kbd>Return</kbd> key when in Edit mode (blue) moves the cursor to the next line
  in the cell just like in a text editor.
- We need some other way to tell the Notebook we want to run what's in the cell.
- Pressing <kbd>Shift</kbd>\+<kbd>Return</kbd> together will execute the contents of the cell.
- Notice that the <kbd>Return</kbd> and <kbd>Shift</kbd> keys on the right of the keyboard are
  right next to each other.

### Notebook підтримує мову розмітки текстів Markdown

- Notebooks can also render [Markdown][markdown].
  - Простий текстовий формат для запису списків, посилань та інших елементів, які можуть з'являтися на  вебсторінці.
  - Власне, це підмножина HTML, яка виглядає у стилі старомодного електронного листа.
- Turn the current cell into a Markdown cell by entering the Command mode (<kbd>Esc</kbd>/gray)
  and press the <kbd>M</kbd> key.
- `In [ ]:` will disappear to show it is no longer a code cell and you will be able to write in
  Markdown.
- Turn the current cell into a Code cell by entering the Command mode (<kbd>Esc</kbd>/gray) and
  press the <kbd>y</kbd> key.

### Markdown робить більшість того, що робить HTML.

Table: Showing some markdown syntax and its rendered output.

+---------------------------------------+------------------------------------------------+
\| Markdown code                         | Rendered output                                |
+=======================================+================================================+
+---------------------------------------+------------------------------------------------+
\| `                                  | <p></p>                                        | | *   Use asterisks                     | -   Use asterisks                              | | *   to create                         | -   to create                                  | | *   bullet lists.                     | -   bullet lists.                              |
|`                                   |                                                |
+---------------------------------------+------------------------------------------------+
+---------------------------------------+------------------------------------------------+
\| `                                  | <p></p>                                        | | 1.   Use numbers                      | 1.   Use numbers                               | | 1.   to create                        | 2.   to create                                 | | 1.   bullet lists.                    | 3.   нумеровані списки.                           |
|`                                   |                                                |
+---------------------------------------+------------------------------------------------+
+---------------------------------------+------------------------------------------------+
\| `                                  | <p></p>                                        | | *  You can use indents                | - You can use indents                          | |   *  To create sublists               |   - To create sublists                         | |   *  of the same type                 |   - of the same type                           | | *  Or sublists                        | - Or sublists                                  | |   1. Of different                     |   1. Of different                              | |   1. types                            |   2. types                                     |
|`                                   |                                                |
+---------------------------------------+------------------------------------------------+
+---------------------------------------+------------------------------------------------+
\| `                                  | <p></p>                                        | | # A Level-1 Heading                   | ## A Level-1 Heading                           |
|`                                   |                                                |
+---------------------------------------+------------------------------------------------+
+---------------------------------------+------------------------------------------------+
\| `                                  | <p></p>                                        | | ## A Level-2 Heading (etc.)           | ### A Level-2 Heading (etc.)                   |
|`                                   |                                                |
+---------------------------------------+------------------------------------------------+
+---------------------------------------+------------------------------------------------+
\| `                                  | <p></p>                                        | | Line breaks                           | Line breaks                                    | | don't matter.                         | don't matter.                                  | |                                       |                                                | | But blank lines                       | But blank lines                                | | create new paragraphs.                | create new paragraphs.                         |
|`                                   |                                                |
+---------------------------------------+------------------------------------------------+
+---------------------------------------+------------------------------------------------+
\| ``                                  | <p></p>                                        | | [Links](http://software-carpentry.org)| [Links](https://software-carpentry.org)        | | are created with `[...](...)`.        | are created with `[...](...)`.                 | | Or use [named links][data-carp].      | Or use [named links][data_carpentry].          | |                                       |                                                | | [data-carp]: http://datacarpentry.org |                                                |
|``                                   |                                                |
+---------------------------------------+------------------------------------------------+

:::::::::::::::::::::::::::::::::::::::  challenge

## Створення списків в Markdown

Create a nested list in a Markdown cell in a notebook that looks like this:

1. Знайти фінансування.
2. Виконати роботу.

- Провести експеримент.
- Зібрати дані.
- Провести аналіз.

3. Написати статтю.
4. Опублікувати.

:::::::::::::::  solution

## Рішення

Рішення Це завдання поєднує як нумерований, так і маркований списки.
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

## Більше математики

What is displayed when a Python cell in a notebook
that contains several calculations is executed?
Наприклад, що трапиться при виконанні дій наступної комірки?

```python
7 * 3
2 + 1
```

:::::::::::::::  solution

## Рішення

Python повертає результат останнього розрахунку.

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

А потім запустіть цей код в комірці за допомогою <kbd>Shift</kbd>\+<kbd>Return</kbd>, щоб переконатися, що ця комірка працює як комірка коду.
Тепер поверніться до комірки та натисніть <kbd>Esc</kbd>, а потім <kbd>m</kbd>, щоб перемкнути комірку на Markdown і "запустити" її за допомогою <kbd>Shift</kbd>\+<kbd>Return</kbd>.
Що сталося, і як це може бути корисним?

:::::::::::::::  solution

## Рішення

Код Python розглядається як текст Markdown.
Рядки виглядають так, ніби вони є частиною одного суміжного абзацу.
This could be useful to temporarily turn on and off cells in notebooks that get used for multiple purposes.

```python
x = 6 * 7 + 12 print(x)
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Рівняння

Стандартний Markdown (наприклад, такий, що використовується для цих нотаток) не надаватиме рівняння, але Notebook буде.
Створіть нову комірку Markdown і введіть наступне:

```
$\sum_{i=1}^{N} 2^{-i} \approx 1$
```

(Мабуть, легше скопіювати та вставити.)
What does it display?
Що ви думаєте про підкреслювання, `_`, циркумфлекс, `^` і доларовий знак, `$`, далі?

:::::::::::::::  solution

## Рішення

У блокноті показано рівняння з синтаксисом рівняння LaTeX.
The dollar sign, `$`, is used to tell Markdown that the text in between is a LaTeX equation.
Якщо ви не знайомі з LaTeX, підкреслення, `_`, використовується для підрядкових індексів та циркумфлекс, `^`, використовується для верхніх індексів.
Пара фігурних дужок, `{` та `}`, використовується для групування тексту разом, щоб вираз `i=1` став нижнім та `N` - верхнім індексом.
Аналогічно, вираз `-i` взятий у фігурні дужки, щоб зробити цей вираз верхнім індексом для `2`.
`\sum` та `\approx` є командами LaTeX для значень "sum over" й "approximate".

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

## Закриття JupyterLab

- From the Menu Bar select the "File" menu and then choose "Shut Down" at the bottom of the dropdown menu. Вам буде запропоновано підтвердити, що Ви бажаєте вимкнути сервер JupyterLab (не забудьте зберегти свою роботу!). Click "Shut Down" to shutdown the JupyterLab server.
- To restart the JupyterLab server you will need to re-run the following command from a shell.

```
$ jupyter lab
```

:::::::::::::::::::::::::::::::::::::::  challenge

## Закриття JupyterLab

Потренуйтеся закривати та перезапускати сервер JupyterLab.

::::::::::::::::::::::::::::::::::::::::::::::::::

[jupyterlab]: https://jupyterlab.readthedocs.io/en/stable/
[jupyterlab-ui]: https://jupyterlab.readthedocs.io/en/stable/user/interface.html
[jupyterlab-notebook-docs]: https://jupyterlab.readthedocs.io/en/stable/user/notebook.html
[markdown]: https://en.wikipedia.org/wiki/Markdown
[data_carpentry]: https://datacarpentry.org

:::::::::::::::::::::::::::::::::::::::: keypoints

- Python scripts are plain text files.
- Застосування Jupyter Notebook для редагування та запуску Python
- Jupiter Notebook має режими команд та редагування
- Use the keyboard and mouse to select and edit cells.
- Notebook підтримує мову розмітки текстів Markdown
- Markdown виконує більшість функцій HTML.

::::::::::::::::::::::::::::::::::::::::::::::::::
