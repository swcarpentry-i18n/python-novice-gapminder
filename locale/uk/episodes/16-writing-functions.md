---
title: Написання функції
teaching: 10
exercises: 15
---

::::::::::::::::::::::::::::::::::::::: objectives

- Поясни різницю між визначенням функції та викликом функції.
- Напишіть функцію, яка бере невеличку фіксовану кількість аргументів і видає єдиний результат.

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::: питань

- Як я можу створити свої власні функції?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Розбийте програми в функції, щоб полегшити їх розуміння.

- Люди можуть зберігати тільки кілька елементів в оперативній пам'яті.
- Розуміння більших/більш складних ідей шляхом розуміння та об'єднання частин.
  - Компоненти в машині.
  - Ненависть підтверджує теорії.
- Функції виконують той самий сенс у програмах.
  - _Підложено_ складність, щоб ми могли розглядати її як одну "річ".
- Також дозволяє _повторне використання_.
  - Напишіть один раз, використовуйте багато разів.

## Визначте функцію, що використовує `def` з назвою, параметрами та блоком коду.

- Почніть визначення нової функції з `def`.
- Підписаний назвою функції.
  - Повинен слухатися тих самих правил, що і назви змінних.
- Тоді _параметри_ в дужках.
  - Порожні дужки, якщо функція не приймає жодного входу.
  - Зараз ми обговоримо це докладно.
- Ось кішка.
- Потім вкладений блок коду.

```python
def print_greeting():
    print('Привіт!')
    print('Погода сьогодні гарна.')
    print('Right?')
```

## Визначення функції не запускає його.

- Визначення функції не запускає його.
  - Наприклад, присвоєння значення змінній.
- Треба викликати функцію, щоб виконати код, який вона містить.

```python
print_greeting()
```

```output
Доброго дня!
```

## Аргументи виклику функції відповідають його певним параметрам.

- Функції найбільш корисні, якщо вони можуть працювати з різними даними.
- Вкажіть _параметри_ при визначенні функції.
  - Ці змінні стають після виконання функції.
  - Присвоюється аргументи виклику (тобто значення, передані функції).
  - Якщо ви не називаєте аргументи при виклику, аргументи будуть відповідати значенню
    параметрів в порядку визначені в функції.

```python
def print_date(рік, місяць):
    joined = str(рік) + '/' + str(місяць) + '/' + str(день)
    (друковано)

print_date(1871, 3, 19)
```

```output
1871/3/19
```

Or, we can name the arguments when we call the function, which allows us to
specify them in any order and adds clarity to the call site; otherwise as
one is reading the code they might forget if the second argument is the month
or the day for example.

```python
print_date(month=3, day=19, year=1871)
```

```output
1871/3/19
```

