---
title: 変数スコープ
teaching: 10
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- ローカルおよびグローバル変数を特定します。
- パラメータをローカル変数として識別します。
- トレースバックを読み、エラーが発生したファイル、関数、行番号、エラーの種類、エラーメッセージを決定します。

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::

- 関数呼び出しは実際にどのように動作しますか?
- どこでエラーが発生したかを確認するにはどうすればよいですか?

::::::::::::::::::::::::::::::::::::::::::::::::::

## 変数のスコープは、変数を「見る」ことができるプログラムの一部です。

- 変数には非常に多くの賢明な名前しかありません。
- People using functions shouldn't have to worry about
  what variable names the author of the function used.
- 関数を書いている人は、関数の呼び出し元が使用する変数の名前を
  気にする必要はありません。
- 変数が表示されるプログラムの一部は _scope_ と呼ばれます。

```python
pressure = 103.9

def adjust(t):
    temperature = t * 1.43 / pressure
    リターン温度
```

- `pressure`は_グローバル変数_です。
  - 特定の関数の外側で定義されます。
  - どこにでも表示できます。
- `t`と`temperature`は`adjust`の_ローカル変数_です。
  - 関数で定義します。
  - メインプログラムには表示されません。
  - 関数パラメータは、関数が呼び出されたときに自動的に値が割り当てられる変数
    です。

```python
print('adjusted:', adjust(0.9))
print('call:', temperature)
```

```output
adjusted: 0.01238691049085659
```

```error
トレースバック (直近の呼び出しが最後):
  ファイル "/Users/swcarpentry/foo.py", 行8, in <module>
    print('call:', temperature)
NameError: name 'temperature' is not defined
```

::::::::::::::::::::::::::::::::: チャレンジ

## ローカルおよびグローバル変数の使用

実行時にこのプログラム内のすべての変数の値をトレースします。
(変数が存在する前後の値として「---」を使用します。

```python
limit = 100

def clip(value):
    return min(max(0.0, value), limit)

value = -22.5
print(clip(value))
```

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## エラー メッセージの読み取り

以下のトレースバックを読み、以下のように識別します。

1. トレースバックのレベルはいくつですか？
2. エラーが発生したファイル名は何ですか?
3. エラーが発生した関数名は何ですか?
4. この関数のどの行番号でエラーが発生しましたか?
5. エラーの種類は何ですか?
6. エラーメッセージとは何ですか?

```error
---------------------------------------------------------------------------
KeyError                                  Traceback (most recent call last)
<ipython-input-2-e4c4cbafeeb5> in <module>()
      1 import errors_02
----> 2 errors_02.print_friday_message()

/Users/ghopper/thesis/code/errors_02.py in print_friday_message()
     13
     14 def print_friday_message():
---> 15     print_message("Friday")

/Users/ghopper/thesis/code/errors_02.py in print_message(day)
      9         "sunday": "Aw, the weekend is almost over."
     10     }
---> 11     print(messages[day])
     12
     13

KeyError: 'Friday'
```

::::::::::::::::: solution

## 解決策

1. ３つのレベルです

2. `errors_02.py`

3. `print_message`

4. 11行目

5. `KeyError`. これらのエラーは、存在しないキー(通常は辞書のようなデータ
   構造体内)を検索しようとするときに発生します。 We can find more information about the `KeyError` and other built-in exceptions
   in the [Python docs](https://docs.python.org/3/library/exceptions.html#KeyError).

6. `KeyError: 'Friday'`

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- 変数のスコープは、変数を「見る」ことができるプログラムの一部です。

::::::::::::::::::::::::::::::::::::::::::::::::::
