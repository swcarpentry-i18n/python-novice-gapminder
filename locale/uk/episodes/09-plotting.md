---
title: Плотка
teaching: 15
exercises: 15
---

::::::::::::::::::::::::::::::::::::::: objectives

- Створити часовий графік з окремим набором даних.
- Створити графік розсіювання, що показує відношення між двома наборами даних.

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: питань

- Як я можу побудувати свої дані?
- Як я можу зберегти свою діаграму для публікації?

::::::::::::::::::::::::::::::::::::::::::::::::::

## [`matplotlib`](https://matplotlib.org/) є найбільш поширеною науковою бібліотекою в Python.

- Зазвичай використовувати підбібліотеку під назвою [`matplotlib.pyplot`](https://matplotlib.org/stable/tutorials/introductory/pyplot.html).
- Jupyter Notebook за замовчуванням надасть plot інлайновано.

```python
імпорт матриці для matplotlib.pyplot
```

- Прості діаграми тоді (справедливо) прості в створенні.

```python
time = [0, 1, 2, 3]
позиція = [0, 100, 200, 300]

plt.plot(time, position)
plt.xlabel('Час (hr)')
plt.ylabel('Position (км)')
```

![](fig/9_simple_position_time_plot.svg){alt='Simple Position-Time lot'}

:::::::::::::::::::::::::::::::::::::::::  callout

## Відображати всі відкриті фігури

У нашому прикладі Jupyter Notebook він працює в клітині, яка генерує цифру безпосередньо під кодом.
Фігура також включена у блокнот для майбутнього перегляду документів.
Проте, інші середовища Python, такі як інтерактивна сесія Python, що починаються з терміналу
або Python скрипт, виконаний за допомогою командного рядка, потребують додаткової команди для відображення фігури.

Поструктуруйте "matplotlib", щоб показати фігуру:

```python
plt.show()
```

Цю команду також можна використовувати в блокноті - наприклад, для відображення декількох цифр
якщо кілька створюються однією клітиною.

::::::::::::::::::::::::::::::::::::::::::::::::::

## Збудуйте дані безпосередньо з [`Pandas datжа`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html).

- Ми можемо також накреслити [Pandas datжами](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.html).
- Перед plotting, ми перетворюємо колонкові заголовки з `string` в тип даних `integer`, оскільки вони представляють числові значення,
  використовуючи [str.replace()](https\://pandas.pydata.org/docs/reference/api/pandas.Series.str.replace. tml), щоб видалити `gpdPercap_`
  префікс і потім [astype(int)](https\://pandas.pydata.org/docs/reference/api/pandas.Series.astype. tml)
  щоб перетворити ряд значень рядка (`['1952', '1957', ...'2007']`) в ряд цілих чисел: `[1925, 1957, ..., 2007]`.

```python
імпорт pandas як pd

дані = pd.read_csv('data/gapminder_gdp_oceania. sv', index_col='country')

# Вилучити рік з останніх 4 символів кожної назви стовпця
# Назви колонок структуровані як 'gdpPercap_(рік)', 
# отже ми хочемо зберегти (річну) частину лише для ясності при побудові ВВП проти . років
# Для цього ми використовуємо заміну (), який видаляє з рядка символи, зазначені в аргументі
# Цей метод працює над рядками, тому ми використовуємо replace() з Pandas Series. tr vectorized рядкові функції

years = дані. olumns.str.replace('gdpPercap_', '')

# Конвертувати річні значення в цілі числа, зберігаючи результати назад до datрозкладок

data.columns = years.astype(int)

data.loc['Австралія'].plot()
```

![](fig/9_gdp_australia.svg){alt='ВВП для Австралії'}

## Виділіть та трансформуйте дані, а потім намалюйте їх.

- За замовчуванням, [`DataFrame.plot`](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.plot.html#pandas.DataFraFrame.plot) складається з рядків як вісь X.
- Ми можемо переносити дані, щоб зробити кілька серій.

```python
data.T.plot()
plt.ylabel('ВВП на одиницю')
```

![](fig/9_gdp_australia_nz.svg){alt='ВВП ділянка для Австралії і Нової Зеландії '}

## Доступно багато стилів графіків.

- Наприклад, стовпчикова діаграма використовуючи більш вишуканий стиль.

```python
plt.style.use('ggplot')
data.T.plot(kind='bar')
plt.ylabel('ВВП на капітал)
```

![](fig/9_gdp_bar.svg){alt='ВВП барграфік для Австралії'}

## Дані також можуть бути відображені шляхом виклику функції "matplotlib" напряму.

- Ця команда є `plt.plot(x, y)`
- Колір та формат маркерів також можна вказати як додатковий необов'язковий аргумент. ., `b-` - це синя лінія, `g--` - це зелена пунктирна лінія.

## Отримайте дані Австралії з графіка

```python
years = data.columns
gdp_australia = data.loc['Австралія']

plt.plot(років, gdp_australia, 'g--')
```

![](fig/9_gdp_australia_formatted.svg){alt='ВВП відформатований графік для Австралії'}

## Можна побудувати велику кількість наборів даних разом.

```python
# Оберіть дві країни, вартістю даних.
gdp_australia = data.loc['Австралія']
gdp_nz = data.loc['New Zealand']

# Діаграма з різнокольоровими маркерами.
плюс. lot(років, gdp_australia, 'b-', label='Австраліa')
plt.plot(роки, gdp_nz, 'g-', label='New Zealand')

# Створити легенду.
plt.legend(loc='upper left')
plt.xlabel('Year')
plt.ylabel('ВВП на душу населення ($)')
```

:::::::::::::::::::::::::::::::::::::::::  callout

## Додавання легенди

Often when plotting multiple datasets on the same figure it is desirable to have
a legend describing the data.

Це можна зробити в `matplotlib` на двох етапах:

- Вкажіть мітку для кожного набору даних у фігурі:

```python
plt.plot(роки, gdp_australia, label='Австралія')
plt.plot(роки, gdp_nz, label='Новий Зеландія')
```

- З'єднайте "matplotlib", щоб створити легенду.

```python
plt.legend()
```

За замовчуванням matplotlib спробує розмістити легенду в відповідній позиції. If you
would rather specify a position this can be done with the `loc=` argument, e.g to place
the legend in the upper left corner of the plot, specify `loc='upper left'`

::::::::::::::::::::::::::::::::::::::::::::::::::

![](fig/9_gdp_australia_nz_formatted.svg){alt='ВВП відформатований графік для Австралії і Нової Зеланди'}

- Збудуйте точний сюжет, що підтверджує ВВП Австралії та Нової Зеландії
- Використовуйте або `plt.scatter` або `DataFrame.plot.scatter`

```python
plt.scatter(gdp_australia, gdp_nz)
```

![](fig/9_gdp_correlation_plt.svg){alt='ВВП кореляція за допомогою plt.scatter'}

```python
data.T.plot.scatter(x = 'Австралія', y = 'Нова Зеландія')
```

![](fig/9_gdp_correlation_data.svg){alt='ВВП кореляція, використовуючи data.T.plot.scatter'}

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Мініма та Максима

Заповніть пропуски, наведені нижче, щоб побудувати мінімальний ВВП на душу населення з часом
для всіх країн Європи.
Змініть її, щоб побудувати максимальний ВВП на душу населення протягом часу для Європи.

```python
data_europe = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')
data_europe.__.plot(label='min')
data_europe.____
plt.legend(loc='best')
plt.xticks(rotation=90)
```

:::::::::::::::::::: Рішення

## Розв'язок

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

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Коронні відносини

Modify the example in the notes to create a scatter plot showing
the relationship between the minimum and maximum GDP per capita
among the countries in Asia for each year in the data set.
Які стосунки ви бачите (якщо такі є)?

:::::::::::::::::::: Рішення

## Розв'язок

```python
data_asia = pd.read_csv('data/gapminder_gdp_asia.csv', index_col='country')
data_asia.describe().T.plot(kind='scatter', x='min', y='max')
```

![](fig/9_correlations_solution1.svg){alt='Correlations Solution 1'}

Жодного конкретного корелятора не можна побачити між значеннями мінімального та максимального gdp
року в рік. Здається, статки арабських країн не піднімаються і не падають разом.

:::::::::::::::::::::::::

You might note that the variability in the maximum is much higher than
that of the minimum.  Перегляньте максимум і макс. індексів:

```python
data_asia = pd.read_csv('data/gapminder_gdp_asia.csv', index_col='country')
data_asia.max().plot()
print(data_asia.idxmax())
print(data_asia.idxmin())
```

:::::::::::::::::::: Рішення

## Розв'язок

![](fig/9_correlations_solution2.png){alt='Correlations Solution 2'}

Схоже, мінливість цього значення через різке падіння після 1972 року.
Можливо, деякі геополітики грають? Given the dominance of oil producing countries,
maybe the Brent crude index would make an interesting comparison?
Незважаючи на те, що М'янма має найнижчий gdp, найвищу країну gdb було вирізнокольоровано
більш помітно.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Більше кореляції

This short program creates a plot showing
the correlation between GDP and life expectancy for 2007,
normalizing marker size by population:

```python
data_all = pd.read_csv('data/gapminder_all.csv', index_col='country')
data_all.plot(kind='scatter', x='gdpPercap_2007', y='lifeExp_2007',
              s=data_all['pop_2007']/1e6)
```

Використання онлайн-довідки та інших ресурсів,
пояснювати, що має робити кожен аргумент.

:::::::::::::::::::: Рішення

## Розв'язок

![](fig/9_more_correlations_solution.svg){alt='More Correlations Solution'}

Гарне місце для пошуку є документацією до функції графіків -
help(data_all.plot).

тип - як видно, це вже визначає спосіб малювання.

x and y - ім'я стовпця або індекс, який визначає, які дані будуть розміщені
на осі x і y з графіку

s - Подробиці цього можна знайти в документації plt.scatter.
Одинарне число або одне значення для кожної точки. Визначає розмір
відмічених точок.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## Збереження вашої діаграми в файл

If you are satisfied with the plot you see you may want to save it to a file,
perhaps to include it in a publication. There is a function in the
matplotlib.pyplot module that accomplishes this:
[savefig](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.savefig.html).
Виклик цієї функції, наприклад з

```python
plt.savefig('my_figure.png')
```

зберігатиме поточну картинку у файлі `my_figure.png`. Формат файлу
буде автоматично замінено на розширення назви файлу (інші формати* pdf, ps, eps і svg).

Зверніть увагу, що функції у «plt» посилаються на глобальну змінну
і після визначення, яка була відображена на екрані (e. . з `plt.show`)
matplotlib зробить цю змінну наведеною на нову порожню фігуру.
Therefore, make sure you call `plt.savefig` before the plot is displayed to
the screen, otherwise you may find a file with an empty plot.

При використанні датафри, дані часто генеруються і відмічаються на екрані в одній прямій.
На додаток до використання `plt.savefig`, ми можемо зберегти посилання на поточну цифру
в локальній змінній (з `plt. cf`) і викличте "savefig\` метод з
з цієї змінної, щоб зберегти малюнок у файл.

```python
data.plot(kind='bar')
fig = plt.gcf() # отримати поточну цифру
fig.savefig('my_figure.png')
```

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## Доступ до ваших ділянок

Коли кожен раз, коли ви породжуєте сюжети в папір або презентацію, Є кілька речей, які ви можете зробити, щоб переконатися, що кожен може зрозуміти ваші сюжети.

- Завжди переконайтесь, що ваш текст досить великий для читання. Використай параметр `fontsize` у `xlabel`, `ylabel`, `title`, and `legend`, and [`tick_params` з `labelsize`](https://matplotlib.org/stable/api/_as_gen/matplotlib.axes.tick_params.html) для збільшення розміру тексту чисел для ваших осань.
- Аналогічно, ви повинні зробити елементи вашого графіку простими для видимого вигляду. Використовуйте `s` для збільшення розміру маркерів розсіяного графіку і "лінійних", щоб збільшити розміри ліній вашого графіку.
- Використання кольору (і нічого іншого) для розрізнення різних елементів графіків зробить вашу ділянку нечитабельною для кожного, хто є кольоровим сліпим, або у кого чорно-білий офісний принтер. Для рядків параметр "linestyle" можна використовувати різні типи рядків. Для розсіювання «маркера» дозволяє змінювати форму балів. Якщо ви не впевнені у своїх кольорах, ви можете використовувати [Coblis](https\://www\.color-blindness. om/coblis-color-blindness-simulator/) або [Color Oracle](https://colororacle.org/), щоб імітувати ваші ділянки схожі на них з кольоровою сліпотою.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- [`matplotlib`](https://matplotlib.org/) є найбільш поширеною науковою бібліотекою в Python.
- Будуйте різноманітні дані безпосередньо з назви пандаса.
- Виділіть та трансформуйте дані, а потім намалюйте їх.
- Доступно багато стилів: подивіться [Python Graph Gallery](https://python-graph-gallery.com/matplotlib/) для отримання додаткових опцій.
- Можна побудувати велику кількість наборів даних разом.

::::::::::::::::::::::::::::::::::::::::::::::::::
