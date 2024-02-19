---
title: データ型と型変換
teaching: 10
exercises: 10
---

::::::::::::::::::::::::::::::::::

- 整数と浮動小数点数のキー差を説明します。
- 数字と文字列のキー差を説明します。
- 整数、浮動小数点数、文字列を変換するには、組み込み関数を使用します。

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::

- プログラムはどのようなデータを保存しますか?
- ある型を別の型に変換するにはどうすればよいですか?

::::::::::::::::::::::::::::::::::::::::::::::::::

## すべての値には型があります。

- プログラムのすべての値には、特定の型があります。
- 整数(`int`): 3 や -512 のような正または負の整数を表します。
- 浮動小数点数 (`float`): 3.14159や-2.5のような実数を表します。
- 文字列(通常は "string", `str`):テキスト。
  - (一致する限り) シングルクォートまたはダブルクォートのいずれかで書かれています。
  - 文字列を表示すると、引用符は印刷されません。

## 組み込み関数 `type` を使用して、値の型を見つけます。

- 組み込み関数 `type` を使って、値の型を調べましょう。
- 変数でも動作します。
  - しかし、覚えておいてください: _value_ は --- _variable_ という型を持っています。

```python
print(type(52))
```

```output
<class 'int'>
```

```python
fitness = 'average'
print(type(fitness))
```

```output
<class 'str'>
```

## 型は、与えられた値に対してどの操作(またはメソッド)を実行できるかを制御します。

- 値の型はプログラムに何ができるかを決定します。

```python
print(5 - 3)
```

```output
2
```

```python
print('hello' - 'h')
```

```error
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-2-67f5626a1e07> in <module>()
----> 1 print('hello' - 'h')

TypeError: unsupported operand type(s) for -: 'str' and 'str'
```

## 文字列に "+" と "\*" 演算子を使用できます。

- "Adding" 文字列を連結します。

```python
full_name = 'Ahmed' + ' ' + 'Walsh'
print(full_name)
```

```output
Ahmed Walsh
```

- 整数_N_で文字列を掛けると、その文字列が繰り返された _N_ 回からなる新しい文字列が生成されます。
  - 乗算が繰り返されるため、乗算が繰り返されます。

```python
separator = '=' * 10
print(separator)
```

```output
==========
```

## 文字列には長さがあります(数字はありません)。

- 組み込み関数 `len` は文字列内の文字数をカウントします。

```python
print(len(full_name))
```

```output
11
```

- しかし、数字には長さがありません(ゼロでさえありません)。

```python
print(len(52))
```

```error
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-3-f769e8e8097d> in <module>()
----> 1 print(len(52))

TypeError: object of type 'int' has no len()
```

## 数値を文字列に、またはその逆に変換する必要があります。 {#convert-numbers-and-strings}

- 数字と文字列を追加できません。

```python
print(1 + '2')
```

```error
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-4-fe4f54a023c6> in <module>()
----> 1 print(1 + '2')

TypeError: unsupported operand type(s) for +: 'int' and 'str'
```

- 曖昧さがあるため許可されていません: `1 + '2'` は `3` か `12` でなければなりませんか？
- 型名を関数として使用することで、型を他の型に変換することができます。

```python
print(1 + int('2'))
print(str(1) + '2')
```

```output
3
12
```

## 整数と浮動小数点を自由に組み合わせることができます。

- 整数と浮動小数点数は算術式で混在させることができます。
  - Python 3 は必要に応じて整数を浮動小数点数に自動的に変換します。

```python
print('half is', 1 / 2.0)
print('three squared is', 3.0 ** 2)
```

```output
半分は 0.5
三乗は 9.0
```

## 変数は、何かがそれらに割り当てられたときにのみ値を変更します。

- If we make one cell in a spreadsheet depend on another,
  and update the latter,
  the former updates automatically.
- これはプログラミング言語で **起こりません**。

```python
variable_one = 1
variable_two = 5 * variable_one
variable_one = 2
print('first is', variable_one, 'and second is', variable_two)
```

```output
1つ目は2つ目と2つ目は5です
```

- は新しい値を生成し、それを `variable_one` に代入します。
- 後 `variable_two`の値は新しい値に設定され、\*variable_one`に依存しないので、変数
    は`variable_one\`が変更されたときに自動的に変化しません。

::::::::::::::::::::::::::::::::: チャレンジ

## 分数

3.4とはどのような値ですか?
どうやって見つけることができますか?

::::::::::::::::: solution

## 解決策

これは浮動小数点数です(しばしば「float」と略されます)。
組み込み関数 `type()` を使うことで見つけることができます。

```python
print(type(3.4))
```

```output
<class 'float'>
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 自動型変換

3.25 + 4の値はどのようなタイプですか?

::::::::::::::::: solution

## 解決策

整数は、必要に応じて自動的にフロートに変換されます。

```python
result = 3.25 + 4
print(result, 'is', type(result))
```

