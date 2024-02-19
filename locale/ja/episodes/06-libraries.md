---
title: ライブラリ
teaching: 10
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- ソフトウェアライブラリとは何か、プログラマーがそれらを作成して使用する理由を説明します。
- Pythonの標準ライブラリからモジュールをインポートして使用するプログラムを書く。
- 標準ライブラリのドキュメントをインタラクティブに(通訳で)見つけて読んでください。

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::

- 他の人が書いたソフトウェアをどのように使用できますか?
- そのソフトウェアが何をしているのかを調べるにはどうすればいいですか?

::::::::::::::::::::::::::::::::::::::::::::::::::

## プログラミング言語の力のほとんどはライブラリにあります。

- _library_ は、他のプログラムで使用するための
  関数を含むファイル(_modules_ と呼ばれる)のコレクションです。
  - データ値(数値定数など)なども含めることができます。
  - 図書館の内容は関連するはずですが、それを強制する方法はありません。
- Python [standard library][stdlib] は、Python 自体に
  付属のモジュール群です。
- 多くの追加ライブラリは [PyPI][pypi] (Python Package Index) から入手できます。
- 後で新しいライブラリの作成方法を見ていきます。

:::::::::::::::::::::::::::::::::::::::::  callout

## ライブラリとモジュール

A library is a collection of modules, but the terms are often used
interchangeably, especially since many libraries only consist of a single
module, so don't worry if you mix them.

::::::::::::::::::::::::::::::::::::::::::::::::::

## プログラムはライブラリモジュールを使用する前にインポートする必要があります。

- プログラムのメモリにライブラリモジュールをロードするには、 `import` を使います。
- 次に、モジュール内のものを `module_name.thing_name` として参照します。
  - Python は `.` を使って「の一部」を意味します。
- 標準ライブラリのモジュールの一つである `math` を使用します。

```python
import math

print('pi is', math.pi)
print('cos(pi) is', math.cos(math.pi))
```

```output
pi は 3.141592653589793
cos(pi) は -1.0
```

- モジュールの名前で各項目を参照する必要があります。
  - `math.cos(pi)`は動作しません: `pi`
    への参照は何らかの形で`math`への関数の参照を"継承"しません。

## ライブラリモジュールの内容については、 `help` を使います。

- 関数のヘルプのように動作します。

```python
help(数学)
```

```output
Help on module math:

NAME
    math

MODULE REFERENCE
    http://docs.python.org/3/library/math

    The following documentation is automatically generated from the Python
    source files.  It may be incomplete, incorrect or include features that
    are considered implementation detail and may vary between Python
    implementations.  When in doubt, consult the module reference at the
    location listed above.

DESCRIPTION
    This module is always available.  It provides access to the
    mathematical functions defined by the C standard.

FUNCTIONS
    acos(x, /)
        Return the arc cosine (measured in radians) of x.
⋮ ⋮ ⋮
```

## プログラムを短縮するためにライブラリモジュールから特定の項目をインポートします。

- `from ... import ...` to load only specific items from a library module.
- 次に、ライブラリ名なしで直接プレフィックスとして参照します。

```python
from math import cos, pi

print('cos(pi) is', cos(pi))
```

```output
cos(pi) は -1.0
```

## プログラムを短縮するためにインポートするときにライブラリモジュールのエイリアスを作成します。

- `import を使用... として...`ライブラリにインポート中に短い_エイリアス_を与えます。
- その後、短縮した名前を使用してライブラリ内の項目を参照してください。

```python
import math as m

print('cos(pi) is', m.cos(m.pi))
```

```output
cos(pi) は -1.0
```

- 頻繁に使用される、または長い名前のライブラリのために一般的に使用されます。
  - 例えば、`matplotlib`プロットライブラリはしばしば`mpl`としてエイリアスされます。
- しかし、
  はあなたのプログラムのエイリアスを学ばなければならないので、プログラムを理解しにくくすることができます。

::::::::::::::::::::::::::::::::: チャレンジ

## 数学モジュールの探索

1. `math`モジュールのどの関数を使って、`sqrt`を使って、平方根
   _ない_を計算できますか？
