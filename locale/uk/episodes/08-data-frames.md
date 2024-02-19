---
title: Pandas DataFrames
teaching: 15
exercises: 15
---

::::::::::::::::::::::::::::::::::::::: objectives

- Вибір індивідуальних значень з діапазону «Пандас».
- Обрати цілі рядки або цілі колонки з головоломки.
- Виберіть підмножину рядків і стовпців з діаграми в одній операції.
- Виберіть підмножину дати інформацію по одному логічному критерію.

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: питань

- Як я можу зробити статистичний аналіз табличних даних?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Примітка про дані Pandas DataFrames/серії

A [DataFrame][pandas-dataframe] is a collection of [Series][pandas-series];
The DataFrame is the way Pandas represents a table, and Series is the data-structure
Pandas use to represent a column.

Pandas is built on top of the [Numpy][numpy] library, which in practice means that
most of the methods defined for Numpy Arrays apply to Pandas Series/DataFrames.

Завдяки чому Pandas такий привабливий - це потужний інтерфейс для доступу до окремих записів
таблиці, належне поводження з відсутніми значеннями та операціями в відносинах даних
між DataFrames.

## Вибір значень

To access a value at the position `[i,j]` of a DataFrame, we have two options, depending on
what is the meaning of `i` in use.
Remember that a DataFrame provides an _index_ as a way to identify the rows of the table;
a row, then, has a _position_ inside the table as well as a _label_, which
uniquely identifies its _entry_ in the DataFrame.

## Використовуйте `DataFrame.iloc[..., ...]` для вибору значень за їх позицією

- Можна вказати місце за числовим індексом аналогічно 2D версії вибору символів у рядках.

```python
імпорт pandas як pd
дані = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')
print(data.iloc[0, 0])
```

```output
1601.056136
```

## Використовуйте `DataFrame.loc[..., ...]` щоб вибрати значення за їх міткою.

- Можна вказати розташування по рядку та/або імені стовпця.

```python
print(data.loc["Албанія", "gdpPercap_1952"])
```

```output
1601.056136
```

## Використовуйте `:` самостійно, щоб означати всі стовпці або всі рядки.

- Так само, як звичайне позначення Python'а.

```python
print(data.loc["Албанія", :])
```

```output
gdpPercap_1952 1601.056136
gdpPercap_1957 1942.284244
gdpPercap_1962 2312.888958
gdpPercap_1967 2760. 96931
gdpPercap_1972 3313.422188
gdpcap_1977 3533.003910
gdpPercap_1982 30. 80722
gdpPercap_1987 3738.932735
gdpPercap_1992 2497.437901
gdpPercap_1997 3193. 54604
gdpPercap_2002 4604.211737
gdpPercap_2007 5937.029526
Ім'я: Албанія, тип: float64
```

- отримаєте той самий результат, який надрукує `data.loc["Албанія"]` (без другого індексу).

```python
print(data.loc[:, "gdpPercap_1952"])
```

```output
country
Albania                    1601.056136
Austria                    6137.076492
Belgium                    8343.105127
⋮ ⋮ ⋮
Switzerland               14734.232750
Turkey                     1969.100980
United Kingdom             9979.508487
Name: gdpPercap_1952, dtype: float64
```

- Буде отриманий той самий результат, який надрукує `data["gdpPercap_1952"]`
- Також отримати той самий результат, який виводить `data.gdpPercap_1952` (не рекомендується, оскільки легко плутати з `.` нотацією для методів)

## Оберіть декілька стовпців або рядків, використовуючи `DataFrame.loc` і з назвою slice.

```python
print(data.loc['Italy':'Poland', 'gdpPercap_1962':'gdpPercap_1972'])
```

```output
             gdpPercap_1962  gdpPercap_1967  gdpPercap_1972
country
Italy           8243.582340    10022.401310    12269.273780
Montenegro      4649.593785     5907.850937     7778.414017
Netherlands    12790.849560    15363.251360    18794.745670
Norway         13450.401510    16361.876470    18965.055510
Poland          5338.752143     6557.152776     8006.506993
```

