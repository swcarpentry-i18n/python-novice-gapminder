---
title: プログラミングスタイル
teaching: 15
exercises: 15
---

::::::::::::::::::::::::::::::::::::::: objectives

- コーディングスタイルの基本的なルールの正当化を提供します。
- 1 ページのプログラムをリファクタリングして、より読みやすくなり、変更を正当化します。
- Python コミュニティのコーディング規格 (PEP-8) を使用してください。

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::

- プログラムをもっと読みやすくするにはどうすればいいですか?
- ほとんどのプログラマーはどのようにコードをフォーマットしますか?
- プログラムはどのように自分の操作を確認することができますか?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Coding style

一貫性のあるコーディングスタイルは、他の人(私たちの将来を含む)がコードを読み取り、理解するのに役立ちます。 コードは書かれているよりもはるかに頻繁に読み取られ、format@@0(https\://www\.python.org/dev/peps/pep-0020) は「読みやすさ」を示しています。
Pythonは最初のPython拡張提案 (PEP), [PEP8](https://www.python.org/dev/peps/pep-0008) を通して標準的なスタイルを提案しました。

ハイライトする価値のあるいくつかのポイント:

- コードを文書化し、仮定、内部アルゴリズム、期待される入力、期待される出力などが明確であることを確認してください
- 意味的に意味のある変数名を使ってください
- ホワイトスペース、_not_ タブを使用して行をインデントする (タブは異なるテキストエディタ、オペレーティングシステム、バージョン管理システムで問題を引き起こす可能性があります)

## あなたのコードで標準の Python スタイルに従ってください。

- [PEP8](https://www.python.org/dev/peps/pep-0008):
  a style guide for Python that discusses topics such as how to name variables,
  how to indent your code,
  how to structure your `import` statements,
  etc.
  Adhering to PEP8 makes it easier for other Python developers to read and understand your code, and to understand what their contributions should look like.
- PEP8 に準拠しているかどうかを確認するには、[pycodestyle application](https://pypi.org/project/pycodestyle/)と、format@@0(https\://github) のようなツールを使用します。 om/psf/black)はPEP8とpycodestyle(Jupyterノートブックフォーマッタは[nb_black](https://github.com/dnanhkhoa/nb_black)に準拠するようにコードを自動的にフォーマットできます。
- 一部のグループや組織はPEP8以外にも異なるスタイルガイドラインに従っています。 例えば、[PythonのGoogleスタイルガイド](https://google.github.io/styleguide/pyguide/html)は少し異なる推奨をしています。 Google は、コードをスタイルまたは [yapf](https://github.com/google/yapf/) と呼ばれるPEP8 のいずれかでフォーマットするのに役立つアプリケーションを作成しました。
- コーディングスタイルに関しては、キーは_一貫性_です。 PEP8、Googleスタイルのプロジェクトのスタイルを選択してください。 自分と他の人が協力していることを確認するために最善を尽くしてください プロジェクト内の一貫性は、使用される特定のスタイルよりも影響力が高いことがよくあります。 一貫したスタイルは、ソフトウェアを他の人のために、そしてあなたの将来の自己のために読みやすくします。

## アサーションを使用して内部エラーを確認します。

アサーションは、コードが実行されているコンテキストが期待どおりであることを確認するためのシンプルで強力なメソッドです。

```python
def calc_bulk_density(mass, volume):
    '''''ドライバルク密度=粉末量/粉末量を返す。'''
    assert volume > 0
    return mass / volume
```

アサーションが `False` の場合、Python インタプリタは `AssertionError` ランタイム例外を発生させます。 失敗した式のソースコードがエラーメッセージの一部として表示されます。 コード内のアサーションを無視するには、インタプリタを '-O' (最適化) スイッチで実行します。 アサーションには、単純なチェックのみが含まれており、プログラムの状態を変更することはありません。 たとえば、アサーションに代入を含めてはいけません。

## 組み込みヘルプを提供するには、docstringsを使用してください。

関数内の最初のものが変数に直接割り当てられていない文字列である場合。 Pythonはそれを関数にアタッチし、組み込みのヘルプ関数でアクセスできます。 ドキュメントを提供するこの文字列は _docstring_ とも呼ばれます。

```python
def average(values):
    "Return average of values, or None if no values are supplied."

    if len(values) == 0:
        return None
    return sum(values) / len(values)

help(average)
```

```output
モジュール __main__の関数平均に関するヘルプ :

average(values)
    値の平均値を返すか、値が指定されていない場合は None を返します。
```

:::::::::::::::::::::::::::::::::::::::::  callout

## 複数行の文字列

ドキュメントには _multiline strings_ を使うことが多い。
これらの開始と終了は、3つの引用符文字 (シングルまたはダブル)
で、3つの一致する文字で終了します。

```python
"""This string spans
multiple lines.

Blank lines are allowed."""
```

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 何を表示しますか？

以下のコードの行を強調表示します。オンラインヘルプが表示されます。
利用可能にすべきではあるがそうでないラインはあるか。
どの行でも構文エラーやランタイムエラーが発生しますか?

```python
"Find maximum edit distance between multiple sequences."
# This finds the maximum distance between all sequences.

def overall_max(sequences):
    '''Determine overall maximum edit distance.'''

    highest = 0
    for left in sequences:
        for right in sequences:
            '''Avoid checking sequence against itself.'''
            if left != right:
                this = edit_distance(left, right)
                highest = max(highest, this)

    # Report.
    return highest
```

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## これを文書にする

コメントを使用して、他の人が潜在的に直感的でない
セクションや個々のコード行を理解するのに役立ちます。
があなたのコードを理解し編集する必要がある人には、あなた自身も含めて特に役立ちます。

docstrings を使用して、許容可能な入力と期待されるメソッド
またはクラスの出力、その目的、仮定、および意図された動作を文書化します。 ユーザがメソッドやクラスに組み込みの `help` メソッドを呼び出すと、Docstrings は
と表示されます。

Turn the comment in the following function into a docstring
and check that `help` displays it properly.

```python
def middle(a, b, c):
    # Return the middle value of three.
    # Assumes the values can actually be compared.
    values = [a, b, c]
    values.sort()
    return values[1]
```

::::::::::::::::: solution

## 解決策

```python
def middle(a, b, c):
    '''Return the middle value of three.
    Assumes the values can actually be compared.'''
    values = [a, b, c]
    values.sort()
    return values[1]
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## このコードをクリーンアップする

1. この短いプログラムを読んで、それが何をするかを予測してみてください。
2. それを実行します:あなたの予測はどのくらい正確でしたか?
3. プログラムをより読みやすくするためにリファクタリングします。
   動作が変更されていないことを確認するために、変更ごとに実行することを忘れないでください。
4. あなたの書き換えを隣人のものと比較しなさい。
   あなたも同じことをしたのですか。
   あなたは何を違っていましたか、そしてなぜですか?

```python
n = 10
s = 'et cetera'
print(s)
i = 0
while i < n:
    # print('at', j)
    new = ''
    for j in range(len(s)):
        left = j-1
        right = (j+1)%len(s)
        if s[left]==s[right]: new = new + '-'
        else: new = new + '*'
    s=''.join(new)
    print(s)
    i += 1
```

::::::::::::::::: solution

## 解決策

これが一つの解決策です

```python
def string_machine(input_string, iterations):
    """
    Takes input_string and generates a new string with -'s and *'s
    corresponding to characters that have identical adjacent characters
    or not, respectively.  Iterates through this procedure with the resultant
    strings for the supplied number of iterations.
    """
    print(input_string)
    input_string_length = len(input_string)
    old = input_string
    for i in range(iterations):
        new = ''
        # iterate through characters in previous string
        for j in range(input_string_length):
            left = j-1
            right = (j+1) % input_string_length  # ensure right index wraps around
            if old[left] == old[right]:
                new = new + '-'
            else:
                new = new + '*'
        print(new)
        # store new string as old
        old = new     

string_machine('et cetera', 10)
```

```output
et cetera
*****-***
----*-*--
---*---*-
--*-*-*-*
**-------
***-----*
--**---**
*****-***
----*-*--
---*---*-
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- あなたのコードで標準の Python スタイルに従ってください。
- 組み込みヘルプを提供するには、docstringsを使用してください。

::::::::::::::::::::::::::::::::::::::::::::::::::
