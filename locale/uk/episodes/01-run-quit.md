---
title: Біг і вихід
teaching: 15
exercises: 0
---

::::::::::::::::::::::::::::::::::::::::::::: цілеї

- Запустіть сервер JupyterLab .
- Create a new Python script.
- Створити зошит.
- Завершення роботи сервера JupyterLab .
- Зрозумійте різницю між писемністю на Python і зошитом.
- Створення клітин Markdown в зошиті.
- Створюйте і запускайте Python клітини в блокноті.

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: питань

- Як можна запускати програми на Python?

::::::::::::::::::::::::::::::::::::::::::::::::::

To run Python, we are going to use \[Jupyter Notebooks]\[jupyter] via [JupyterLab][jupyterlab] for the remainder of this workshop. Блокноти Jupyter поширені в вивченні даних, а також в зручному вигляді зручного розповсюдженого знаменника для запуску коду на Python з інтерактивним методом, де ми можемо легко переглядати і обмінюватися результатами нашого коду на Python.

Є й інші способи редагування, управління та запуску. Програмні розробники часто використовують інтегроване середовище розробки (IDE), подібне до [PyCharm](https\://www\.jetbrains. om/pycharm/) або [Visual Studio Code](https://code.visualstudio.com/) або текстові редакції, такі як Vim або Emacs, щоб створити та відредагувати свої програми Python. Після редагування та збереження ваших програм Python ви можете виконувати ці програми в самому IDE або безпосередньо в командному рядку. Навпаки, блокноти Jupyter дозволяють нам виконувати і переглянути результати нашого коду на Python відразу в зошиті.

JupyterLab має декілька інших зручних функцій:

- Ви можете легко друкувати, редагувати і вставляти блоки коду.
- Tab complete allows you to easily access the names of things you are using
  and learn more about them.
- It allows you to annotate your code with links, different sized text, bullets, etc.
  to make it more accessible to you and your collaborators.
- It allows you to display figures next to the code that produces them
  to tell a complete story of the analysis.

Кожен блокнот містить одну або кілька клітин, які містять код, текст або зображення.

## Початок роботи з JupyterLab

JupyterLab is an application server with a web user interface from [Project Jupyter][jupyter] that
enables one to work with documents and activities such as Jupyter notebooks, text editors, terminals,
and even custom components in a flexible, integrated, and extensible manner. JupyterLab потребує новітню версію
(переважно поточна версія Chrome, Safari, Firefox); Internet
Explorer 9 і нижче _не підтримуються_.

JupyterLab включається як частина розподілу Anaconda Python. Якщо у вас вже немає
встановив Розподіл Anaconda Python, завітайте [інструкції з встановлення](../learners/setup.md)
для встановлення інструкцій.

In this lesson we will run JupyterLab locally on our own machines so it will not require an internet connection besides
the initial connection to download and install Anaconda and JupyterLab

- Запустити сервер JupyterLab на вашому комп'ютері
- Використовуйте веб-браузер для відкриття спеціальної localhost URL-адреси, яка з'єднується з сервером JupyterLab
- Сервер JupyterLab робить роботу і веб-браузер дає результат
- Введіть код в браузері і побачте результати після того, як сервер JupyterLab закінчив виконання коду

:::::::::::::::::::::::::::::::::::::::::  callout

## JupyterLab? Що можна сказати про блокноти Jupyter?

JupyterLab - це [наступний етап в еволюції блокнота JupyterLab (https\://jupyterlab.readthedocs.io/en/stable/getting_started/overview\.html#overview).
Якщо ви вже робили досвід роботи з блокнотами Jupyter, то у вас буде хороший висновок, що очікується від JupyterLab.

Досвідчені користувачі блокнотів Jupyter, зацікавлені у більш докладному обговоренні схожостей і відмінностей
між JupyterLab і Jupyter notebook інтерфейсами можуть знайти більше інформації в інтерфейсі
[JupyterLab користувацької документації з інтерфейсом ][jupyterlab-ui].

::::::::::::::::::::::::::::::::::::::::::::::::::

## Запуск JupyterLab

Ви можете запустити сервер JupyterLab через командний рядок або через додаток, що називається
'Анаконда Navigator'. У Анаконда Навігатор включено як частину розподілу Анаконди Python.

### macOS - командний рядок

Для запуску сервера JupyterLab вам потрібно буде отримати доступ до командного рядка через Terminal.
Існує два способи відкрити термінал на Mac.

1. У вашій папці програм відкрийте Утиліти та двічі клацніть на терміналі
2. Press <kbd>Command</kbd> + <kbd>spacebar</kbd> to launch Spotlight. Введіть `Terminal`, а потім
   двічі клацніть на результат пошуку або натисніть <kbd>Введіть</kbd>

Після того, як ви запустили Terminal, введіть команду для запуску сервера JupyterLaby.

```bash
$ jupyter lab
```

### Користувачі Windows - командний рядок

Щоб запустити сервер JupyterLab вам потрібно отримати доступ до програми Anaconda Prompt.

Натисніть <kbd>Ключ логотипу Windows</kbd> і пошукайте «Анаконда підказку», натисніть результат або натисніть клавішу Enter.

Після того, як ви запустили Команду Анаконда, введіть команду:

```bash
$ jupyter lab
```

### Anaconda Navigator

Щоб запустити сервер JupyterLab з Anaconda Navigator ви повинні спочатку [запустіть Anaconda Navigator (натисніть для докладних інструкцій на macOS, Windows та Linux)](https://docs.anaconda.com/free/navigator/getting-started/#navigator-starting-navigator). Ви можете виконати пошук Anaconda Navigator через Spotlight на macOS (<kbd>Command</kbd> + <kbd>spacebar</kbd>), функція пошуку Windows (<kbd>ключ Windows Logo</kbd>) або відкриття термінальної оболонки і виконання команди `anaconda-navigator`, виконуваний з командного рядка.

Після того, як ви запустили Anaconda Navigator, натисніть кнопку `Launch` під JupyterLab. Можливо, вам знадобиться
для прокручування донизу, аби знайти її.

Ось скріншот сторінки навігації Anaconda Navigator подібний до той, що має відкриватися для macOS
або Windows.

<p align='center'>
  <img alt="Anaconda Navigator landing page" src="fig/0_anaconda_navigator_landing_page.png" width="750"/>
</p>

І ось знімок екрана JupyterLab цільової сторінки, яка повинна бути схожа на ту, що відкривається у вашій
за замовчуванням веб браузер після запуску сервера JupyterLab на macOS або Windows.

<p align='center'>
  <img alt="JupyterLab landing page" src="fig/0_jupyterlab_landing_page.png" width="750"/>
</p>

## Інтерфейс Юпітерлабораторії

JupyterLab знайшов багато функцій в традиційних інтегрованих середовищах розробки (IDE), але
орієнтовано на забезпечення гнучких цеглинок для інтерактивних, дослідницьких обчислень.

\[Інтерфейс JupyterLab[jupyterlab-ui]
складається з «Меню», руйнуючого лівого бокового бару, і основна Робоча область, яка містить вкладки
документів та діяльності.

### Смужка меню

Панель меню в JupyterLab має меню верхнього рівня, який викриває різні дії
в JupyterLab разом з комбінацією клавіш (де це застосовано). Наступна
меню включено за замовчуванням.

- **Файл:** Дії пов'язані з файлами і теками, такими як _Нове_, _Відкрити_, _Закрити_, _Зберегти_, тощо. Меню _Файл_ також включає дію \* Завершення відтворення, що використовується для завершення сервера JupyterLab (функції).
- **Змінити:** Дії пов'язані з редагуванням документів та іншими видами дій, такими як _Undo_, _Cut_, _Copy_, _Paste_, і т. д.
- **Перегляд:** Дії, які змінюють зовнішній вигляд JupyterLab.
- **Запустіть:** Дії з кодом різних дій, таких як блокноти та консолі коду (обговорюється нижче).
- **Ядро:** Дії щодо управління ядрами. Ядра в Юпітері будуть детально описані нижче.
- **Вкладки:** Список відкритих документів і заходів у головній робочій області.
- **Налаштування:** Загальні налаштування JupyterLab можуть бути налаштовані через це меню. Також існує опція \* Розширений редактор налаштувань\* в випадаючому меню, що забезпечує більш тонкий контроль над налаштуваннями JupyterLab та варіантами конфігурації.
- **Допоможіть** Список JupyterLab і ядра допоміжних зв'язків.

:::::::::::::::::::::::::::::::::::::::::  callout

## Ядра

JupyterLab [docs](https://jupyterlab.readthedocs.io/en/stable/user/documents_kernels.html)
визначають явища як "окремі процеси, які запускають ваш код з різних мов програмування та середовища."
Коли ми відкриємо Jupyter Notebook, який запускає ядро - процес - який запускає код.
На цьому уроці ми будемо використовувати ядро Jupyter ipython , яке дозволяє нам запускати Python 3 код інтерактивно.

Using other Jupyter [kernels for other programming languages](https://github.com/jupyter/jupyter/wiki/Jupyter-kernels) would let us
write and execute code in other programming languages in the same JupyterLab interface, like R, Java, Julia, Ruby, JavaScript, Fortran,
etc.

::::::::::::::::::::::::::::::::::::::::::::::::::

Скріншот рядка меню за замовчуванням знаходиться нижче.

<p align='center'>   <img alt="JupyterLab Menu Bar" src="fig/0_jupyterlab_menu_bar.png" width="750"/>
</p>

### Left Sidebar

Ліва бічна панель містить кілька зазвичай використаних вкладок, наприклад файловий браузер (відображення
вміст каталогу на якому був запущений сервер JupyterLab сервері), список працюючих ядер
і терміналів, командна палітра і список відкритих вкладок в головній області роботи. Скріншот
обрана ліва панель за замовчуванням знаходиться нижче.

<p align='center'>   <img alt="JupyterLab Left Side Bar" src="fig/0_jupyterlab_left_side_bar.png" width="250"/>
</p>

The left sidebar can be collapsed or expanded by selecting "Show Left Sidebar" in the View menu or
by clicking on the active sidebar tab.

### Основна робоча область

Основна робоча область в JupyterLab дозволяє організовувати документи (ноутбуки, текстові файли і т. д.)
та інші види діяльності (терміни, консолі коду та ін.) на панелі вкладок, які можуть бути змінені або
розділені на панелі вкладок. Зняток стандартної робочої області наведено нижче.

Якщо Ви не бачите вкладку Launcher на панелі запуску, натисніть синій плюс під знаком "Файл" та "Редагувати" і він з'явиться.

<p align='center'>   <img alt="JupyterLab Main Work Area" src="fig/0_jupyterlab_main_work_area.png" width="750"/>
</p>

Перетягніть вкладку в центр панелі вкладок для переміщення вкладки на панель. Розділіть панель вкладки на
перетягування вкладки ліворуч, зверху, або нижню частину панелі. Робоча область має одну поточну
активність. Вкладка для поточної діяльності позначена кольоровою верхньою межею (синьою за замовчуванням).

## Створення скрипту Python

- Щоб почати писати нову програму Python, натисніть на іконку текстового файлу в заголовку _Іншого_ в вкладці Launcher в основній робочої області.
  - Ви також можете створити новий текстовий файл, обравши \*Новий -> Текстовий файл \* з меню _Файл_ в рядку меню.
- Щоб перетворити цей простий текстовий файл у програму Python, виберіть _Зберегти файл як_ з меню _File_ в рядку меню, і дайте ваш новий текстовий файл ім'я яке закінчується на `. y` розширення.
  - Розширення `.py` дозволить всім (включаючи операційну систему) знати, що цей текстовий файл це програма Python.
  - Це норма, а не вимога.

## Створення блокноту Jupyter

Щоб відкрити новий блокнот, натисніть на іконку Python 3 у заголовку _Notebook_ у вкладці Launcher в
в основній робочій області. Також можна створити новий блокнот, обравши _Нове -> Notebook_ в меню _File_ в меню.

Додаткові нотатки на Юпітері зошиті.

- Блокнот файли мають розширення `.ipynb`, щоб відрізнити їх від текстових програм на Python.
- Блокноти можна експортувати як скрипти Python, які можуть бути виконані з командного рядка.

Нижче наведено скріншот блокнота Jupyter, який працює в JupyterLab. Якщо ви зацікавлені в
більш докладну інформацію, тоді перегляньте [офіційну документацію з блокноту][jupyterlab-notebook-docs].

<p align='center'>   <img alt="Example Jupyter Notebook" src="fig/0_jupyterlab_notebook_screenshot.png" width="750"/>
</p>

:::::::::::::::::::::::::::::::::::::::::  callout

## Як зберігається

- Записник файл зберігається в форматі JSON.
- Як і веб-сторінка, збережена інформація виглядає відмінно від того, що ви бачите в браузері.
- Але цей формат дозволяє Jupyter змішувати вихідний код, текст та зображення в одному файлі.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Впорядкування документів в панелі вкладок

В головній робочій зоні JupyterLab ви можете помістити документи на панелі вкладок. Here is an
example from the [official documentation][jupyterlab].

<p align='center'>   <img alt="Multi-panel JupyterLab" src="fig/0_multipanel_jupyterlab_screenshot.png" width="750"/>
</p>

Спочатку створіть текстовий файл, консоль Python, вікно і перемістить їх у три
панелі в основній робочій області. Далі, створити блокнот, вікно терміналу, і текстовий файл і
вживати їх на три панелі в основній робочій області. Нарешті, створіть власну комбінацію
панелей та вкладок. What combination of panels and tabs do you think will be most useful for your
workflow?

:::::::::::::::::::: Рішення

## Розв'язок

After creating the necessary tabs, you can drag one of the tabs to the center of a panel to
move the tab to the panel; next you can subdivide a tab panel by dragging a tab to the left,
right, top, or bottom of the panel.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## Код проти тексту

Код і текст вимірюються різними типами блоків, що називаються клітинами. Ми часто використовуємо термін
"код" для позначення "код програмного забезпечення, написане мовою на кшталт Python".
В блокноті "кодова клітина" - це клітина, що містить програму;
текстова клітинка містить простий, написаний для людей.

::::::::::::::::::::::::::::::::::::::::::::::::::

## У блокноті є команди і режими редагування.

- Якщо ви натиснете <kbd>Esc</kbd> та <kbd>Повертає</kbd> по черзі, зовнішня межа вашого кодові клітинки зміняться з сірого на синій.
- Це **Команда** (сірий) та **Редагувати** (синій) режими вашого зошиту.
- Командний режим дозволяє редагувати функції рівня зошита та змінювати вміст клітин.
- Коли в командному режимі (позиція/сіра)
  - The <kbd>b</kbd> key will make a new cell below the currently selected cell.
  - The <kbd>a</kbd> key will make one above.
  - The <kbd>x</kbd> key will delete the current cell.
  - The <kbd>z</kbd> key will undo your last cell operation (which could be a deletion, creation, etc).
- Усі дії можна робити за допомогою меню клавіатури, але їх можна прискорити.

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Командування Vs. Редагувати

На сторінці в блокноті Jupyter ви зараз перебуваєте в режимі командування або редагування?\
Перемикання між режимами.
Використовуйте ярлики для генерації нової клітини.
Використовуйте ярлики для видалення клітини.
Відкотити останні операції з клітинки, які ви виконали.

:::::::::::::::::::: Рішення

## Розв'язок

Командний режим має сіру межу і режим редагування має сині кордони.
Використайте <kbd>Esc</kbd> та <kbd>return</kbd> для перемикання між режимами.
You need to be in Command mode (Press <kbd>Esc</kbd> if your cell is blue).  Type <kbd>b</kbd> or <kbd>a</kbd>.
You need to be in Command mode (Press <kbd>Esc</kbd> if your cell is blue).  Введіть <kbd>x</kbd>.
You need to be in Command mode (Press <kbd>Esc</kbd> if your cell is blue).  Type <kbd>z</kbd>.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

### Скористайтеся клавіатурою та мишкою, щоб вибрати та відредагувати клітини.

- Pressing the <kbd>Return</kbd> key turns the border blue and engages Edit mode, which allows
  you to type within the cell.
- Because we want to be able to write many lines of code in a single cell,
  pressing the <kbd>Return</kbd> key when in Edit mode (blue) moves the cursor to the next line
  in the cell just like in a text editor.
- Нам потрібно ще один спосіб розповісти про це у блокноті, ми хочемо запустити що в клітині.
- Натиснувши <kbd>Shift</kbd>+<kbd>return</kbd> разом виконуватиме вміст клітини.
- Notice that the <kbd>Return</kbd> and <kbd>Shift</kbd> keys on the right of the keyboard are
  right next to each other.

### Блокнот перетворить Markdown на надруковану документацію красивого.

- Notebooks can also render [Markdown][markdown].
  - Простий текстовий формат для запису списків, посилань,
    та інших речей, які можуть переходити на веб-сторінку.
  - Прийнято, піднабір HTML, який виглядає як ви відправите старомодну електронну пошту.
- Turn the current cell into a Markdown cell by entering the Command mode (<kbd>Esc</kbd>/gray)
  and press the <kbd>M</kbd> key.
- `У [ ]:` зникне, що це вже не кодова комірка, і ви зможете записати в
  Markdown.
- Turn the current cell into a Code cell by entering the Command mode (<kbd>Esc</kbd>/gray) and
  press the <kbd>y</kbd> key.

### Markdown робить більшість з HTML коду.

<div class="row">

  <div class="col-md-6" markdown="1">

```
* Використовувати asterisks
* для створення
* куль списків.
```

  

  <div class="col-md-6" markdown="1">

- Використовувати зірочки
- створити
- кулькові списки.

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

1. Використовувати номери
2. створити
3. нумерований список.

  

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

- Ви можете використовувати відступ
  - Для створення підсписків
  - з того ж типу
- Або підсписки

  1. З іншого
  2. типи

  </div>

</div>

<div class="row">

  <div class="col-md-6" markdown="1">

```
# Заголовок рівня 1
```

  

  <div class="col-md-6" markdown="1">

## Заголовок

  

</div>

<div class="row">

  <div class="col-md-6" markdown="1">

```
## Заголовок рівня 2 (і т. д.)
```

  

  <div class="col-md-6" markdown="1">

## Заголовок рівня (і т. д.)

  

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

Але порожні лінії
створити нові абзаци.

  

</div>

<div class="row">

  <div class="col-md-6" markdown="1">

```
[Створити посилання](http://software-carpentry.org) з `[...](...)`.
Або використайте [named links][data_carpentry].

[data_carpentry]: http://datacarpentry.org
```

  

  <div class="col-md-6" markdown="1">

[Створити посилання](https://software-carpentry.org) з `[...](...)`.
Або використовуйте [named links][data_carpentry].

  

</div>

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Створення списків в Markdown

Створіть вкладений список в комірці Markdown в записнику, який виглядає так:

1. Отримуй фінансування.
2. Зробіть роботу.

- Експеримент з дизайну.
- Збирайте дані.
- Проаналізуємо.

3. Запишіть це.
4. Опублікувати.

:::::::::::::::::::: Рішення

## Розв'язок

Цей виклик інтегрує нумерований список і список куль.
Зверніть увагу, що список куль є відступом з 2 просторами для того, щоб він був вбудований з елементами нумерованого списку.

```
1. Отримуйте фінансування.
2. Зробіть роботу.
    * Конзайн експеримент.
    * Збирайте дані.
    * Аналіз.
3. Напишіть
4. Видавати.
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Більше математики

What is displayed when a Python cell in a notebook
that contains several calculations is executed?
Наприклад, що трапиться коли клітина буде виконана?

```python
7 * 3
2 + 1
```

:::::::::::::::::::: Рішення

## Розв'язок

Python повертає результат останнього розрахунку.

```python
3
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Змінити існуючу клітинку з коду на Markdown

What happens if you write some Python in a code cell
and then you switch it to a Markdown cell?
Наприклад,
покласти наступне в кодову клітинку:

```python
x = 6 * 7 + 12
print(x)
```

And then run it with <kbd>Shift</kbd>+<kbd>Return</kbd> to be sure that it works as a code cell.
Now go back to the cell and use <kbd>Esc</kbd> then <kbd>m</kbd> to switch the cell to Markdown
and "run" it with <kbd>Shift</kbd>+<kbd>Return</kbd>.
Що трапилося і як це може бути корисно?

:::::::::::::::::::: Рішення

## Розв'язок

Код Python розглядається як текст Markdown.
Лінії з’являються так, ніби вони є частиною одного спітнілого пункту.
Це може бути корисно для тимчасово ввімкнення і відключення клітин у зошитах, які використовуються для декількох цілей.

```python
x = 6 * 7 + 12 print(x)
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Рівняння

Standard Markdown (such as we're using for these notes) won't render equations,
but the Notebook will.
Створіть нову комірку Markdown
і введіть наступне:

```
$\sum_{i=1}^{N} 2^{-i} \approx 1$
```

(Напевно, легше скопіювати та вставити.)
Що це відображає?
Що ти думаєш про підкреслювання, `_`, кружка, `^` і доларовий знак, `$`, далі?

:::::::::::::::::::: Рішення

## Розв'язок

У блокноті показано рівняння з синтаксисом рівняння LaTeX.
Знак долара, "$" використовується для того, щоб повідомити Markdown про те, що текст між ним є рівняння LaTeX.
Якщо ви не знайомі з LaTeX, підкреслення, `_`, використовується для підрядкових індексів та обілфлексу, `^`, використовується для верхніх індексів.
Пара фігурних дужок, `{` і`}`, використовується для групування тексту разом, щоб оператор `i=1` став підрядковим і `N` стає верхнім індексом.
Аналогічно, `-i` перебуває у фігурних дужках, щоб зробити весь вираз верхнього індексу для `2`.
`\sum` і `\approx` є командами LaTeX для символу "sum over" та "approximate".

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

## Закриття JupyterLab

- В меню виберіть меню "Файл", а потім виберіть "Закрити вниз" в нижньому меню. Вам буде запропоновано підтвердити, що ви хочете завершити сервер JupyterLab (не забудьте зберегти свою роботу!). Натисніть кнопку "Shut Down", щоб завершити сервер JupyterLab каналів.
- Для того, щоб перезапустити сервер JupyterLab вам потрібно буде перезапустити наступну команду з оболонки.

```
$ jupyter lab
```

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Закриття JupyterLab

Тренуйся закрити та перезапустити сервер JupyterLab (JupyterLab користувачів).

::::::::::::::::::::::::::::::::::::::::::::::::::

[jupyterlab]: https://jupyterlab.readthedocs.io/en/stable/

[jupyterlab-ui]: https://jupyterlab.readthedocs.io/en/stable/user/interface.html

[jupyterlab-notebook-docs]: https://jupyterlab.readthedocs.io/en/stable/user/notebook.html

[markdown]: https://uk.wikipedia.org/wiki/Markdown

[data_carpentry]: https://datacarpentry.org

:::::::::::::::::::::::::::::::::::::::: keypoints

- Python скрипти - це звичайні текстові файли.
- За допомогою блокнота Jupyter для редагування і запуску Python.
- У блокноті є команди і режими редагування.
- Скористайтеся клавіатурою та мишкою, щоб вибрати та відредагувати клітини.
- Блокнот перетворить Markdown на надруковану документацію красивого.
- Markdown робить більшість з HTML коду.

::::::::::::::::::::::::::::::::::::::::::::::::::