In the above code, we discover that **slicing using `loc` is inclusive at both
ends**, which differs from **slicing using `iloc`**, where slicing indicates
everything up to but not including the final index.

## Результат розтягування можна використати в подальших операціях.

- Зазвичай не просто друкувати фрагмент.
- All the statistical operators that work on entire dataframes
  work the same way on slices.
- Наприклад, розрахуємо максимум фрагменту.

```python
print(data.loc['Italy':'Poland', 'gdpPercap_1962':'gdpPercap_1972'].max())
```

```output
gdpPercap_1962 13450.40151
gdpPercap_1967 16361.87647
gpPercap_1972 18965.05551
dtype: float64
```

```python
print(data.loc['Italy':'Poland', 'gdpPercap_1962':'gdpPercap_1972'].min())
```

```output
gdpPercap_1962 4649.593785
gdpPercap_1967 5907.850937
gdpPercap_1972 7778.414017
dtype: float64
```

## Для вибору даних на основі їх значень.

- Порівняння має застосований елемент за елементом.
- Повертає аналогічно сформовану інформацію про `True` і "False".

```python
# Use a subset of data to keep output readable.
subset = data.loc['Italy':'Poland', 'gdpPercap_1962':'gdpPercap_1972']
print('Subset of data:\n', subset)

# Which values were greater than 10000 ?
print('\nWhere are values large?\n', subset > 10000)
```

```output
Subset of data:
             gdpPercap_1962  gdpPercap_1967  gdpPercap_1972
country
Italy           8243.582340    10022.401310    12269.273780
Montenegro      4649.593785     5907.850937     7778.414017
Netherlands    12790.849560    15363.251360    18794.745670
Norway         13450.401510    16361.876470    18965.055510
Poland          5338.752143     6557.152776     8006.506993

Where are values large?
            gdpPercap_1962 gdpPercap_1967 gdpPercap_1972
country
Italy                False           True           True
Montenegro           False          False          False
Netherlands           True           True           True
Norway                True           True           True
Poland               False          False          False
```

## Виберіть значення або NaN за допомогою логічної маски.

- Каркас повного логічного типу, іноді називають _маскою-_ через те, як його можна використовувати.

```python
mask = subset > 10000
print(subset[mask])
```

```output
             gdpPercap_1962  gdpPercap_1967  gdpPercap_1972
country
Italy                   NaN     10022.40131     12269.27378
Montenegro              NaN             NaN             NaN
Netherlands     12790.84956     15363.25136     18794.74567
Norway          13450.40151     16361.87647     18965.05551
Poland                  NaN             NaN             NaN
```

- Отримайте значення, де маска вірна, і NaN (Not a Number), де вона хибна.
- Корисно тому, що NaNs ігноруються такими операціями, як max, min, середня тощо.

```python
print(subset[subset > 10000].describe())
```

```output
       gdpPercap_1962  gdpPercap_1967  gdpPercap_1972
count        2.000000        3.000000        3.000000
mean     13120.625535    13915.843047    16676.358320
std        466.373656     3408.589070     3817.597015
min      12790.849560    10022.401310    12269.273780
25%      12955.737547    12692.826335    15532.009725
50%      13120.625535    15363.251360    18794.745670
75%      13285.513523    15862.563915    18879.900590
max      13450.401510    16361.876470    18965.055510
```

## Групувати за: розгалуження apply-combine

::::::::::::::::::::::::::::::::::::: instructor
Learners often struggle here, many may not work with financial data and concepts so they
find the example concepts difficult to get their head around. Найбільша проблема
, хоча і є генерацією лінії заможності, цей крок повинен пройти через
:

- Воно використовує неявне перетворення між булевим та плаваючим значенням, які
  не було покрито в курсі.
- Вісь = 1 аргумент повинен бути чітко пояснений.
  :::::::::::::::::::::::::::::::::::::::::::::::::

