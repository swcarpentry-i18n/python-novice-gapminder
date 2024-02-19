---
title: 内蔵の関数とヘルプ
teaching: 15
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- 機能の目的を説明します。
- 組み込みの Python 関数を正しく呼び出します。
- 組み込み関数へのネストコールが正しく行われます。
- 組み込み関数のドキュメントを表示するにはヘルプを使用してください。
- SyntaxError と NameError が発生する状況を正しく記述します。

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::

- 組み込み関数はどのように使用できますか?
- どのように私は彼らが何をしているかを調べることができますか?
- プログラムではどのようなエラーが発生する可能性がありますか?

::::::::::::::::::::::::::::::::::::::::::::::::::

## プログラムにドキュメントを追加するには、コメントを使用します。

```python
# この文はPythonによって実行されません。
adjusting = 0.5 # どちらもこれではありません - '#' 以降の文は無視されます。
```

## 関数は0以上の引数を取ることができます。

- すでにいくつかの機能を見てきました。--- では詳しく見てみましょう。
- _argument_ は関数に渡される値です。
- `len`は正確に1つ必要です。
- `int`、`str`、`float`は、既存の値から新しい値を作成します。
- `print` は0かそれ以上かかります。
- 引数のない`print` は空白の行を表示します。
  - Must always use parentheses, even if they're empty,
    so that Python knows a function is being called.

```python
print('before')
print()
print('after')
```

```output


の前
```

## すべての関数は何かを返します。

- すべての関数呼び出しは何らかの結果を生成します。
- 関数に有用な結果が返されない場合、
  は通常、特殊な値 `None` を返します。 `None` は Python
  オブジェクトで、値がないときはいつでも立ちます。

```python
result = print('example')
print('result of print is', result)
```

```output
例
print の結果は None
```

## 一般的に使用される組み込み関数には、`max`、`min`、および`round`が含まれます。

- 1つ以上の値の最大値を見つけるには `max` を使います。
- 最小値を見つけるには、`min`を使います。
- どちらも文字列と数字で動作します。
  - "大きい"と"小さい"文字を比較する(0-9、A-Z、a-z)を使用します。

```python
print(max(1, 2, 3))
print(min('a', 'A', '0'))
```

```output
3
0 0
```

## 関数は特定の引数(組み合わせ)に対してのみ動作します。

- `max`と`min`は少なくとも1つの引数を与える必要があります。
  - 「空のセットの最大」は無意味な質問です。
- そして、彼らは意味を持って比較できるものを与えられなければなりません。

```python
print(max(1, 'a'))
```

```error
TypeError                                 Traceback (most recent call last)
<ipython-input-52-3f049acf3762> in <module>
----> 1 print(max(1, 'a'))

TypeError: '>' not supported between instances of 'str' and 'int'
```

## 関数はいくつかの引数にデフォルト値を持つことができます。

- `round` は浮動小数点数を丸めます。
- デフォルトでは、小数点以下の桁数をゼロに切り替えます。

```python
round(3.712)
```

```output
4
```

- 小数点以下の桁数を指定できます。

```python
round(3.712, 1)
```

```output
3.7
```

## オブジェクトに追加された関数はメソッドと呼ばれます。

- 機能は、パンダのエピソードに共通する別の形をとります。
- メソッドは、関数のように括弧を持っていますが、変数の後に続いていきます。
- いくつかのメソッドは内部Pythonの操作に使用され、二重の下線でマークされています。

```python
my_string = 'Hello world!'  # creation of a string object 

print(len(my_string))       # the len function takes a string as an argument and returns the length of the string

print(my_string.swapcase()) # calling the swapcase method on the my_string object

print(my_string.__len__())  # calling the internal __len__ method on the my_string object, used by len(my_string)

```

```output
12
hELLO WORLD!
12
```

- あなたは彼らが一緒に鎖でつながっているのを見るかもしれません。  彼らは左から右に動作します。

```python
print(my_string.isupper()) # すべての文字が大文字であるわけではありません。
print(my_string.upper()) # これはすべての大文字を大文字にします。

print(my_string.upper().isupper()) # これですべての大文字になります。
```

```output
False
HELLO WORLD
True
```

## 関数のヘルプを取得するには、組み込み関数 `help` を使用します。

- すべての組み込み関数にはオンラインドキュメントがあります。

```python
help(round)
```

```output
Help on built-in function round in module builtins:

round(number, ndigits=None)
    Round a number to a given precision in decimal digits.
    
    The return value is an integer if ndigits is omitted or None.  Otherwise
    the return value has the same type as the number.  ndigits may be negative.
```

## Jupyter Notebook には二つの方法があります。

- Option 1: セル
  (すなわち、関数名またはそのパラメータ)で関数が呼び出される場所の近くにカーソルを置きます。
  - <kbd></kbd>を押しながら、 <kbd>タブ</kbd> を押します。
  - 返された情報を拡大するためにこれを数回行う。
- オプション2:その後に疑問符が付いたセルに関数名を入力します。 次に、セルを実行します。

## Pythonはプログラムのソースを理解できない場合、構文エラーを報告します。

- 解析できない場合は、プログラムを実行しようとしません。

```python
# 文字列を囲む引用符を閉じるのを忘れた。
name = 'Feng
```

