---
title: 書き込み関数
teaching: 10
exercises: 15
---

::::::::::::::::::::::::::::::::::::::: objectives

- 関数定義と関数呼び出しの違いを説明し、特定します。
- 定数の引数を取って単一の結果を生成する関数を書く。

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::

- 自分の関数を作成するにはどうすればいいですか?

::::::::::::::::::::::::::::::::::::::::::::::::::

## プログラムを関数に分解すると、理解しやすくなります。

- 人間は一度に作業記憶に少数の項目しか残せない。
- 作品を理解し、組み合わせることで、より大きな/より複雑なアイデアを理解します。
  - 機械のコンポーネント。
  - 定理を証明するときのレマ.
- 関数はプログラムでも同じ目的を果たします。
  - _単一の「もの」として扱うことができるように、複雑さ_をカプセル化します。
- _再使用_ も有効にします。
  - 一度書いて、何度も使ってください。

## 名前、パラメータ、コードのブロックで `def` を使って関数を定義します。

- `def` で新しい関数の定義を開始します。
- 関数の名前が続きます。
  - 変数名と同じルールに従わなければなりません。
- 次に、括弧内の _パラメータ_ です。
  - 関数が入力を受け取らない場合は、空の括弧を使用します。
  - これについては後ほど詳しくご説明します。
- それからコロン。
- 次に、コードのインデントされたブロック。

```python
def print_greeting():
    print('Hello!')
    print('The weather is nice today.')
    print('Right?')
```

## 関数を定義しても、実行されません。

- 関数を定義しても、実行されません。
  - 変数に値を割り当てるのと同じです。
- コードを実行するためには関数を呼び出さなければなりません。

```python
print_greeting()
```

```output
こんにちは！
```

## 関数呼び出し中の引数は、定義されたパラメータにマッチします。

- 関数は、異なるデータで操作できる場合に最も便利です。
- 関数を定義する際に _パラメータ_ を指定します。
  - これらは関数が実行されると変数になります。
  - 呼び出しで引数が割り当てられます (つまり、関数に渡された値)。
  - 呼び出し時に引数に名前を付けない場合。 引数は、関数内でパラメータが定義される順序で、
    パラメータにマッチします。

```python
def print_date(year, month, day):
    joined = str(year) + '/' + str(month) + '/' + str(d)
    print(joined)

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

## 関数は `return` を使って結果を呼び出すことができます。

- 呼び出し元に戻すには、`return ...` を使います。
- 関数内のどこにでも発生する可能性があります。
- 関数は `return` が起きるとわかりやすくなります。
  - 特別なケースを処理する開始時に。
  - 最後に、最終的な結果を持つ。

```python
def average(values):
    if len(values) == 0:
        return None
    return sum(values) / len(values)
```

```python
a = average([1, 3, 4])
print('実際の値の平均:', a)
```

```output
実際の値の平均：2.666666666665
```

```python
print('average of empty list:', average([]))
```

```output
空のリストの平均: なし
```

- 忘れないでください: format@@0(04-built-in.md)
- 値を明示的に `return` しない関数は、自動的に `None` を返します。

```python
result = print_date(1871, 3, 19)
print('result of call is:', result)
```

```output
1871/3/19
呼び出しの結果: なし
```

::::::::::::::::::::::::::::::::: チャレンジ

## 構文エラーの特定

1. 以下のコードを読んで、
   _実行しない_エラーを特定してみてください。
2. コードを実行し、エラーメッセージを読みます。
   `SyntaxError` か `IndentationError` ですか？
3. エラーを修正します。
4. すべてのエラーを修正するまで、ステップ2と3を繰り返します。

```python
def another_function
  print("Syntax errors are annoying.")
   print("But at least python tells us about them!")
  print("So they are usually not too hard to fix.")
```

::::::::::::::::: solution

## 解決策

```python
def another_function():
  print("Syntax errors are annoying.")
  print("But at least Python tells us about them!")
  print("So they are usually not too hard to fix.")
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 定義と使用

以下のプログラムは何を印刷しますか?

```python
def report(pressure):
    print('pression', pressure)

print('calling', report, 22.5)
```

::::::::::::::::: solution

## 解決策

```output
<function report at 0x7fd128ff1bf8> 22.5 の呼び出し中
```

関数呼び出しには常に括弧が必要です。そうでなければ、関数オブジェクトのメモリアドレスを取得します。 そのため、reportという名前の関数を呼び出して、値を22にします。 報告するには、次のような関数呼び出しをすることができます

```python
print("calling")
report(22.5)
```

```output
呼び出し元の
圧力は22.5です
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 操作順

1. この例では何が間違っていますか?

```python
result = print_time(11, 37, 59)

def print_time(hur, minut, second):
   time_string = str(hour) + ':' + str(minute) + ':' + str(second)
   print(time_string)