Pandas vectorizing methods and grouping operations are features that provide users
much flexibility to analyse their data.

For instance, let's say we want to have a clearer view on how the European countries
split themselves according to their GDP.

1. We may have a glance by splitting the countries in two groups during the years surveyed,
   those who presented a GDP _higher_ than the European average and those with a _lower_ GDP.
2. We then estimate a _wealthy score_ based on the historical (from 1962 to 2007) values,
   where we account how many times a country has participated in the groups of _lower_ or _higher_ GDP

```python
mask_higher = дані > data.mean()
wealth_score = mask_higher.aggregate('sum', axis=1) / len(data.columns)
print(wealth_score)
```

```output
country
Albania                   0.000000
Austria                   1.000000
Belgium                   1.000000
Bosnia and Herzegovina    0.000000
Bulgaria                  0.000000
Croatia                   0.000000
Czech Republic            0.500000
Denmark                   1.000000
Finland                   1.000000
France                    1.000000
Germany                   1.000000
Greece                    0.333333
Hungary                   0.000000
Iceland                   1.000000
Ireland                   0.333333
Italy                     0.500000
Montenegro                0.000000
Netherlands               1.000000
Norway                    1.000000
Poland                    0.000000
Portugal                  0.000000
Romania                   0.000000
Serbia                    0.000000
Slovak Republic           0.000000
Slovenia                  0.333333
Spain                     0.333333
Sweden                    1.000000
Switzerland               1.000000
Turkey                    0.000000
United Kingdom            1.000000
dtype: float64
```

Нарешті, для кожної групи у таблиці «wealth_score», ми додаємо їх (фінансову) внесок
протягом років, проведених за допомогою ланцюгових методів:

```python
print(data.groupby(wealth_score).sum())
```

```output
          gdpPercap_1952  gdpPercap_1957  gdpPercap_1962  gdpPercap_1967  \
0.000000    36916.854200    46110.918793    56850.065437    71324.848786   
0.333333    16790.046878    20942.456800    25744.935321    33567.667670   
0.500000    11807.544405    14505.000150    18380.449470    21421.846200   
1.000000   104317.277560   127332.008735   149989.154201   178000.350040   

          gdpPercap_1972  gdpPercap_1977  gdpPercap_1982  gdpPercap_1987  \
0.000000    88569.346898   104459.358438   113553.768507   119649.599409   
0.333333    45277.839976    53860.456750    59679.634020    64436.912960   
0.500000    25377.727380    29056.145370    31914.712050    35517.678220   
1.000000   215162.343140   241143.412730   263388.781960   296825.131210   

          gdpPercap_1992  gdpPercap_1997  gdpPercap_2002  gdpPercap_2007  
0.000000    92380.047256   103772.937598   118590.929863   149577.357928  
0.333333    67918.093220    80876.051580   102086.795210   122803.729520  
0.500000    36310.666080    40723.538700    45564.308390    51403.028210  
1.000000   315238.235970   346930.926170   385109.939210   427850.333420
```

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Вибір індивідуальних значень

Assume Pandas було імпортовано в ваш блокнот
і дані ВВП Gapminder для Європи були завантажені:

```python
імпорт pandas як pd

data_europe = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')
```

Напишіть вираз, щоб знайти за показник ВВП Сербії в 2007 році.

:::::::::::::::::::: Рішення

## Розв'язок

Вибір можна зробити за допомогою міток для рядка "Сербія", а колонка "gdpPercap_2007"):

```python
print(data_europe.loc['Serbia', 'gdpPercap_2007'])
```

Вихід

```output
9786.534714
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Розширювач різання

1. Чи можуть дві інструкції видавати однаковий результат?
2. Виходячи з цього,
   яке правило керує тим, що включено (або немає) у числових строках та іменуються відрізки у Пандасі?

```python
print(data_europe.iloc[0:2, 0:2])
print(data_europe.loc['Албанія':'Бельгія', 'gdpPercap_1952':'gdpPercap_1962'])
```

:::::::::::::::::::: Рішення

## Розв'язок

Ні, вони не дають того ж результату! Результат першого твердження:

```output
        gdpPercap_1952 gdpPercap_1957