- Via [Twitter](https://twitter.com/minisciencegirl/status/693486088963272705):
  `()` contains the ingredients for the function
  while the body contains the recipe.

## Функції можуть повернути результат виклику за допомогою `return`.

- Використайте `return ...`, щоб повернути значення зворотному абоненту.
- Може трапитися будь-де в функції.
- Але функції легше розуміти, якщо відбудеться `return`:
  - Спочатку працювати зі спеціальними випадками.
  - Наприкінці кінцевого результату.

```python
def average(значень):
    якщо len(values) == 0:
        повертати немає
    сума (значень) / len(values)
```

```python
a = average([1, 3, 4])
print('середні фактичні значення: ', a)
```

```output
в середньому фактичних значень: 2.66666666666665
```

```python
print('середній список порожній:', average([]))
```

```output
середнє пустий список: немає
```

- Запам'ятайте: [кожна функція повертає щось](04-built-in.md).
- Функція, яка в явному випадку не повертає значення "Немає".

```python
результат = print_date(1871, 3, 19)
print('результат виклику: ', результат)
```

```output
Результат дзвінка 1871/3/19
немає
```

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Визначення синтаксичних помилок

1. Read the code below and try to identify what the errors are
   _without_ running it.
2. Запустіть код та прочитайте повідомлення про помилку.
   Це 'Синтаксист' або "Помилка відступи\`?
3. Виправ помилку.
4. Повторюйте кроки 2 і 3, поки не виправите всі помилки.

```python
def another_function
  print("Syntax errors are annoying.")
   print("But at least python tells us about them!")
  print("So they are usually not too hard to fix.")
```

:::::::::::::::::::: Рішення

## Розв'язок

```python
def another_function():
  друкувати ("Синтаксичні помилки дратують. )
  print("Але принаймні Python розказує нам про це!")
  print("Отже вони зазвичай не занадто складні для виправлення.")
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Визначення та використання

Що робить друк наступної програми?

```python
звіт def (тиск):
    print('pressure is', pressure)

print('calling', report, 22.5)
```

:::::::::::::::::::: Рішення

## Розв'язок

```output
виклик <function report at 0x7fd128ff1bf8> 22.5
```

Функція виклику завжди потребує круглі дужки, інакше ви отримаєте адресу пам'яті об'єкта функції. Отже, якщо ми хочемо викликати функцію, що називається звіт, і надати їй значення 22. щоб повідомити про на, ми можемо зробити виклик функції наступним чином

```python
print("calling")
report(22.5)
```

```output
виклик
тиску 22.5
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Порядок операцій

1. Що не так в цьому прикладі?

```python
результат = print_time(11, 37, 59)

def print_time(hour, minute, second):
   time_string = str(hour) + ':' + str(minute) + ':' + str(second)
   print(time_string)
```

2. Після виправлення проблеми вище, пояснить, чому виконується цей приклад:

```python
результат = print_time(11, 37, 59)
print('результат виклику: ', результат)
```

дає цей вивід:

```output
11:37:59
результат виклику: None
```

3. Чому викликано виклик "Ні"?

:::::::::::::::::::: Рішення

## Розв'язок

1. Проблема з прикладом в тому, що функція `print_time()` визначена _after_ виклик у функції. Python
   не знає, як вирішити ім'я `print_time` оскільки воно ще не визначено і запустить `NameError` e. .,
   `NameError: name 'print_time' не визначено`

2. Перший рядок виводу `11:37:59` надрукований за першим рядком коду, `result = print_time(11, 37, 59)`, який прив'язує значення
   , повернувшись, викликавши `print_time` до змінної `result`. Другий рядок розташований від другого друкованого виклику до друку виведення вмісту
   змінної `result`.

3. `print_time()` точно не повертає значення, так що воно автоматично повертає `Немає`.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Інкапсуляція

Заповніть пропуски, щоб створити функцію, яка бере єдине ім'я файлу в якості аргументу,
завантажує дані у файл з назвою аргумент,
і повертає мінімальне значення в цих даних.

```python
імпорт pandas як pd

def min_in_data(__):
    дані = ____
    повернення ____
```

:::::::::::::::::::: Рішення

## Розв'язок

```python
імпорт pandas як pd

def min_in_data(filename):
    дані = pd.read_csv(filename)
    повертає data.min()
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Знайти перше

Заповніть пропуски, щоб створити функцію, яка приймає список чисел у вигляді аргументу
і повертає перше від'ємне значення в списку.
Що робить функція, якщо список пустий? Що робити, якщо список не має від'ємних чисел?

```python
def first_negative(values):
    for v in ____:
        if ____:
            return ____
```

:::::::::::::::::::: Рішення

## Розв'язок

```python
def first_negative(значень):
    для v у значеннях:
        якщо v < 0:
            повертати v
```

Якщо передано порожній список або список з усіма додатними значеннями цієї функції, функція повертає `Немає`:

```python
my_list = []
print(first_negative(my_list))
```

```output
Без ефекту
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Виклик за іменем

Раніше ми побачили цю функцію:

```python
def print_date(рік, місяць):
    joined = str(рік) + '/' + str(місяць) + '/' + str(день)

```

Ми побачили, що можна викликати функцію за допомогою \*званих аргументів \*, як тут:

```python
print_date(day=1, місяць=2, рік=2003)
```

1. Що таке `print_date(day=1, month=2, year=2003)` друк?
2. Коли ти бачив виклик функції на зразок цього раніше?
3. Коли і чому це корисно називати функції таким чином?

:::::::::::::::::::: Рішення

## Розв'язок

1. `2003/2/1`

2. Ми бачили приклади використання _названих аргументів_ під час роботи з бібліотекою пандас. Наприклад, під час читання в
   використання `data = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')`, останній аргумент `index_col` є аргументом
   з назвою аргументу.

3. Using named arguments can make code more readable since one can see from the function call what name the different arguments
   have inside the function. Він також може знизити шанси на передавання аргументів у неправильному порядку, оскільки використання іменованих аргументів
   замовлення не має значення.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Інкапсуляція If/Print блоку

Для курячого яйця, наведений нижче на принтері мітки.  A digital scale will report a chicken egg mass (in grams)
to the computer and then the computer will print a label.

```python
import random
for i in range(10):

    # simulating the mass of a chicken egg
    # the (random) mass will be 70 +/- 20 grams
    mass = 70 + 20.0 * (2.0 * random.random() - 1.0)

    print(mass)

    # egg sizing machinery prints a label
    if mass >= 85:
        print("jumbo")
    elif mass >= 70:
        print("large")
    elif mass < 70 and mass >= 55:
        print("medium")
    else:
        print("small")
```

The if-block that classifies the eggs might be useful in other situations,
so to avoid repeating it, we could fold it into a function, `get_egg_label()`.
Перегляд програми використання функції дасть нам це:

```python
# revised version
import random
for i in range(10):

    # simulating the mass of a chicken egg
    # the (random) mass will be 70 +/- 20 grams
    mass = 70 + 20.0 * (2.0 * random.random() - 1.0)

    print(mass, get_egg_label(mass))

```

1. Створіть визначення функції для `get_egg_label()`, яка буде працювати з зміненою програмою вище.  Зверніть увагу, що функція `get_egg_label()` може бути важливою. Зразок виводу вище програми буде `71.23 великий`.
2. Брудні яйця можуть мати масу більше ніж 90 грам, і зіпсоване або зламане яйце може мати масу, яка становить менше 50 грам.  Змініть функцію `get_egg_label()` для обліку цих умов помилки. Зразок виводу може бути \`25 занадто світла, ймовірно, зіпсованим.

:::::::::::::::::::: Рішення

## Розв'язок

```python
def get_egg_label(mass):
    # egg sizing machinery prints a label
    egg_label = "Unlabelled"
    if mass >= 90:
        egg_label = "warning: egg might be dirty"
    elif mass >= 85:
        egg_label = "jumbo"
    elif mass >= 70:
        egg_label = "large"
    elif mass < 70 and mass >= 55:
        egg_label = "medium"
    elif mass < 50:
        egg_label = "too light, probably spoiled"
    else:
        egg_label = "small"
    return egg_label
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Аналіз обробки даних

Припустимо, що був виконаний наступний код:

```python
імпорт pandas як pd

data_asia = pd.read_csv('data/gapminder_gdp_asia.csv', index_col=0)
japan = data_asia.loc['Японія']
```

1. Завершіть заяви нижче, щоб отримати середній ВВП для Японії
   протягом наступних років, повідомлених за 1980-ті роки.

```python
year = 1983
gdp_decade = 'gdpPercap_' + str(рік ____)
avg = (japan.loc[gdp_decade + ___] + japan.loc[gdp_decade + ___]) / 2
```

2. Абстрактувати код, що наведений вище в одній функції.

```python
def avg_gdp_in_decade(country, continent, year):
    data_countries = pd.read_csv('data/gapminder_gdp_'+___+'.csv',delimiter=',',index_col=0)
    ____
    ____
    ____
    return avg
```

3. How would you generalize this function
   if you did not know beforehand which specific years occurred as columns in the data?
   Наприклад, що якщо ми також мали дані від закінчення в 1 та 9 років протягом кожного десятиліття?
   (Підказка: використовуйте стовпці для відбору тих з даних, які відповідають десятиліттям,
   замість того, щоб перерахувати їх в коді.)

:::::::::::::::::::: Рішення

## Розв'язок

1. Середній ВВП для Японії протягом багатьох років, про який повідомлялося 1980-х років, обчислений так:

```python
year = 1983
gdp_decade = 'gdpPercap_' + str(рік // 10)
avg = (japan.loc[gdp_decade + '2'] + japan.loc[gdp_decade + '7']) / 2
```

2. Цей код як функція:

```python
def avg_gdp_in_in_decade(country, континент, рік):
    data_country = pd.read_csv('data/gapminder_gdp_' + continent + '.csv', index_col=0)
    = data_countries. oc[country]
    gdp_decade = 'gdpPercap_' + str(рік // 10)
    avg = (c. oc[gdp_decade + '2'] + c.loc[gdp_decade + '7'])/2
    повернути avg
```

3. Щоб отримати середній показник за відповідні роки, нам потрібно розібратись над цим:

```python
def avg_gdp_in_decade(country, continent, year):
    data_countries = pd.read_csv('data/gapminder_gdp_' + continent + '.csv', index_col=0)
    c = data_countries.loc[country]
    gdp_decade = 'gdpPercap_' + str(year // 10)
    total = 0.0
    num_years = 0
    for yr_header in c.index: # c's index contains reported years
        if yr_header.startswith(gdp_decade):
            total = total + c.loc[yr_header]
            num_years = num_years + 1
    return total/num_years
```

Ця функція тепер може викликатися так:

```python
avg_gdp_in_in_decade('Япон','asia',1983)
```

```output
20880.023800000003
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::: виклик

## Симуляція динамічної системи

In mathematics, a [dynamical system](https://en.wikipedia.org/wiki/Dynamical_system) is a system
in which a function describes the time dependence of a point in a geometrical space. Канонічна
приклад динамічної системи - це [логістична карта](https\://en.wikipedia. rg/wiki/Logistic_map),
модель зростання, яка обчислює нову щільність населення (з 0 до 1) на основі поточної
щільності. В моделі, час займає дискретні значення 0, 1, 2, ...

1. Визначте функцію, яка називається `logistic_map`, яка приймає два вхідних значення: `x`, представляючи поточне
   населення (вчасно `t`), а параметр `r = 1`. This function should return a value
   representing the state of the system (population) at time `t + 1`, using the mapping function:

`f(t+1) = r * f(t) * [1 - f(t)]`

2. Using a `for` or `while` loop, iterate the `logistic_map` function defined in part 1, starting
   from an initial population of 0.5, for a period of time `t_final = 10`. Store the intermediate
   results in a list so that after the loop terminates you have accumulated a sequence of values
   representing the state of the logistic map at times `t = [0,1,...,t_final]` (11 values in total).
   Надрукуйте цей список, щоб побачити еволюцію населення.

3. Перетворити логіку вашого циклу у функцію, яка називається `iterate`, яка приймає початкове значення
   популяція як першого входу, параметр `t_final` як другий вхід та параметр
   `r` є третім видом. Функція повинна повернути список значень, що представляють стан
   логістична карта інколи `t = [0,1,...,t_final]`. Виконай цю функцію для періодів `t_final = 100`
   і `1000` і надрукуй деякі значення. Чи населення йде до стабільної держави?

:::::::::::::::::::: Рішення

## Розв'язок

1. ```python
   ```

def logistic_map(x, r):
повертати r \* x \* (1 - x)

````

2. ```python
initial_population = 0.5
t_final = 10
r = 1.
population = [initial_population]
для t в діапазоні (t_final):
    популяція.append( logistic_map(population[t], r)
````

3. ```python
   ```

def iterate(initial_population, t_final, r):
population = [initial_population]
for t в range(t_final):
population.append( logistic_map(population[t], r)
повертається населення

for period in (10, 100, 1000):
population = iterate(0.5, period, 1)
print(population[-1])

````

```вивід
0.06945089389714401
0.009395779870614614648
0.0009913908614406382
````

Здається, популяція наближається до нуля.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## Використання функцій з умовами у Пандасі

Функції часто містять умови.  Here is a short example that
will indicate which quartile the argument is in based on hand-coded values
for the quartile cut points.

```python
def calculate_life_quartile(exp):
    if exp < 58.41:
        # This observation is in the first quartile
        return 1
    elif exp >= 58.41 and exp < 67.05:
        # This observation is in the second quartile
       return 2
    elif exp >= 67.05 and exp < 71.70:
        # This observation is in the third quartile
       return 3
    elif exp >= 71.70:
        # This observation is in the fourth quartile
       return 4
    else:
        # This observation has bad data
       return None

calculate_life_quartile(62.5)
```

```output
2
```

That function would typically be used within a `for` loop, but Pandas has
a different, more efficient way of doing the same thing, and that is by
_applying_ a function to a dataframe or a portion of a dataframe.  Here
is an example, using the definition above.

```python
data = pd.read_csv('data/gapminder_all.csv')
data['life_qrtl'] = data['lifeExp_1952'].apply(calculate_life_quartile)
```

В цій другій прямій, давайте візьмемо її за частиною.
У правій частині `=` ми починаємо з `data['lifeExp']`, що є символом
в датарії під назвою `data` позначений `lifExp`.  Ми використовуємо
`apply()` для того, щоб виконати те, що він говорить, застосовує значення "calculate_life_quartile" до
для кожного рядка дата.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Розбийте програми в функції, щоб полегшити їх розуміння.
- Визначте функцію, що використовує `def` з назвою, параметрами та блоком коду.
- Визначення функції не запускає його.
- Аргументи виклику функції відповідають його певним параметрам.
- Функції можуть повернути результат виклику за допомогою `return`.

::::::::::::::::::::::::::::::::::::::::::::::::::