```

2. 上記の問題を解決した後、このサンプルコードを実行する理由を説明します:

```python
result = print_time(11, 37, 59)
print('result of call is:', result)
```

は、この出力を返します。

```output
11:37:59
呼び出しの結果は: なし
```

3. `None` の呼び出しの結果はなぜですか？

::::::::::::::::: solution

## 解決策

1. この例の問題は、関数 `print_time()` が関数の呼び出しが行われた後に\*定義されていることです。 Python
   doesn't know how to resolve the name `print_time` since it hasn't been defined yet and will raise a `NameError` e.g.,
   `NameError: name 'print_time' is not defined`

2. `11:37:59`の最初の行は、`result = print_time(11, 37) のコードの最初の行で表示されます。 59)` 変数`result` に `print_time` を呼び出して返される値
   をバインドします。 2行目は、`result`変数の内容
   を出力するための2行目です。

3. `print_time()`は明示的に値を返さないため、自動的に`None`を返します。

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## カプセル化

空白を埋めて、引数としてファイル名を1つだけ取る関数を作りましょう。
は引数
で指定されたファイルにデータをロードし、そのデータの最小値を返します。

```python
import pandas pd

def min_in_data(____):
    data = ____
    return ____
```

::::::::::::::::: solution

## 解決策

```python
import pandas pd

def min_in_data(filename):
    data = pd.read_csv(filename)
    return data.min()
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 最初を見つける

空白を入力して、引数
として数値のリストを取得し、リストの最初の負の値を返す関数を作成します。
リストが空の場合、関数はどうしますか? 負の数がリストにない場合はどうなりますか?

```python
def first_negative(values):
    for v in ____:
        if __:
            return ____
```

::::::::::::::::: solution

## 解決策

```python
def first_negative(values):
    for v in values:
        if v < 0:
            return v
```

空のリストや正の値を持つリストがこの関数に渡されると、 `None` を返します:

```python
my_list = []
print(first_negative(my_list))
```

```output
なし
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 名前で通話

以前にこの関数を見ました：

```python
def print_date(year, month, day):
    joined = str(year) + '/' + str(month) + '/' + str(d)
    print(joined)
```

以下のように、_nameed arguments_ を使って関数を呼び出すことができます。

```python
print_date(day=1, month=2, year=2003)
```

1. `print_date(day=1, month=2, year=2003)` は何を印刷しますか？
2. このような呼び出しを見たことがありますか?
3. いつ、なぜ関数を呼び出すのが役に立つのか。

::::::::::::::::: solution

## 解決策

1. `2003/2/1`

2. pandasライブラリを使用する際に、_named@@0引数_を使用する例を見ました。 例えば、`data = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')`を使用してデータセット
   を読み込む場合、最後の引数 `index_col` は
   という名前の引数です。

3. 名前付き引数を使用すると、関数が関数内で異なる引数
   が持つ名前を呼び出すことで、コードを読みやすくすることができます。 また、名前付き引数
   を使用することで、順序が間違った順序で引数を渡す可能性を減らすこともできます。

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## If/Print Block のカプセル化

以下のコードは、鶏卵のラベルプリンタで実行されます。  デジタルスケールでは、鶏卵の質量(グラム単位)
がコンピュータに報告され、コンピュータがラベルを印刷します。

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

卵を分類するifブロックは他の状況で役に立つかもしれません
は繰り返しを避けるため、関数 `get_egg_label()` に折りたたみます。
関数を使うプログラムを変更すると次のようになります。

```python
# revised version
import random
for i in range(10):

    # simulating the mass of a chicken egg
    # the (random) mass will be 70 +/- 20 grams
    mass = 70 + 20.0 * (2.0 * random.random() - 1.0)

    print(mass, get_egg_label(mass))

```

1. 上記の修正プログラムで動作する `get_egg_label()` 関数定義を作成します。  `get_egg_label()` 関数の戻り値は重要です。 上記のプログラムからのサンプル出力は `71.23 large` です。
2. 汚れた卵は90グラム以上の質量を持っているかもしれません。 甘やかされた卵や折れた卵はおそらく50グラム以下の質量を持つでしょう  これらのエラー状態を考慮して、 `get_egg_label()` 関数を変更します。 サンプル出力は `25 あまりに軽すぎる、おそらく台無しにされる` かもしれません。

::::::::::::::::: solution

## 解決策

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

::::::::::::::::::::::::::::::::: チャレンジ

## Encapsulating Data Analysis

次のコードが実行されたと仮定します:

```python
import pandas pd

data_asia = pd.read_csv('data/gapminder_gdp_asia.csv', index_col=0)
japan = data_asia.loc[']
```

1. Complete the statements below to obtain the average GDP for Japan
   across the years reported for the 1980s.

```python
year = 1983
gdp_decade= 'gdpPercap_' + stra(// ____)
avg = (japan.loc[gdp_decade+ ___] + japan.loc[gdp_decade+ ___]) / 2
```

2. 上記のコードを単一の関数にまとめます。