country                                
Албанія 1601.056136 1942.284
Австрія 6137.076492 8842.598030
```

Дає другу заяву:

```output
        gdpPercap_1952 gdpPercap_1957 gdpPercap_1962
country                                                
Албанія 1601.056136 1942.284242312.888958
Austria 6137.076492 8842.598030 10750.7211
Бельгія 8343.105127 9714.960623 10991.206760
```

Зрозуміло, що другий оператор виробляє додаткову колонку та додатковий рядок в порівнянні з першою заявкою.\
Який ми можемо намалювати? Ми бачимо, що напис з числовим шрифтом, 0:2, \* оміт \* кінцевий індекс (тобто. індекс 2)
в діапазоні вказаного вище,
під час іменованого фрагменту, 'gdpPercap_1952':'gdpPercap_1962', _включити_ кінцевий елемент.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Відновлення даних

Поясніть, що робить кожен рядок в цій короткій програмі:
що відбувається в "перший", "секунда" і т.д.?

```python
first = pd.read_csv('data/gapminder_all.csv', index_col='country')
second = first['continent'] == 'Americas']
третім = second.drop('Puerto Rico')
четвертий = третя.drop('contin('x1)
fourth.to_csv('result.csv')
```

:::::::::::::::::::: Рішення

## Розв'язок

Давайте пройдемо цей шматок коду по лінії.

```python
перший = pd.read_csv('data/gapminder_all.csv', index_col='country')
```

Ця лінія завантажує дані, що містять дані про ВВП з усіх країн у датафраму під назвою "
"першим". Параметр `index_col='country'` вказує, які колонки використовувати як
теги рядків у даті.

```python
second = перше['континент'] == 'Америка']
```

This line makes a selection: only those rows of `first` for which the 'continent' column matches
'Americas' are extracted. Зауважте, як булевий вираз у дужках,
\`first['continent'] == 'Америка'', використовується для вибору тільки тих рядків, де істинний вираз.
Спробуйте надрукувати цей вираз! Ви можете надрукувати свої індивідуальні елементи True/False?
(підказка: спочатку призначте вираз змінної)

```python
третє = second.drop('Пуерто-Рико')
```

Як підказує, ця лінія скидає рядок з "секунди", де етикетка "Пуерто-Рико".
, отримана Африка `третя. Має один рядок менше ніж оригінальна датагра `секунда\`.

```python
fourth = third.drop('континент', вісь = 1)
```

Знову ми застосовуємо функцію падіння, але в цьому випадку ми скидаємо не рядок, а цілий стовпець.
Для цього нам необхідно також вказати параметр \`axis' (ми хочемо видалити другий стовпець
який містить індекс 1).

```python
чет.to_csv('result.csv')
```

Останній крок - записати дані, над якими ми працюємо у csv файлі. Пандас спрощує
з функцією "to_csv()". Єдиний необхідний аргумент для функції - це ім'я файлу. Зверніть увагу, що
файл буде записаний в каталозі, з якого ви запустили Jupyter або Python сесію.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Вибір індексів

Пояснюйте простими термінами того, що `idxmin` та `idxmax` роблять у короткій програмі нижче.
Коли б ви використовували ці методи?

```python
data = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')
print(data.idxmin())
print(data.idxmax())
```

:::::::::::::::::::: Рішення

## Розв'язок

Для кожного стовпця в `data`, `idxmin` поверне значення індексу, відповідне щодо мінімуму кожного стовпця;
`idxmax` буде робити аналогічне для максимального значення кожного стовпця.

Ці функції можна використовувати кожен раз, коли ви хочете отримати індекс мінімального/максимального значення і не фактичне мінімальне/максимальне значення.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Тренуйтеся з виділеним

Припустимо, що Пандас імпортовано і дані ВВП Gapminder для Європи були завантажені.
Напишіть вираз, щоб вибрати кожен з них:

1. ВВП на душу населення для всіх країн 1982 року.
2. ВВП на душу населення для Данії протягом всіх років.
3. ВВП на душу населення для всіх країн протягом багатьох років \* після\* 1985 року.
4. ВВП на душу населення для кожної країни у 2007 році як кілька
   ВВП на душу населення для цієї країни в 1952 році.

:::::::::::::::::::: Рішення

## Розв'язок

1:

```python
data['gdpPercap_1982']
```

2:

```python
data.loc['Данія',:]
```

3:

```python
data.loc[:,'gdpPercap_1985':]
```

Пандас досить розумний, щоб розпізнати число в кінці позначки стовпця, і не дає вам помилки, хоча жодного стовпця з назвою `gdpPercap_1985` насправді не існує. Це корисно, якщо нові стовпці додаються в CSV файл пізніше.

4:

```python
data['gdpPercap_2007']/data['gdpPercap_1952']
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Багато шляхів доступу