```output
7.25 is <class 'float'>
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## タイプを選択

値(整数、浮動小数点数、文字列)の種類
は、以下のそれぞれを表すために使用しますか?  各問題について複数の良い答えを考え出してみてください。  例えば、# 1 では、浮動小数点変数で日数を数えると、整数を使うよりも意味があります。

1. 年の開始からの日数。
2. 年の初めから今までの日数の経過時間。
3. ラボ機器のシリアル番号。
4. 研究所の標本の年齢
5. 都市の現在の人口。
6. 時間の経過とともに都市の平均人口。

::::::::::::::::: solution

## 解決策

質問に対する答えは次のとおりです。

1. 整数は、日数が1から365の間にあるので。

2. 浮動小数点以下の日数が必要です

3. シリアル番号が文字と数字を含む場合の文字列。それ以外の場合は、シリアル番号が数字のみである場合の整数。

4. これは異なります! 標本の年齢はどのように定義しますか? コレクションから丸一日(整数)? 日付と時刻(弦)は?

5. 個体単位で人口を表すための大きな集計(例えば百万円)、または整数として人口を表すために浮動小数点を選択してください。

6. 浮動小数点数は、平均が小数部を持つ可能性があるためです。

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 分割タイプ

Python 3 では、`//` 演算子は整数(全体番号)のフロア除算を実行します。`/` 演算子は浮動小数点
除算を実行します。 そして、 `%` (または _modulo_) 演算子は、整数の除算から余りを計算して返します。

```python
print('5 // 3:', 5 // 3)
print('5 / 3:', 5 / 3)
print('5 % 3:', 5 % 3)
```

```output
5 // 3: 1
5 / 3: 1.6666666667
5 % 3: 2
```

If `num_subjects` is the number of subjects taking part in a study,
and `num_per_survey` is the number that can take part in a single survey,
write an expression that calculates the number of surveys needed
to reach everyone once.

::::::::::::::::: solution

## 解決策

We want the minimum number of surveys that reaches everyone once, which is
the rounded up value of `num_subjects/ num_per_survey`.
は床の除算を`//`で行い、1を足すのと同じです。
の前に、
を扱う対象の数から 1 を引く必要があります。この場合、`num_subjects` は `num_per_survey` で均等に割り当てられます。

```python
num_subjects = 600
num_per_survey = 42
num_surveys = (num_subjects - 1) // num_per_survey + 1

print(num_subjects, 'subjects,', num_per_survey, 'per survey:', num_surveys)
```

```output
600件の被験者、42件の被験者:15
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 文字列から数字へ

合理的な場合、`float()`は文字列を浮動小数点数に変換します。
と`int()`は浮動小数点数を整数に変換します。

```python
print("string to float:", float("3.4"))
print("float to int:", int(3.4))
```

```output
string to float: 3.4
float to int: 3
```

しかし、変換が意味をなさない場合は、エラーメッセージが発生します。

```python
print("string to float:", float("Hello world!))
```

```error
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
<ipython-input-5-df3b790bf0a2> in <module>
----> 1 print("string to float:", float("Hello world!"))

ValueError: could not convert string to float: 'Hello world!'
```

この情報を考えると、次のプログラムがどうなると思いますか?

実際に何をするのか？

なぜそうすると思いますか？

```python
print("fracional string to int:", int("3.4"))
```

::::::::::::::::: solution

## 解決策

このプログラムで何ができると思いますか？ Python 3 の `int` コマンドを
に変換するのはそれほど不合理ではありません。 " から 3.4 へ、そして 3 への追加型変換。 結局のところ、Python 3は他の多くの
マジックを実行します。それはその魅力の一部ではありませんか？

```python
int("3.4")
```

```output
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
<ipython-input-2-ec6729dfccdc> in <module>
----> 1 int("3.4")
ValueError: invalid literal for int() with base 10: '3.4'
```

しかし、Python 3 はエラーを投げます。 なぜでしょう？ 一貫性を持つために、おそらく。 2つ連続した
型キャストを実行するようPythonに求める場合は、コード内で明示的に変換する必要があります。

```python
int(float("3.4"))
```

```output
3
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 異なる種類の算術演算を行う

浮動小数点数`2.0`を返すのは、次のうちどれですか？
注意: 正解が複数ある場合があります。

```python
first = 1.0
second = "1"
third = "1.1"
```

1. `first + float(second)`
2. `float(second) + float(third)`
3. `first + int(third)`
4. `first + int(float(third))`
5. `int(first) + int(float(third))`
6. `2.0 * second`

::::::::::::::::: solution

## 解決策

答え: 1 と 4

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 複素番号

Pythonには複雑な数字
が用意されており、これは`1.0+2.0j`として記述されています。
`val`が複雑な数字の場合、
実数と虚数の部分は`val.real`と`val.imag`として_dot notation_
を使用してアクセスできます。

```python
a_complex_number = 6 + 2j
print(a_complex_number.real)
print(a_complex_number.imag)
```

```output
6.0
2.0
```

1. なぜPythonは架空の部分に`i`の代わりに`j`を使用していると思いますか？
2. `1 + 2j + 3` の生産量は？
3. `4j`は何を期待しますか？  `4 j`または`4 + j`については？

::::::::::::::::: solution

## 解決策

1. 標準的な数学治療では、通常、虚数を表すために `i` を使用します。 しかし、メディアからの報告では、
   は電気工学から設立された初期の大会であり、今や技術的に高価な領域を
   変化にもたらします。 Stack Overflow は追加の説明と
   discussion.

2. `(4+2j)`

3. `4j` と `Syntax Error: invalid syntax` 後者の場合、`j`は変数と見なされ、
   文は`j`が定義されているかどうかに依存します。

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- すべての値には型があります。
- 組み込み関数 `type` を使用して、値の型を見つけます。
- 型は、値に対して行うことができる操作を制御します。
- 文字列を追加し、掛けることができます。
- 文字列には長さがあります(数字はありません)。
- 数値を文字列に、またはその逆に変換する必要があります。
- 整数と浮動小数点を自由に組み合わせることができます。
- 変数は、何かがそれらに割り当てられたときにのみ値を変更します。

::::::::::::::::::::::::::::::::::::::::::::::::::
