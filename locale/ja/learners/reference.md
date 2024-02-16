---
title: 参照
---

## 参照

## format@@0(episodes/01-run-quit.md)

- Python ファイルは `.py` 拡張子を持っています。
- テキストファイルや[Jupyter Notebook][jupyter] に書き込めます。
  - Jupyter notebook は `.ipynb` という拡張子を持っています。
  - Jupyter notebook は [Anaconda](https://docs.continuum.io/anaconda/install) から、またはコマンドラインで `$ jupyter notebook` を入力して開くことができます。
    - Markdown と HTML は、コードを文書化するためにマークダウンセルに許可されています。

## format@@0(episodes/02-variables.md)

- 変数は `=` を使用して保存されます。
  - 文字列は引用符`'...'`で定義されます。
  - 整数と浮動小数点数は引用符なしで定義されます。
- 変数には、文字、数字、アンダースコアを含めることができます。
  - 数字で開始することはできません。
  - アンダースコアで始まる変数は避けるべきです。
- 値をテキストとして表示するには、`print(...)` を使用します。
- 文字列のインデックスを使用できます。
  - インデックスは0から始まります。
  - 変数名の後に、角括弧`[position]`で位置を指定します。
  - `[start:stop]`を使ってスライスを取りましょう。 これは、元の文字列の一部をコピーします。
    - `start` は最初の要素のインデックスです。
    - `stop` は最後の要素の後の要素のインデックスです。
- 変数または文字列の長さを求めるには、`len(...)`を使います。

## format@@0(episodes/03-types-conversion.md)

- 各値には型があります。 これにより、何ができるかが制御されます。
  - `int` は整数を表します
  - `float` は浮動小数点数を表します。
  - `str`は文字列を表します。
- 変数型を決定するには、括弧内に変数名を含む組み込み関数 `type(...)` を使用します。
- 文字列の変更:
  - 文字列を連結するには `+` を使用します。
  - `*`で文字列を繰り返します。
  - 数値と文字列は別のものには追加できません。
    - 文字列を整数に変換する: `int(...)` 。
    - 整数を文字列に変換する: `str(...)` 。

## format@@0(episodes/04-built-in.md)

- コメントを追加するには、実行されないものの前に `#` を置いてください。
- 一般的に使用される組み込み関数:
  - `min()` は最小値を見つけます。
  - `max()`は最大値を検索します。
  - `round()` は浮動小数点数を四捨五入します。
  - `help()` は括弧内の関数のドキュメントを表示します。
    - ヘルプを得る他の方法としては、Jupyter Notebookで`shift`を押しながら`tab`を押します。

## [Libraries](episodes/06-libraries.md)

- ライブラリのインポート:
  - ライブラリをロードするには `import ...` を使います。
  - `module_name.thing_name` を使用して、このライブラリを参照してください。
    - `.`は'の一部'を示します。
- ライブラリから特定のアイテムをインポートするには: `from ... import ...`
- エイリアスを使用してライブラリをインポートするには: `import ... as ...`
- 数学ライブラリのインポート: `import math`
  - モジュール名の項目を参照する例: `math.cos(math.pi)` 。
- プロットライブラリを別名としてインポートします: `import matplotlib as mpl`

## format@@0(episodes/07-reading-tabular.md)

- pandas ライブラリを使用して、表形式のデータに関する統計を行います。 `import pandas pd` で読み込みます。
  - csv で読み込むには: `pd.read_csv()` 括弧内のパス名を含む。
    - カラムの値を指定するには、行見出しとして使用する必要があります: `pd. ead_csv('path', index_col='column name')` パスと列名を関連する値に置き換える必要があります。
- DataFrameに関する詳細な情報を得るには、`DataFrame.info`を使用します。`DataFrame` をDataFrameの変数名に置き換えます。
- 列名を表示するには、`DataFrame.columns` を使用します。
- DataFrame.Tを移調するには、`DataFrame.T`を使用します。
- データに関するサマリ統計を取得するには、`DataFrame.describe`を使用してください。

## format@@0(episodes/08-data-frames.md)

- `[i,j]` を使用してデータを選択
  - エントリの位置で選択するには、`DataFrame.iloc[..., ...]`
    - これは、最終的な指数以外のすべてのものが含まれています。
  - エントリラベルで選択するには、`DataFrame.loc[..., ...]`
    - ラベルを一覧表示することで複数の行または列を選択できます。
    - これは両方の目的に含まれています。
  - すべての行または列を選択するには `:` を使用します。
- TrueとFalseを使用して値に基づいてデータを選択することもできます。 これはブールマスクです。
  - `mask = subset > 10000`
  - これを使用して値を選択できます。
- select-apply-combin操作を使用するには、 `data.apply(lambda x: x > x. `mean()\`は、ユーザーがxに適用したい任意の操作になります。

## [Plotting](エピソード/09-ploting.md)

- 最も広く使用されているプロットライブラリは `matplotlib` です。
  - 通常は、`import matplotlib.pyplot を plt` としてインポートします。
  - 図を描くには、 `plt.plot(time, position)` を使います。
  - 凡例を作成するには `plt.legend(['label1', 'label2'], loc='upper left')` を使います。
    - また、 `plt.plot(time, position, label='label')` を使って、プロット文内でラベルを定義することもできます。 凡例を表示するには、 `plt.legend()` を使用します。
  - x軸とy軸に`plt.xlabel('label')`と`plt.ylabel('label')`を使用します。
- Pandas DataFrame は、 `DataFrame.plot()` を使用してプロットすることができます。 DataFrameで使用できる操作は、プロット中に適用できます。
  - 棒グラフをプロットする `data.plot(kind='bar')`

```python
import matplotlib.puplot as plot
plt.plot(time, position, label='label')
plt.xlabel('x axis label')
plt.ylabel('y axis label')
plt.legend()
```

## [Lists](episodes/11-lists.md)

- `[...]`内で定義され、`,`で区切られています。
  - `[]`を使えば、空のリストを作成できます。
- `len(...)`を使って、リスト内の値の数を決めることができます。
- 以前のレッスンと同様にインデックスを作成できます。
  - インデックス作成は、 `list_name[0] = newvalue` の値を再割り当てするために使用できます。
- リストに項目を追加するには、 `list_name.append()` を使用し、括弧内に項目を追加します。
- 2つのリストを組み合わせるには、 `list_name_1.extend(list_name_2)` を使います。
- リストから項目を削除するには、`del list_name[index] ` を使用します。

## format@@0(episodes/12-for-loops.md)

- forループは、`for number in [1, 2, 3]:`で始まり、次の行をインデントします。
  - `[1, 2, 3]` はコレクションとみなされます。
  - `number` はループ変数です。
  - コレクションに続くアクションが本文です。
- 連続した数字を繰り返すには、 `range(start, end)` を使います。

```python
for number in range(0,5):
    print(number)
```

## [Conditionals](episode / 13conditionals.md)

- `if variable conditional value:`を使用して、ループと同じように定義します。
  - 例えば、 `if variable > 5:` です。
- 追加のテストには`elif:`を使います。
- if文が真でないときは、`else:`を使ってください。
- `and`または`or`を使って複数の条件を組み合わせることができます。
- for ループと組み合わせてよく使用されます。
- 使用可能な条件
  - `==`は等しくなります。
  - `>=` 以上。
  - `<=` 以下。
  - `>` より大きい。
  - `<`より小さい。

```python
for m in [3, 6, 7, 2, 8]:
    if m > 5:
        print(m, 'is large')
    elif m == 5:
        print(m, 'is 5')
    else:
        print(m, 'is small')
```

## format@@0(episodes/14-looping-data-sets.md)

- for ループを使ってください: `for filename in [file1, file2]:`
- パターンを使用して一連のファイルを見つけるには、 `glob.glob` を使用します。
  - `import glob` を使ってインポートする必要があります。
  - `*` は「ゼロ以上の文字に一致する」を示します
  - `?` は「一致する文字」を示します。
    - 例: `glob.glob(*.txt)` はカレントディレクトリに`.txt`で終わるすべてのファイルを検索します。
- `for filename in glob.glob.glob(*.txt):` を使って、これらを組み合わせましょう。

```python
for filename in glob.glob(*.txt):
  data = pd.read_csv(filename)
```

## format@@0(episodes/16-writing-functions.md)

- `def function_name(parameters):` を使って関数を定義します。 関数を実行するときに使用する変数に `parameters` を置き換えます。
- `function_name(parameters)` を使用して実行します。
- 呼び出し元に結果を返すには、関数で `return ...` を使います。

```python
def add_numbers(a, b):
    result = a + b
    return result

add_numbers(1, 4)
```

## format@@0(episodes/17-scope.md)

- ローカル変数は関数内で定義され、その関数内でのみ見ることができます。
- グローバル変数は関数の外側で定義され、定義後の任意の場所で見ることができます。

## format@@0(episodes/18-style.md)

- コードを文書化します。
- 明確で意味のある変数名を使用してください。
- コードを設定するときは、format@@0(https\://www\.python.org/dev/peps/pep-0008)に従ってください。
- アサーションを使用して内部エラーを確認します。
- ヘルプを提供するには、docstringsを使用してください。

## Glossary

引数
: 関数に渡される値。

配列
: 同じ型の要素を保持するコンテナ。

Boolean
: `True` と `False` で構成されたオブジェクト。

DataFrame
: Pandasが表; 系列のコレクションを表す方法。

要素
: リストまたは配列の項目。 文字列の場合、これらは個々の文字です。

関数
: 他の場所で呼び出して再利用できるコードブロック。

グローバル変数
: 関数の外部で使用できる変数。

インデックス
: 指定された要素の位置。

Jupyter Notebook
: コードとマークダウンの組み合わせを可能にするインタラクティブなコーディング環境。

ライブラリ
: 他のプログラムで使用される関数を含むファイルの集合。

ローカル変数
: 関数の内部でのみ使用できる変数。

マスク
: 別のオブジェクトからデータを選択するために使用されるブール型オブジェクト。

メソッド
: 特定のオブジェクトに関連付けられたアクション。 `object.method` を使用して呼び出されます。

モジュール
: 他のプログラムで使用されている関数を含むライブラリ内のファイル。

パラメータ
: 関数の実行時に使用する変数。

シリーズ
: 列を表すパンダデータ構造。

Substring
: 文字列の一部。

変数
: 値の名前。