Є щонайменше два способи доступу до значення або частини DataFram: за іменем чи індексом.
Тим не менш, є багато інших. Наприклад, можна отримати окрему колонку або рядки або як `DataFrame`
або "Series".

Пропонуйте різні способи виконання наступних операцій по DataFrame:

1. Доступ до однієї колонки
2. Доступ до одного рядка
3. Доступ до індивідуального елемента DataFrame
4. Доступ до декількох стовпців
5. Доступ до декількох рядків
6. Доступ до підмножини вказаних рядків і стовпців
7. Доступ до підмножини рядків і діапазонів стовпців

:::::::::::::::::::: Рішення

## Розв'язок

1\. Доступ до одного стовпчика:

```python
# за назвою
data["col_name"] # як серія
data[["col_name"]] # як DataFrame

# за назвою, використовуючи дані .loc
. .loc["col_name"] # як серія
data.T.loc[["col_name"]].T # як DataFrame

# Нотація (Series)
даних. ol_name

# за індексом (iloc)
data.iloc[:, col_index] # як серія
даних. loc[:, [col_index]] # як DataFrame

# використовуючи маску
дані.T[data.T.index == "col_name"].T
```

2\. Доступ до одного рядка:

```python
# за назвою .loc
data.loc["row_name"] # як дані серії
. oc[["row_name"]] # як DataFrame

# by name
data.T["row_name"] # як серія
data.T[["row_name"]]. # як DataFrame

# за індексом
data.iloc[row_index]   # в якості даних серії
. loc[[row_index]] # як DataFrame

# використовуючи mask
data[data.index == "row_name"]
```

3\. Доступ до елементу DataFrame :

```python
# by column/row names
data["column_name"]["row_name"]         # as a Series

data[["col_name"]].loc["row_name"]  # as a Series
data[["col_name"]].loc[["row_name"]]  # as a DataFrame

data.loc["row_name"]["col_name"]  # as a value
data.loc[["row_name"]]["col_name"]  # as a Series
data.loc[["row_name"]][["col_name"]]  # as a DataFrame

data.loc["row_name", "col_name"]  # as a value
data.loc[["row_name"], "col_name"]  # as a Series. Preserves index. Column name is moved to `.name`.
data.loc["row_name", ["col_name"]]  # as a Series. Index is moved to `.name.` Sets index to column name.
data.loc[["row_name"], ["col_name"]]  # as a DataFrame (preserves original index and column name)

# by column/row names: Dot notation
data.col_name.row_name

# by column/row indices
data.iloc[row_index, col_index] # as a value
data.iloc[[row_index], col_index] # as a Series. Preserves index. Column name is moved to `.name`
data.iloc[row_index, [col_index]] # as a Series. Index is moved to `.name.` Sets index to column name.
data.iloc[[row_index], [col_index]] # as a DataFrame (preserves original index and column name)

# column name + row index
data["col_name"][row_index]
data.col_name[row_index]
data["col_name"].iloc[row_index]

# column index + row name
data.iloc[:, [col_index]].loc["row_name"]  # as a Series
data.iloc[:, [col_index]].loc[["row_name"]]  # as a DataFrame

# using masks
data[data.index == "row_name"].T[data.T.index == "col_name"].T
```

