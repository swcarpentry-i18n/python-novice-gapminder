---
title: Зациклення над наборами даних
teaching: 5
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- Можна читати та записувати глобальні вирази що відповідають наборам файлів.
- Використовуйте glob для створення списків файлів.
- Записуйте цикли для виконання операцій з файлами з вказаними іменами списку.

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: питань

- Як я можу обробляти багато наборів даних за допомогою однієї команди?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Використовуйте цикл `for` для обробки файлів, у яких зазначений список їх імен.

- Ім'я файлу - символ рядка.
- Списки можуть містити рядки символів.

```python
імпорт під
для назви файлу в ['data/gapminder_gdp_africa.csv', 'data/gapminder_gdp_asia.csv']:
    data = pd.read_csv(filename, index_col='country')
    print(filename, data.min())
```

```output
data/gapminder_gdp_africa.csv gdpPercap_1952    298.846212
gdpPercap_1957    335.997115
gdpPercap_1962    355.203227
gdpPercap_1967    412.977514
⋮ ⋮ ⋮
gdpPercap_1997    312.188423
gdpPercap_2002    241.165877
gdpPercap_2007    277.551859
dtype: float64
data/gapminder_gdp_asia.csv gdpPercap_1952    331
gdpPercap_1957    350
gdpPercap_1962    388
gdpPercap_1967    349
⋮ ⋮ ⋮
gdpPercap_1997    415
gdpPercap_2002    611
gdpPercap_2007    944
dtype: float64
```

## Використовуйте [`glob.glob`](https://docs.python.org/3/library/glob.html#glob.glob) для пошуку наборів файлів, імена яких відповідають шаблону.

- В Unix, термін "globbing" означає "відповідність набору файлів з шаблоном".
- Найбільш поширені шаблони:
  - `*` означає "заповнити нуль або більше символів"
  - `?` означає "відповідає лише одному символу"