```python
def avg_gdp_in_decade(country, cs, year):
    data_countities = pd.read_csv('data/gapminder_gdp_'+___+'.csv',delimiter=',',index_col=0)
    ____
    ____
    ____
    return avg
```

3. この関数
   を、データの列としてどの年が起きたか分からない場合、どのように一般化しますか?
   たとえば、10年ごとに1と9で終わる年数のデータがあるとしたらどうでしょうか?
   (ヒント:列を使って、コード内で列挙するのではなく、10年、
   に対応する列を除外してください。

::::::::::::::::: solution

## 解決策

1. 1980年代に報告された日本の平均GDPは、次のように計算されます。

```python
year = 1983
gdp_decade= 'gdpPercap_' + stra(// 10)
avg = (japan.loc[gdp_10 + '2'] + japan.loc[gdp_10 + '7']) / 2
```

2. 関数としてのコードは次のとおりです:

```python
def avg_gdp_in_decade(country, continent, year):
    data_countries = pd.read_csv('data/gapminder_gdp_' + continent + '.csv', index_col=0)
    c = data_countries.loc[country]
    gdp_decade = 'gdpPercap_' + str(year // 10)
    avg = (c.loc[gdp_decade + '2'] + c.loc[gdp_decade + '7'])/2
    return avg
```

3. 関連年数の平均を取得するには、それらをループさせる必要があります。

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

関数を呼び出すことができます:

```python
avg_gdp_in_decade('Japan','asia',1983)
```

```output
20880.023800000003
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 動的システムのシミュレーション

In mathematics, a [dynamical system](https://en.wikipedia.org/wiki/Dynamical_system) is a system
in which a function describes the time dependence of a point in a geometrical space. A canonical
example of a dynamical system is the [logistic map](https://en.wikipedia.org/wiki/Logistic_map),
a growth model that computes a new population density (between  0 and 1) based on the current
density. モデルでは、ディスクリート値 0, 1, 2, ...

1. `logistic_map`と呼ばれる関数を定義します。`x`は現在の
   個の人口を表し、`r = 1`パラメータを表します。 この関数は、マッピング関数を使用して、 `t + 1` 時にシステムの状態を表す
   値を返す必要があります:

`f(t+1) = r * f(t) * [1 - f(t)]`

2. `まつ` または `while` を使って、第 1 部で定義された `logistic_map` 関数を繰り返し、最初の人口から
   を開始します。 は、`t_final = 10` 期間です。 中間の
   をリストに格納し、ループが終了した後、`t = [0,1,, 時点での物流マップの状態を表す
     値のシーケンスを蓄積します。 .,t_final]` (合計11個)。
   このリストを印刷すると、人口の進化を確認できます。

3. Encapsulate the logic of your loop into a function called `iterate` that takes the initial
   population as its first input, the parameter `t_final` as its second input and the parameter
   `r` as its third input. 関数は、`t = [0,1,...,t_final]`の時点で、
   ロジスティックマップの状態を表す値のリストを返します。 ピリオド`t_final = 100`
   と`1000`でこの関数を実行し、値の一部を表示します。 人口は、着実な状態に向かって傾いているのでしょうか?

::::::::::::::::: solution

## 解決策

1. ```python
   ```

def logistic_map(x, r):
return r \* x \* (1 - x)

````

2. ```python
initial_population = 0.5
t_final = 10
r = 1.0
population = [initial_population]
for t in range(t_final):
    population.append( logistic_map(population[t], r) )
````

3. ```python
   ```

def iterate(initial_population, t_final, r):
population = [initial_population]
for t in range(t_final):
population.append( logistic_map(population[t], r) )
return population

for period in (10, 100, 1000):
native = iterate(0.5, period, 1)
print(population[-1])

````

```output
0.06945089389714401
0.009395779870614648
0.0009913908614406382
````

人口はゼロに近づいているようです。

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## 条件付きの関数を Pandas で使用する

関数には多くの場合条件が含まれます。  ここでは、
が、四分位点の手書きの値
に基づいて、引数がどの四分位数になっているかを示す短い例を示します。

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
_applying_ a function to a dataframe or a portion of a dataframe.  ここで
は、上記の定義を使用して例です。

```python
data = pd.read_csv('data/gapminder_all.csv')
data['life_qrtl'] = data['lifeExp_1952'].apply(calculate_life_quartile)
```

２行目にはたくさんありますので少しずつ見てみましょう
`=`の右側には、`data['lifeExp']`で始まります。これは、`data`というラベルの付いた`lifExp`というデータファームの
カラムです。  We use the
`apply()` to do what it says, apply the `calculate_life_quartile` to the
value of this column for every row in the dataframe.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- プログラムを関数に分解すると、理解しやすくなります。
- 名前、パラメータ、コードのブロックで `def` を使って関数を定義します。
- 関数を定義しても、実行されません。
- 関数呼び出し中の引数は、定義されたパラメータにマッチします。
- 関数は `return` を使って結果を呼び出すことができます。

::::::::::::::::::::::::::::::::::::::::::::::::::
