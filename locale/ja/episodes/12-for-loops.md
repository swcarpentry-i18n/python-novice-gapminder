---
title: ループ
teaching: 10
exercises: 15
---

::::::::::::::::::::::::::::::::::::::: objectives

- ループが通常に使用されるものを説明します。
- 単純(unnested)ループの実行をトレースし、各反復内の変数の値を正しくステートメントします。
- Accumulatorパターンを使用して値を集計するループに書き込みます。

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::

- プログラムを作るにはどうしたらいいですか？

::::::::::::::::::::::::::::::::::::::::::::::::::

## _for loop_ は、コレクション内の値ごとにコマンドを1回実行します。

- リスト内の値を1つずつ計算する
  は、 `pressure_001` や `pressure_002` などを扱うのと同じくらい苦労します。
- _for loop_ は、リスト、
  文字列、
  または他のコレクション内の値ごとに、いくつかの文を1回実行するようにPythonに指示します。
- "このグループの各事ごとに、これらの操作を行います"

```python
for number in [2, 3, 5]:
    print(number)
```

- `まで` は次のようになります。

```python
print(2)
print(3)
print(5)
```

- `まつ`の出力は次のとおりです。

```output
2
3
5
```

## `まつ`は、コレクション、ループ変数、および本体で構成されています。

```python
for number in [2, 3, 5]:
    print(number)
```

- `[2, 3, 5]`のコレクションは、ループが実行されているものです。
- body `print(number)` は、コレクション内の各値に対して何をするかを指定します。
- ループ変数`number`は、ループの_繰り返し_ごとに変更されるものです。
  - 「現在のもの」。

## `まつ` の最初の行はコロンで終わらなければなりません。そして、本体はインデントされなければなりません。

- 最初の行の末尾にあるコロンは、文の_ブロック_の始まりを示します。
- Python は _ネスティング_を表示するために `{}` や `begin`/`end` ではなくインデントを使用します。
  - 一貫したインデントは合法ですが、ほとんどの人は4つのスペースを使用します。

```python
for number in [2, 3, 5]:
print(number)
```

```error
IndentationError: expected block
```

- インデントはPythonでは常に意味があります。

```python
firstName = "Jon"
  lastName = "Smith"
```

```error
  File "<ipython-input-7-f65f2962bf9c>", line 2
    lastName = "Smith"
    ^
indentationError: unexpected indent
```

- このエラーは、2行目の最初の余分なスペース
  を削除することで修正できます。

## ループ変数は何でも呼ぶことができます。

- すべての変数と同様に、ループ変数は次のとおりです。
  - 需要に応じて作成されます。
  - 意味のない:彼らの名前は何でもあり得ます。

```python
for kitten [2, 3, 5]:
    print(kitten)
```

## ループの本文には多くの文を含めることができます。

- しかし、ループは数行以上でなければなりません。
- 人間がより大きなコードを念頭に置くのは難しい。

```python
primes = [2, 3, 5]
for p in primes:
    squared = p ** 2
    cubed = p ** 3
    print(p. 2乗、3乗)
```

```output
2 4 8
3 9 27
5 25 125
```

## 数字のシーケンスを繰り返すには、`range` を使います。