- Стандартна бібліотека Python містить модуль [`glob`](https://docs.python.org/3/library/glob.html) для забезпечення послідовності, відповідної функціональності
- Модуль [`glob`](https://docs.python.org/3/library/glob.html) містить функцію з назвою `glob` для відповідності шаблонам файлу
- Наприклад, `glob.glob.glob('*.txt')` відповідає всім файлам в поточній папці
  імена яких закінчуються `.txt`.
- Результат є (можливо порожнім) списком рядків символів.

```python
імпорт glob
print('all csv файли в каталозі даних:', glob.glob('data/*.csv'))
```

```output
all csv files in data directory: ['data/gapminder_all.csv', 'data/gapminder_gdp_africa.csv', \
'data/gapminder_gdp_americas.csv', 'data/gapminder_gdp_asia.csv', 'data/gapminder_gdp_europe.csv', \
'data/gapminder_gdp_oceania.csv']
```

```python
print('всі файли PDB:', glob.glob('*.pdb'))
```

```output
всі файли PDB: []
```

## Використовуйте `glob` and `for` для обробки пакетів файлів.

- Helps a lot if the files are named and stored systematically and consistently
  so that simple patterns will find the right data.

```python
для назви файлу в glob.glob('data/gapminder_*.csv'):
    data = pd.read_csv(filename)
    print(filename, data['gdpPercap_1952'].min())
```

```output
data/gapminder_all.csv 298.8462121
data/gapminder_gdp_africa.csv 298.8462121
data/gapminder_gdp_americas.csv 1397.717137
data/gapminder_gp_asia.csv 331.0
data/gapminder_dp_europe.csv 973.5331948
data/apminder_gapminder_dpana.csa.csv 39.59564
```

- Це включає всі дані, як і дані по області.
- Використовуйте більш конкретний шаблон в вправах для виключення цілого набору даних.
- Але зверніть увагу, що мінімум цілої числової множини є також мінімальним з одного з числових множин,
  , яка є гарною перевіркою щодо правильності.

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Детерміновані матчі

Який з цих файлів _не_ відповідає виразу `glob.glob('data/*as*.csv')`?

1. `data/gapminder_gdp_africa.csv`
2. `data/gapminder_gdp_americas.csv`
3. `data/gapminder_gdp_asia.csv`

:::::::::::::::::::: Рішення

## Розв'язок

1 не відповідає світовому світу.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Мінімальний розмір файлу

Змініть цю програму, щоб вона друкувала кількість записів в
у файлі, в якому є найменша кількість записів.

```python
імпорт glob
імпортувати панди як pd
fewest = ____
для назви файлу в glob.glob('data/*.v'):
    dathapame = pd. ___(filename)
    fewest = min(__, datAFame.shape[0])
print('Найменший файл', 'records')
```

Зверніть увагу, що метод [`DataFrame.shape()`][shape-method]
повертає кортеж з кількістю рядків і стовпців блоку даних.

:::::::::::::::::::: Рішення

## Розв'язок

```python
імпорт glob
імпортувати панди як pd
fewest = float('Inf')
для назви файлу в glob.glob('data/*.csv'):
    datame = pd. ead_csv(filename)
    fewest = min(fewest, datame.shape[0])
print('найменший файл має', мало, 'записів')
```

You might have chosen to initialize the `fewest` variable with a number greater than the numbers
you're dealing with, but that could lead to trouble if you reuse the code with bigger numbers.
Python дозволяє використати додатню нескінченність, яка буде працювати незалежно від розмірів ваших чисел.
What other special strings does the [`float` function][float-function] recognize?

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Порівняння даних

Напишіть програму, яка зчитує в регіональних даних набори
і розміщує середній ВВП на душу населення для кожного регіону з часом
в одному графіку.

:::::::::::::::::::: Рішення

## Розв'язок

This solution builds a useful legend by using the [string `split` method][split-method] to
extract the `region` from the path 'data/gapminder\_gdp\_a\_specific\_region.csv'.

```python
імпорт glob
імпорту панд в якості pd
імпорту matplotlib.pyplot у вигляді plt
fig, ax = plt.subplots(1,1)
для назви файлу в glob.glob('/datagapminder_gdp*. sv'):
    датарами = pd. ead_csv(ім'я)
    # екстракт <region> із імені файлу, очікується, що він буде у форматі 'data/gapminder_gdp_<region>.csv'.
    # ми розділимо рядок за допомогою методу поділу і `_` як нашого розділювача,
    # отримати останній рядок зі списку, який розділяє (`<region>. sv`), 
    # та потім видаліть `. розширення sv` з цього рядка.
    регіон = filename.split('_')[-1][:-4] 
    datSafari [4] . ean().plot(ax=ax, label=region)
plt.legend()
plt.show()
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## Діяльність із шляхами для файлів

Модуль [`pathlib`][pathlib-module] надає корисні абстракції для роботи файлами і шляхом як
повертаючи назву файлу без розширення файлу. This is very useful when looping over files and
directories. У прикладі нижче ми створюємо об'єкт "шлях" і оглядаємо його атрибути.

```python
from pathlib import шлях

p = Path("data/gapminder_gdp_africa.csv")
print(p.parent), print(p.stem), print(p.stem), print(p.suffix)
```

```output
дані
gapminder_gdp_AFica
.csv
```

**Hint:** It is possible to check all available attributes and methods on the `Path` object with the `dir()`
function!

::::::::::::::::::::::::::::::::::::::::::::::::::

[shape-method]: https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.shape.html

[float-function]: https://docs.python.org/3/library/functions.html#float

[split-method]: https://docs.python.org/3/library/stdtypes.html#str.split

[pathlib-module]: https://docs.python.org/3/library/pathlib.html

:::::::::::::::::::::::::::::::::::::::: keypoints

- Використовуйте цикл `for` для обробки файлів, у яких зазначений список їх імен.
- Використовуйте `glob.glob` для пошуку наборів файлів, імена яких відповідають шаблону.
- Використовуйте `glob` and `for` для обробки пакетів файлів.

::::::::::::::::::::::::::::::::::::::::::::::::::
