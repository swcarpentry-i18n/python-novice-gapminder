---
title: データセット上にループする
teaching: 5
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- ファイルの集合に一致するグロビング式を読み書きすることができます。
- glob を使用してファイルのリストを作成します。
- ループを書き込むと、リスト内のファイル名が指定された場合に操作が実行されます。

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::

- 1つのコマンドで多くのデータセットを処理するにはどうすればよいですか?

::::::::::::::::::::::::::::::::::::::::::::::::::

## `まつ`を使って、名前のリストを指定したファイルを処理します。

- ファイル名は文字列です。
- リストは文字列を含めることができます。

```python
import panas pd
for filename in ['data/gapminder_gdp_africa.csv', 'data/gapminder_gdp_asia.csv']:
    data = pd.read_csv(filename, index_col='country')
    print(filename, data.min())
```

```output
data/gapminder_gdp_africa.csv gdpPercap_1952    298.846212
gdpPercap_1957    335.997115
gdpPercap_1962    355.203227
gdpPercap_1967    412.977514
⋮ ⋮ ⋮
gdpPercap_1997    312.188423
gdpPercap_2002    241.165877
gdpPercap_2007    277.551859
dtype: float64
data/gapminder_gdp_asia.csv gdpPercap_1952    331
gdpPercap_1957    350
gdpPercap_1962    388
gdpPercap_1967    349
⋮ ⋮ ⋮
gdpPercap_1997    415
gdpPercap_2002    611
gdpPercap_2007    944
dtype: float64
```

## [`glob.glob`](https://docs.python.org/3/library/glob.html#glob.glob) を使用して、名前がパターンに一致するファイルを見つけます。

- Unix では、"globbing" という用語は"一連のファイルにパターンをマッチさせる"ことを意味します。
- 最も一般的なパターンは次のとおりです。
  - `*` は "0文字以上に一致する" という意味です
  - `?` は「1文字に一致する」という意味です