2. ライブラリにはこの関数が含まれているので、なぜ`sqrt`が存在するのでしょうか？

::::::::::::::::: solution

## 解決策

1. Using `help(math)` we see that we've got `pow(x,y)` in addition to `sqrt(x)`,
   so we could use `pow(x, 0.5)` to find a square root.

2. `sqrt(x)`関数は、
   が方程式を実装した場合、間違いなく`pow(x, 0.5)`より読みやすいです。 読みやすさは良いプログラミングの土台であるため、
   はこの特定の一般的なケースに特別な関数を提供することは理にかなっています。

Also, the design of Python's `math` library has its origin in the C standard,
which includes both `sqrt(x)` and `pow(x,y)`, so a little bit of the history
of programming is showing in Python's function names.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 右モジュールの位置

文字列からランダムな文字を選択します。

```python
bases = 'ACTTGCTTGAC'
```

1. どの[standard library][stdlib] モジュールが役に立ちますか？
2. そのモジュールからどの関数を選択しますか？ 選択肢はありますか？
3. 関数を使うプログラムを書いてみてください。

::::::::::::::::: solution

## 解決策

[random module][randommod] は役に立つかもしれません。

文字列は 11 文字で、それぞれは 0 から 10 までの位置指数を持ちます。
You could use the [`random.randrange`](https://docs.python.org/3/library/random.html#random.randrange)
or [`random.randint`](https://docs.python.org/3/library/random.html#random.randint) functions
to get a random integer between 0 and 10, and then select the `bases` character at that index:

```python
from random import randrange

random_index = randrange(len(bases))
print(bases[random_index])
```

もっとコンパクトに

```python
from random import randrange

print(bases[randrange(len(bases))])
```

[`random.sample`](https://docs.python.org/3/library/random.html#random.sample) 関数が見つかりましたか？
これにより、少しタイピングが少なくなりますが、読むだけで理解が少し難しいかもしれません。

```python
from random import sample

print(sample(bases, 1)[0])
```

この関数は値のリストを返すことに注意してください。 [エピソード 11](11-lists.md) の
リストについて学びます。

最もシンプルで短い解は、[`random.choice`](https://docs.python.org/3/library/random.html#random.choice)
関数で、これを正確に実行します。

```python
from random import choice

print(choice(bases))
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## ジグソーパズル (Parsonの問題) プログラミング例

以下の文を並べ替えて、ランダムな
DNA ベースが出力され、そのインデックスが文字列中に出力されるようにします。
すべての文が必要とは限りません。\
中間変数を使用/追加してください。

```python
bases="ACTGCTTGAC"
import math
import random
____ = random.range(n_bases)
____ = len(bases)
print("random base ", bases[___], "base index", ____
```

::::::::::::::::: solution

## 解決策

```python
import math 
import random
bases = "ACTTGCTTGAC" 
n_bases = len(bases)
idx = random.randrange(n_bases)
print("random base", bases[idx], "base index", idx)
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## ヘルプはいつ利用できますか?

あなたの同僚が`help(math)`をタイプすると、
Pythonはエラーを報告します。

```error
NameError: name 'math' is not defined
```

あなたの同僚は何を忘れてしまったのですか?

::::::::::::::::: solution

## 解決策

算術モジュールのインポート (`import math`)

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## エイリアスでインポートする

1. 以下のプログラムが `90.0` に出力されるように空白を埋めてください。
2. `import` \*without \* `as` を使うようにプログラムを書き直します。
3. どちらのフォームが読みやすいと思いますか。

```python
import math as m
angle = ____.degrees(____.pi / 2)
print(____)
```

::::::::::::::::: solution

## 解決策

```python
import math as m
angle = m.degrees(m.pi / 2)
print(angle)
```

次のように書くことができます

```python
import math
angle = math.degrees(math.pi / 2)
print(angle)
```

コードを書いたばかりで慣れているので、実際には
最初のバージョンが読みやすいと思うかもしれません。 But when trying to read a huge piece
of code written by someone else, or when getting back to your own huge piece
of code after several months, non-abbreviated names are often easier, except
where there are clear abbreviation conventions.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## ライブラリをインポートする方法はたくさんあります!

次の印刷文を適切なライブラリ呼び出しと一致させます。

コマンドを印刷:

1. `print("sin(pi/2) =", sin(pi/2))`
2. `print("sin(pi/2) =", m.sin(m.pi/2))`
3. `print("sin(pi/2) =", math.sin(math.pi/2))`

ライブラリ通話:

1. `from math import sin, pi`
2. `import math`
3. `import math as m`
4. `from math import *`

::::::::::::::::: solution

## 解決策

1. ライブラリから1と4を呼び出します。 ライブラリ名を
   をプレフィックスとせずに `sin` と `pi` を直接参照するには、 `from ... import ...`
   ステートメント ライブラリ1は特に2つの関数
   `sin` と `pi` をインポートしますが、ライブラリ4は`math` モジュール内のすべての関数をインポートします。
2. ライブラリ通話 3. ここでは、`sin`と`pi`は、`math`の代わりに、短縮ライブラリ
   の名前で参照されます。 ライブラリコール3は、
   `import ... を使用してまさにそれを行います。 as ...` syntax - it creates an alias for `math` in the form of
   the shortened name `m`.
3. ライブラリ通話 2. ここでは、`sin`と`pi`は通常のライブラリ
   の名前で参照されるので、通常の`import ...`を呼び出すだけで十分です。

**Note:** although library call 4 works, importing all names from a module using a wildcard
import is [not recommended][pep8-imports] as it makes it unclear which names from the module
are used in the code. 一般的には、インポートを可能な限り具体的にし、
コードが使うものだけをインポートすることをお勧めします。 In library call 1, the `import` statement explicitly tells us
that the `sin` function is imported from the `math` module, but library call 4 does not
convey this information.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 特定のアイテムをインポートしています

1. 以下のプログラムが `90.0` に出力されるように空白を埋めてください。
2. このバージョンは先行バージョンより読みやすいですか?
3. なぜプログラマーは常に `import` を使わないのでしょうか？

```python
____ math import ____, ____
angle = degrees(pi / 2)
print(angle)
```

::::::::::::::::: solution

## 解決策

```python
from math import degree, pi
angle = degrees(pi / 2)
print(angle)
```

それは密度が低いので、ほとんどの場合、このバージョンは読みやすいです。
このフォームを使用しない主な理由は、名前の衝突を避けるためです。
For instance, you wouldn't import `degrees` this way if you also wanted to
use the name `degrees` for a variable or function of your own. Or if you
were to also import a function named `degrees` from another library.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## エラー メッセージの読み取り

1. 以下のコードを読んで、実行せずにエラーを特定してみてください。
2. コードを実行し、エラーメッセージを読みます。 どのようなタイプのエラーですか?

```python
from math import log
log(0)
```

::::::::::::::::: solution

## 解決策

```output
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
<ipython-input-1-d72e1d780bab> in <module>
      1 from math import log
----> 2 log(0)

ValueError: math domain error
```

1. `x` の対数は `x > 0` にのみ定義されているため、0 は関数の
   ドメイン外です。

2. 関数
   が不適切な引数値を受け取ったことを示す、型 `ValueError` のエラーが表示されます。 追加のメッセージ
   「数学領域エラー」は、問題が何であるかをより明確にします。

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

[stdlib]: https://docs.python.org/3/library/

[pypi]: https://pypi.python.org/pypi/

[randommod]: https://docs.python.org/3/library/random.html

[pep8-imports]: https://pep8.org/#import

:::::::::::::::::::::::::::::::::::::::: keypoints

- プログラミング言語の力のほとんどはライブラリにあります。
- プログラムはライブラリモジュールをインポートする必要があります。
- ライブラリモジュールの内容については、 `help` を使います。
- 特定のアイテムをライブラリからインポートしてプログラムを短縮します。
- プログラムを短縮するためにインポートするときに、ライブラリのエイリアスを作成します。

::::::::::::::::::::::::::::::::::::::::::::::::::