```error
  File "<ipython-input-56-f42768451d55>", line 2
    name = 'Feng
                ^
SyntaxError: EOL while scanning string literal
```

```python
# A extra '== ' in the assignment.
age = 52
```

```error
  File "<ipython-input-57-ccc3df3cf902>", line 2
    age = 52
          ^
SyntaxError: invalid syntax
```

- エラーメッセージをもっとよく見てください:

```python
print("hello world"
```

```error
  File "<ipython-input-6-d1cc229bf815>", line 1
    print ("hello world"
                        ^
SyntaxError: unexpected EOF while parsing
```

- このメッセージは、入力の最初の行(「行1」)に問題があることを示しています。
  - In this case the "ipython-input" section of the file name tells us that
    we are working with input into IPython,
    the Python interpreter used by the Jupyter Notebook.
- ファイル名の`-6-`部分は、
  ノートブックのセル6でエラーが発生したことを示します。
- 次に、
  `^` ポインタに問題があることを示します。

## プログラムの実行中に問題が発生した場合、Pythonはランタイムエラーを報告します。 {#runtime-error}

```python
age = 53
remaining = 100 - aege # mis-spelled 'age'
```

```error
NameError Traceback (most recent call last)
<ipython-input-59-1214fb6c55fc> in <module>
      1 age = 53
---> 2 remaining = 100 - aege # mis-spelled 'age'

NameError: name 'aege' is not defined
```

- 実行をトレースすることで、ソースとランタイムエラーを読み取って構文エラーを修正しました。

::::::::::::::::::::::::::::::::: チャレンジ

## 何時に起こるのか

1. Explain in simple terms the order of operations in the following program:
   when does the addition happen, when does the subtraction happen,
   when is each function called, etc.
2. `輝度`の最終値は何ですか？

```python
radiance = 1.0
radiance = max(2.1, 2.0 + min(radiance, 1.1 * radiance - 0.5))
```

::::::::::::::::: solution

## 解決策

1. 操作の順序:

2. `1.1 * radiance = 1.1`

3. `1.1 - 0.5 = 0.6`

4. `min(radiance, 0.6) = 0.6`

5. `2.0 + 0.6 = 2.6`

6. `max(2.1, 2.6) = 2.6`

7. 最後に `radiance = 2.6`

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 違いを見つけてください

1. 以下のプログラムの `print` 文のそれぞれが印刷されることを予測します。
2. `max(len(rich),貧弱)` は実行されるか、またはエラーメッセージが表示されますか？
   それが動くなら、その結果は何か意味をなさいますか?

```python
easy_string = "abc"
print(max(easy_string))
rich = "gold"
poor = "tin"
print(max(rich), len(貧乏))
print(max(rich), len(貧乏))
```

::::::::::::::::: solution

## 解決策

```python
print(max(easy_string))
```

```output
c
```

```python
print(max(rich, beoo))
```

```output
錫(つね)
```

```python
print(max(len(rich), len(poor)))
```

```output
4
```

`max(len(rich), below)` はTypeErrorを投げます。 先ほど説明したように、文字列と整数は意味のない比較ができないので、これは `max(4, 'tin')` と
になります。

```error
TypeError                                 Traceback (most recent call last)
<ipython-input-65-bc82ad05177a> in <module>
----> 1 max(len(rich), poor)

TypeError: '>' not supported between instances of 'str' and 'int'
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## なぜそうしないのですか？

引数なしで呼び出されたときに `max` と `min` が `None` を返さないのはなぜですか？

::::::::::::::::: solution

## 解決策

`max` と `min` は正しいパラメータ
が指定されていないため、この場合TypeErrorsを返します。 If it just returned `None`, the error would be much harder to trace as it
would likely be stored into a variable and used later in the program, only to likely throw
a runtime error.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 文字列の最後の文字

If Python starts counting from zero,
and `len` returns the number of characters in a string,
what index expression will get the last character in the string `name`?
(注:後のエピソードでこれを行う簡単な方法がわかります。

::::::::::::::::: solution

## 解決策

`name[len(name) - 1]`

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## Pythonドキュメントを探索しよう！

The [official Python documentation](https://docs.python.org/3/) is arguably the most complete
source of information about the language. それは異なる言語で利用可能で、多くの有用な
リソースを含んでいます。 The [Built-in Functions page](https://docs.python.org/3/library/functions.html) contains a catalogue of
all of these functions, including the ones that we've covered in this lesson. これらのうちのいくつかはより高度で、現時点では
不要ですが、他のものは非常にシンプルで便利です。

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- プログラムにドキュメントを追加するには、コメントを使用します。
- 関数は0以上の引数を取ることができます。
- 一般的に使用される組み込み関数には、`max`、`min`、および`round`が含まれます。
- 関数は特定の引数(組み合わせ)に対してのみ動作します。
- 関数はいくつかの引数にデフォルト値を持つことができます。
- 関数のヘルプを取得するには、組み込み関数 `help` を使用します。
- Jupyter Notebook には二つの方法があります。
- すべての関数は何かを返します。
- Pythonはプログラムのソースを理解できない場合、構文エラーを報告します。
- プログラムの実行中に問題が発生した場合、Pythonはランタイムエラーを報告します。
- ソースコードを読み込んで構文エラーを修正し、実行時エラーをプログラムの実行を追跡して修正しました。

::::::::::::::::::::::::::::::::::::::::::::::::::
