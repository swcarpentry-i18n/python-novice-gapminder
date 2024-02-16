---
title: リスト
teaching: 10
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- プログラムがなぜ価値観のコレクションを必要とするかを説明してください。
- フラットリストを作成したり、インデックスを作成したり、スライスしたり、割り当てやメソッド呼び出しで変更したりするプログラムを記述します。

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::

- 複数の値を保存するにはどうすればよいですか?

::::::::::::::::::::::::::::::::::::::::::::::::::

## リストは多くの値を単一の構造体に格納します。

- `pressure_001`、`pressure_002`などと呼ばれる100個の変数を使って計算すると、
  は少なくとも手作業で計算するのと同じくらい遅いでしょう。
- _list_ を使用して、多くの値をまとめて格納します。
  - 角括弧`[...]`内に含まれています。
  - 値はコンマ`,`で区切られます。
- リスト内の値の数を調べるには、`len`を使います。

```python
pressures = [0.273, 0.275, 0.277, 0.275, 0.276]
print('pressures:', pressures)
print('length:', len(pressures))
```

```output
圧力: [0.273, 0.275, 0.277, 0.275, 0.276]
長: 5
```

## リストから取得するには、項目のインデックスを使用します。

- 文字列のように。

```python
print('圧力のゼロ項目:', 圧力[0])
print('圧力の4番目の項目:', 圧力[4])
```

```output
圧力のゼロ項目: 0.273
4番目の圧力: 0.276
```

## リストの値はそれらに割り当てることによって置き換えることができる。

- 代入の左側にあるインデックス式を使用して、値を置き換えます。

```python
圧力[0] = 0.265
print('圧力は今:', 圧力)
```

```output
圧力は現在0.265、0.275、0.277、0.275、0.276です
```

## リストに項目を追加すると長くなります。

- リストの最後に項目を追加するには、`list_name.append` を使用します。

```python
prime = [2, 3, 5]
print('prime is initially:', primes)
primes.append(7)
print('prime has become', primes)
```

```output
素数は最初は: [2, 3, 5]
素数は: [2, 3, 5, 7]
```

- `append` はリストの _メソッド_ です。
  - 関数のように、特定のオブジェクトに関連付けられています。
- メソッドを呼び出すには `object_name.method_name` を使用します。
  - 故意にライブラリ内のものを参照するように似ています。
- 私たちは進むにつれて他のリストの方法を満たします。
  - プレビューには `help(list)` を使います。
- `extend` は `append` と似ていますが、2つのリストを組み合わせることができます。  例:

```python
teen_primes = [11, 13, 17, 19]
middle_aged_primes = [37, 41, 43, 47]
print('primes is currently:', primes)
primes.extend(teen_primes)
print('primes has now become:', primes)
primes.append(middle_aged_primes)
print('primes has finally become:', primes)
```

```output
素数は現在のところ: [2, 3, 5, 7]
素数は: [2, 3, 5, 7, 11, 13, 17, 19] 

素数はついに次のようになりました: [2, 3, 5, 7, 11, 13, 17, 19, [37, 41, 43, 47]]
```

`extend` はリストの「フラット」構造を維持しています。 リストにリストを追加すると、
`primes` の最後の要素はリストであり、整数ではありません。 リストには
タイプの値を含めることができます。したがって、リストのリストは可能です。

## リストから項目を完全に削除するには、`del`を使用します。