- Python の標準ライブラリには、パターンマッチング機能を提供する [`glob`](https://docs.python.org/3/library/glob.html) モジュールが含まれています。
- [`glob`](https://docs.python.org/3/library/glob.html) モジュールにはファイルパターンにマッチする関数`glob`が含まれています。
- 例えば、`glob.glob('*.txt')`は、名前が`.txt`で終わる現在のディレクトリ
  内のすべてのファイルに一致します。
- 結果は文字列の(おそらく空の)リストです。

```python
import glob
print('all csv files in data directory:', glob.glob('data/*.csv'))
```

```output
すべてのcsvファイルデータディレクトリ内: ['data/gapminder_all.csv', 'data/gapminder_gdp_africa.csv', \
'data/gapminder_gdp_americas.csv', 'data/gapminder_gdp_asia.csv', 'data/gapminder_gdp_europe.csv', \
'data/gapminder_gdp_oceurania.csv']
```

```python
print('all PDB files:', glob.glob('*.pdb'))
```

```output
すべてのPDBファイル: []
```

## `glob` と `for` を使ってファイルのバッチを処理します。

- 単純なパターンが適切なデータを見つけられるように、ファイル名と一貫性のある
  一貫して体系的に保存されている場合に役立ちます。

```python
for filename in glob.glob('data/gapminder_*.csv'):
    data = pd.read_csv(filename)
    print(filename, data['gdpPercap_1952'].min())
```

```output
data/gapminder_all.csv 298.8462121
data/gapminder_gdp_africa.csv 298.8462121
data/gapminder_gdp_americas.csv 1397.717137
data/gapminder_gdp_asia.csv 331.0
data/gapminder_gdp_europe.csv 973.5331948
data/gapminder_gdp_csv 10039.595664
```

- これには、すべてのデータだけでなく、リージョンごとのデータも含まれます。
- データセット全体を除外するには、演習でより具体的なパターンを使用します。
- ただし、データセット全体の最小値は、データセットの最小値でもあることに注意してください。
  は正しさの良いチェックです。

::::::::::::::::::::::::::::::::: チャレンジ

## マッチングの決定

`glob.glob('data/*as*.csv')`とマッチしないファイルはどれですか？

1. `data/gapminder_gdp_africa.csv`
2. `data/gapminder_gdp_americas.csv`
3. `data/gapminder_gdp_asia.csv`

::::::::::::::::: solution

## 解決策

1は地球と一致しません。

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 最小ファイルサイズ

このプログラムを変更して、最も低いレコードを持つファイルのレコード数を
に出力するようにします。

```python
import glob
import pandas as pd
fewest = ____
for filename in glob.glob('data/*.csv'):
    dataframe = pd.____(filename)
    fewest = min(____, dataframe.shape[0])
print('smallest file has', fewest, 'records')
```

[`DataFrame.shape()` メソッド][shape-method]
は、データフレームの行数と列のタプルを返すことに注意してください。

::::::::::::::::: solution

## 解決策

```python
import glob
import pandas as pd
fewest = float('Inf')
for filename in glob.glob('data/*.csv'):
    dataframe = pd.read_csv(filename)
    fewest = min(fewest, dataframe.shape[0])
print('smallest file has', fewest, 'records')
```

変数`最小数`を、扱っている数字
より大きい数で初期化することを選択したかもしれません。 大きな数字でコードを再利用すれば問題になるかもしれません
Pythonは正の無限大を使うことができます。それはどんなに大きな数字であっても役に立ちます。
[`float` 関数][float-function] は他にどのような特殊文字列を認識しますか？

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## データの比較

地域データセットを読み込むプログラムを作成し、
単一のグラフで各地域の一人あたりの平均GDPをプロットします。

::::::::::::::::: solution

## 解決策

この解決法は、[string `split` method][split-method] から
に `region` をパス「data/gapminder\_gdp\_a\_specific\_region.csv」から抽出します。

```python
import glob
import pandas as pd
import matplotlib.pyplot as plt
fig, ax = plt.subplots(1,1)
for filename in glob.glob('data/gapminder_gdp*.csv'):
    dataframe = pd.read_csv(filename)
    # extract <region> from the filename, expected to be in the format 'data/gapminder_gdp_<region>.csv'.
    # we will split the string using the split method and `_` as our separator,
    # retrieve the last string in the list that split returns (`<region>.csv`), 
    # and then remove the `.csv` extension from that string.
    region = filename.split('_')[-1][:-4] 
    dataframe.mean().plot(ax=ax, label=region)
plt.legend()
plt.show()
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## ファイルパスの処理

[`pathlib` モジュール][pathlib-module] は、ファイル拡張子を持たないファイル名を返す
のようなファイルやパス操作のための有用な抽象化を提供します。 これは、ファイルや
ディレクトリをループさせるときに非常に便利です。 以下の例では、 `Path` オブジェクトを作成し、その属性を調べます。

```python
from pathlib import Path

p = Path("data/gapminder_gdp_africa.csv")
print(p.parent), print(p.stem), print(p.suffix)
```

```output
data
gapminder_gdp_Africa
.csv
```

**ヒント:** `dir()`
関数で`Path`オブジェクトで利用可能なすべての属性とメソッドをチェックすることができます！

::::::::::::::::::::::::::::::::::::::::::::::::::

[shape-method]: https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.shape.html

[float-function]: https://docs.python.org/3/library/functions.html#float

[split-method]: https://docs.python.org/3/library/stdtypes.html#str.split

[pathlib-module]: https://docs.python.org/3/library/pathlib.html

:::::::::::::::::::::::::::::::::::::::: keypoints

- `まつ`を使って、名前のリストを指定したファイルを処理します。
- `glob.glob` を使用すると、名前がパターンに一致するファイルを見つけることができます。
- `glob` と `for` を使ってファイルのバッチを処理します。

::::::::::::::::::::::::::::::::::::::::::::::::::