- 組み込み関数 [`range`](https://docs.python.org/3/library/stdtypes.html#range) は数字のシーケンスを生成します。
  - _注意_ リスト：数字はオンデマンドで
    生成され、広い範囲でループをより効率的にします。
- `range(N)` は0..N-1
  - 正確には長さNのリストまたは文字列の法的インデックス

```python
print('a range is not a list: range(0, 3)')
for number in range(0, 3):
    print(number)
```

```output
範囲がリストではありません: range(0, 3)
0 0
1
2
```

## Accumulatorパターンは多くの値を1に変換します。

- プログラムの一般的なパターンは以下です。
  1. _accumulator_ 変数をゼロ、空の文字列、または空のリストに初期化します。
  2. コレクションの値で変数を更新します。

```python
# 最初の10の整数を合計します。
total = 0
for number in range(10):
   total = total + (number + 1)
print(total)
```

```output
55
```

- `total = total + (number + 1)`を次のように読みます。
  - `number` 変数の現在の値に 1 を足します。
  - accumulator 変数 `total` の現在の値に追加します。
  - これを `total` に割り当て、現在の値を置き換えます。
- `range`は1..10ではなく0..9を生成するので、`number + 1` を追加します。

::::::::::::::::::::::::::::::::: チャレンジ

## エラーの分類

インデントエラーは構文エラーまたは実行時エラーですか?

::::::::::::::::: solution

## 解決策

IndentationError は、構文エラーです。 構文エラーのあるプログラムを起動できません。
実行時エラーのあるプログラムが起動しますが、特定の条件下でエラーがスローされます。

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 実行のトレース

このプログラムを実行したときに実行される行の数を示すテーブルを作成します。
と各行後の変数の値が実行されます。

```python
total = 0
for char in "tin":
    total = total + 1
```

::::::::::::::::: solution

## 解決策

| 行番号 | 変数                   |
| --- | -------------------- |
| 1   | total = 0            |
| 2   | total = 0 char = 't' |
| 3   | total = 1 char = 't' |
| 2   | total = 1 char = 'i' |
| 3   | total = 2 char = 'i' |
| 2   | total = 2 char = 'n' |
| 3   | total = 3 char = 'n' |

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## Reversing a String

"nit"
(元の文字列「tin」の逆)を出力するように、以下のプログラムの空白を埋めてください。

```python
original = "tin"
result = ____
for char in original:
    result = ____
print(result)
```

::::::::::::::::: solution

## 解決策

```python
original = "tin"
result = ""
for char in original:
    result = char + result
print(result)
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 累積練習をする

指定された結果を生成するには、
以下の各プログラムの空白を入力してください。

```python
# Total length of the strings in the list: ["red", "green", "blue"] => 12
total = 0
for word in ["red", "green", "blue"]:
    ____ = ____ + len(word)
print(total)
```

::::::::::::::::: solution

## 解決策

```python
total = 0
for word in ["red", "green", "blue"]:
    total = total + len(word)
print(total)
```

:::::::::::::::::::::::::

```python
# List of word lengths: ["red", "green", "blue"] => [3, 5, 4]
lengths = ____
for word in ["red", "green", "blue"]:
    lengths.____(____)
print(lengths)
```

::::::::::::::::: solution

## 解決策

```python
length= []
for word in ["red", "green", "blue"]:
    lengths.append(len(word))
print(lengths)
```

:::::::::::::::::::::::::

```python
# Concatenate all words: ["red", "green", "blue"] => "redgreenblue"
words = ["red", "green", "blue"]
result = ____
for ____ in ____:
    ____
print(result)
```

::::::::::::::::: solution

## 解決策

```python
words = ["red", "green", "blue"]
result = ""
for word in words:
    result = result + word
print(result)
```

:::::::::::::::::::::::::

**頭字語を作成しましょう** `["red", "green", "blue"]`のリストから始まり、
a for ループを使って頭字語`RGB"`を作りましょう。

**ヒント:** 頭字語を正しくフォーマットするために文字列メソッドを使用する必要があります。

::::::::::::::::: solution

## 解決策

```python
acronym = ""
for word in ["red", "green", "blue"]:
    acronym = acronym + word[0].upper()
print(acronym)
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 累積合計

Reorder and properly indent the lines of code below
so that they print a list with the cumulative sum of data.
結果は `[1, 3, 5, 10]` でなければなりません。

```python
cumulative.append(total)
for number in data:
cumulative = []
total = total + number
total = 0
print(cumulative)
data = [1,2,2,5]
```

::::::::::::::::: solution

## 解決策

```python
total = 0
data = [1,2,2,5]
cumulative = []
for number in data:
    total = total + number
    cumulative.append(total)
print(cumulative)
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 変数名エラーの識別

1. 以下のコードを読んで、
   _実行しない_エラーを特定してみてください。
2. コードを実行し、エラーメッセージを読みます。
   `NameError` の種類は？
   引用符なし、スペルミスのある変数、または定義されるべきではなかった
   変数を含む文字列ですか?
3. エラーを修正します。
4. すべてのエラーを修正するまで、ステップ2と3を繰り返します。

```python
for number in range(10):
    # use a if the number is a multiple of 3, otherwise use b
    if (Number % 3) == 0:
        message = message + a
    else:
        message = message + "b"
print(message)
```

::::::::::::::::: solution

## 解決策

- Python の変数名は大文字と小文字を区別します: `number` と `Number` は異なる変数を参照します。
- 変数`message`は空の文字列として初期化する必要があります。
- 未定義の変数 `a` ではなく、文字列 `a" を `message\` に追加します。

```python
message = ""
for number in range(10):
    # use a if the number is a multiple of 3, otherwise use b
    if (number % 3) == 0:
        message = message + "a"
    else:
        message = message + "b"
print(message)
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 項目エラーの識別

1. 以下のコードを読んで、
   _実行しない_エラーを特定してみてください。
2. コードを実行し、エラーメッセージを読みます。 どのようなタイプのエラーですか?
3. エラーを修正します。

```python
seases = ['春', '夏', '秋', '冬']
print('私の好きな季節は', seasons[4])
```

::::::::::::::::: solution

## 解決策

このリストには4つの要素があり、リストの最後の要素にアクセスするインデックスは `3` です。

```python
seases = ['春', '夏', '秋', '冬']
print('私の好きな季節は', seasons[3])
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- _for loop_ は、コレクション内の値ごとにコマンドを1回実行します。
- `まつ`は、コレクション、ループ変数、および本体で構成されています。
- `まつ` の最初の行はコロンで終わらなければなりません。そして、本体はインデントされなければなりません。
- インデントはPythonでは常に意味があります。
- ループ変数は何でも呼び出すことができます(ただし、ループ変数に意味のある名前を付けることを強くお勧めします)。
- ループの本文には多くの文を含めることができます。
- 数字のシーケンスを繰り返すには、`range` を使います。
- Accumulatorパターンは多くの値を1に変換します。

::::::::::::::::::::::::::::::::::::::::::::::::::