- リストから要素を削除するには、 `del list_name[index]` を使います(例: 9は素数ではないので、それを短くします。
- `del`は関数やメソッドではなく、言語の文です。

```python
primes = [2, 3, 5, 7, 9]
print('primes before removing last item:', primes)
del primes[4]
print('remove last item:', primes)
```

```output
最後の項目を削除する前の素数: [2, 3, 5, 7, 9]
最後の項目を削除した後の素数: [2, 3, 5, 7]
```

## 空のリストには値がありません。

- 値を含まないリストを表現するには、 `[]` を使います。
  - 「リストのゼロ」です
- 値を集めるための出発点として役立ちます（format@@1(12-for-loops.md)）。

## リストには異なる型の値が含まれている可能性があります。

- 単一のリストには、数字、文字列、および他の何でも含めることができます。

```python
goals = [1, 'Create lists.', 2, 'Extract items from lists.', 3, 'Modify lists.');
```

## 文字列はリストのようにインデックスすることができます。

- 角括弧内の索引を使用して文字列から単一の文字を取得します。

```python
element = 'carbon'
print('ゼロ文字:', element[0])
print('third character:', element[3])
```

```output
ゼロ文字: c
3番目の文字: b
```

## 文字列は変更不能です。

- 文字列を作成した後は文字列内の文字を変更できません。
  - _不変_: 作成後は変更できません。
  - 対照的に、リストは _mutable_: それらは場所で変更することができます。
- Pythonは文字列を部分を持つ単一の値であると考えています。
  値のコレクションではありません。

```python
要素[0] = 'C'
```

```error
TypeError: 'str' オブジェクトはアイテムの割り当てをサポートしていません
```

- リストと文字列はどちらも _コレクション_ です。

## コレクションの終わりを超えたインデックス作成はエラーです。

- Pythonは存在しない値にアクセスしようとすると、 `IndexError` を報告します。
  - これは一種のformat@@0(04-built-in.md)です。
  - Cannot be detected as the code is parsed
    because the index might be calculated based on data.

```python
print('要素の99番目の要素は:', 要素[99])
```

```output
インデックスエラー: 文字列インデックスが範囲外です
```

::::::::::::::::::::::::::::::::: チャレンジ

## 空白を埋めよう

以下のプログラムが表示される出力を生成するように空白を埋めます。

```python
value = ____
values.____(1)
values.____(3)
values.____(5)
print('first time:', values)
values = value[____]
print('second time:', values)
```

```output
1回目:[1, 3, 5]
2回目:[3, 5]
```

::::::::::::::::: solution

## 解決策

```python
values = []
values.append(1)
values.append(3)
values.append(5)
print('first time:', values)
values = values[1:]
print('second time:', values)
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## スライスの大きさは？

`start` と `stop` が両方とも負の整数でない場合、
リストの `values[start:stop]` はどれくらいですか?

::::::::::::::::: solution

## 解決策

`values[start:stop]`のリストには、`stop - start` 要素があります。  例えば、
`values[1:4]`には、`values[1]`、`values[2]`、`values[3] `の3つの要素があります。
なぜ「アップ」するのか？ As we saw in [episode 2](02-variables.md),
if `stop` is greater than the total length of the list `values`,
we will still get a list back but it will be shorter than expected.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 文字列からリストおよび戻る

与えられたもの

```python
print('string to list:', list('tin'))
print('list to string:', ''.join(['g', 'o', 'l', 'd']))
```

```output
string: ['t', 'i', 'n'
string: gold
```

1. `list('some string')` は何をしますか？
2. `-'.join(['x', 'y', 'z'])`は何を生成しますか？

::::::::::::::::: solution

## 解決策

1. [`list('some string')`](https://docs.python.org/3/library/stdtypes.html#list) は文字列をすべての文字を含むリストに変換します。

2. [`join`](https://docs.python.org/3/library/stdtypes.html#str) oin) はリスト内の各string要素の_連結_
   である文字列を返し、リスト内の各要素の間に区切り文字を追加します。 これは
   `x-y-z` になります。 要素間の区切り文字は、このメソッドを提供する文字列です。

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## エンドユーザーとの作業

以下のプログラムは何を印刷しますか?

```python
element = 'helium'
print(element[-1])
```

1. Pythonは負のインデックスをどのように解釈しますか?
2. If a list or string has N elements,
   what is the most negative index that can safely be used with it,
   and what location does that index represent?
3. `values`がリストの場合、`del values[-1]`は何をしますか？
4. `values`を変更せずに、最後の要素以外の要素をどのように表示できますか？
   (ヒント:スライスと負のインデックスを組み合わせる必要があります。

::::::::::::::::: solution

## 解決策

プログラムは `m` を出力します。

1. Python interprets a negative index as starting from the end (as opposed to
   starting from the beginning).  最後の要素は `-1` です。

2. N 要素のリストで安全に使用できる最後のインデックスは、要素
   `-N` で、最初の要素を表します。

3. `del values[-1]` はリストから最後の要素を削除します。

4. `values[:-1]`

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## リストをステッピングする

以下のプログラムは何を印刷しますか?

```python
element = 'fluorine'
print(element[::2])
print(element[::-1])
```

1. `low:high:stride`と書くと、`stride`は何をしますか？
2. コレクションから偶数番号のすべてのアイテムを選択する式は何ですか?

::::::::::::::::: solution

## 解決策

プログラム印刷

```python
furn
eniroulf
```

1. `stride`はスライスのステップサイズです。

2. The slice `1::2` selects all even-numbered items from a collection: it starts
   with element `1` (which is the second element, since indexing starts at `0`),
   goes on until the end (since no `end` is given), and uses a step size of `2`
   (i.e., selects every second element).

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## スライスの範囲

以下のプログラムは何を印刷しますか?

```python
element = 'リチウム'
print(element[0:20])
print(element[-1:3])
```

::::::::::::::::: solution

## 解決策

```output
lithium

```

スライスは文字列の全長を超えるため、最初の文は文字列全体を出力します。
2番目の文は、スライスが文字列の範囲外になるため、空の文字列を返します。

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 並べ替えと並べ替え

この２つのプログラムは何を印刷しますか？
簡単に言うと、`sorted(letters)` と `letters.sort()` の違いを説明します。

```python
# Program A
letters = list('gold')
result = sorted(letters)
print('letters is', letters, 'and result', result)
```

```python
# Program B
letters = list('gold')
result = letters.sort()
print('letters is', letters, 'and result is', result)
```

::::::::::::::::: solution

## 解決策

プログラム A プリント

```output
letters is ['g', 'o', 'l', 'd'] and result is ['d', 'g', 'l', 'o']
```

プログラム B 印刷

```output
letters is ['d', 'g', 'l', 'o'] and result is None
```

`sorted(letters)` returns a sorted copy of the list `letters` (the original
list `letters` remains unchanged), while `letters.sort()` sorts the list
`letters` in-place and does not return anything.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## コピー中 (またはコピーしない)

この２つのプログラムは何を印刷しますか？
簡単に言うと、`new = old`と`new = old[:]`の違いを説明します。

```python
# Program A
old = list('gold')
new = old # simple assign
new[0] = 'D'
print('new is', 新旧、旧）
```

```python
# Program B
old = list('gold')
new = old[:] # スライス
new[0] = 'D'
print('new is', 新旧、旧）
```

::::::::::::::::: solution

## 解決策

プログラム A プリント

```output
new is ['D', 'o', 'l', 'd'] and old is ['D', 'o', 'l', 'd']
```

プログラム B 印刷

```output
new is ['D', 'o', 'l', 'd'] and old is ['g', 'o', 'l', 'd']
```

`new = old` は、`new` を同じオブジェクトに向かって`new`と`old` 点
のリストへの参照にします。

`new = old[:]` は、`old`リストからすべての要素
を含む新しいリストオブジェクト`new`を作成します。`new`と`old`は異なるオブジェクトです。

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- リストは多くの値を単一の構造体に格納します。
- リストから取得するには、項目のインデックスを使用します。
- リストの値はそれらに割り当てることによって置き換えることができる。
- リストに項目を追加すると長くなります。
- リストから項目を完全に削除するには、`del`を使用します。
- 空のリストには値がありません。
- リストには異なる型の値が含まれている可能性があります。
- 文字列はリストのようにインデックスすることができます。
- 文字列は変更不能です。
- コレクションの終わりを超えたインデックス作成はエラーです。

::::::::::::::::::::::::::::::::::::::::::::::::::