4\. Доступ до кількох стовпців:

```python
# by name
data[["col1", "col2", "col3"]]
data.loc[:, ["col1", "col2", "col3"]]

# by index
data.iloc[:, [col1_index, col2_index, col3_index]]
```

5\. Доступ до декількох рядків

```python
# за назвою
data.loc[["row1", "row2", "row3"]]

# за індексом
data.iloc[[data.ilrow1_index, row2_index, row3_index]]
```

6\. Доступ до підмножини вказаних рядків і стовпців

```python
# за назвами
data.loc[["row1", "row2", "row3"], ["col1", "col2", "col3"]]

# за індексами
даних. loc[[row1_index, row2_index, row3_index], [col1_index, col2_index, col3_index]]

# імена стовпців + індекси рядків
data[["col1", "col3", "col3"]]. loc[[row1_index, row2_index, row3_index]]

# індекси рядків + імена рядків
data.iloc[col1_index, col2_index, col3_index]].loc[["row1", "row3"]]
```

7\. Доступ до підмножини рядків і діапазонів стовпців

```python
# за назвою
data.loc["row1":"row2", "col1":"col2"]

# за індексом
data.iloc[row1_index:row2_index, col1_index:col2_index]

# назви стовпців + відступи рядків
даних. oc[:, "col1_name":"col2_name"].iloc[row1_index:row2_index]

# індекси стовпців + назви рядків
data.iloc[:, col1_index:col2_index].loc["row1":"row2"]
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Пошук доступних методів використання функції `dir()`

Python включає функцію `dir()`, яка може бути використана для відображення всіх доступних методів (функцій), що вбудовані в об'єкт даних.  В епізоді 4 ми використали деякі методи з рядком. Але ми можемо побачити ще більше доступними за допомогою `dir()`:

```python
my_string = 'Привіт світ!' # створення текстового об'єкта 
dir(my_string)
```

Команда приходить:

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

Ви можете використовувати `help()` або <kbd>Shift</kbd>+<kbd>Tab</kbd> щоб отримати більше інформації про те, що роблять ці методи.

Assume Pandas імпортовано і дані ВВП Gapminder для Європи були завантажені як "дані".  Потім скористайтеся `dir()`
щоб знайти функцію, яка виводить середній ВВП на душу населення у всіх європейських країнах за рік ця інформація доступна.

:::::::::::::::::::: Рішення

## Розв'язок

Серед багатьох варіантів, `dir()` зараховує функцію "median()\` як можливість.  Таким чином,

```python
data.median()
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Інтерпретація

Poland's borders have been stable since 1945,
but changed several times in the years before then.
Як би ви впоралися з цим, якби створили таблицю ВВП на душу населення за Польщу
протягом усього ХХ століття?

::::::::::::::::::::::::::::::::::::::::::::::::::

[pandas-dataframe]: https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.html

[pandas-series]: https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.html

[numpy]: https://www.numpy.org/

:::::::::::::::::::::::::::::::::::::::: keypoints

- Використовуйте `DataFrame.iloc[..., ...]` щоб вибрати значення по всьому розташуванню.
- Використовуйте `:` самостійно, щоб означати всі стовпці або всі рядки.
- Оберіть декілька стовпців або рядків, використовуючи `DataFrame.loc` і з назвою slice.
- Результат розтягування можна використати в подальших операціях.
- Для вибору даних на основі їх значень.
- Виберіть значення або NaN за допомогою логічної маски.

::::::::::::::::::::::::::::::::::::::::::::::::::
