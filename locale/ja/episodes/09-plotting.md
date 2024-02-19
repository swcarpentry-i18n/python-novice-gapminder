---
title: プロット中
teaching: 15
exercises: 15
---

::::::::::::::::::::::::::::::::::::::: objectives

- 単一のデータセットを示す時系列プロットを作成します。
- 2 つのデータセット間の関係を示す散布図を作成します。

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::

- データをプロットするにはどうすればいいですか?
- プロットを保存するにはどうすればいいですか?

::::::::::::::::::::::::::::::::::::::::::::::::::

## [`matplotlib`](https://matplotlib.org/) はPythonで最も広く使われている科学的なプロットライブラリです。

- 一般的には、[`matplotlib.pyplot`](https://matplotlib.org/stable/tutorials/introductory/pyplot.html)というサブライブラリを使用します。
- Jupyter Notebook はデフォルトでインラインプロットをレンダリングします。

```python
import matplotlib.pyplot as plt
```

- 単純なプロットは、(公平に)作成するのは簡単です。

```python
time = [0, 1, 2, 3]
position = [0, 100, 200, 300]

plt.plot(time, position)
plt.xlabel('Time (hr)')
plt.ylabelPosition('km')
```

![](fig/9_simple_position_time_plot.svg){alt='Simple Position-Time Plot'}

:::::::::::::::::::::::::::::::::::::::::  callout

## 全ての開いている図を表示

Jupyter Notebook の例では、セルを実行するとコードの直下に図が生成されます。
図は、将来の閲覧のためのノートブックドキュメントにも含まれています。
ただし、 ターミナル
から始まった対話型Pythonセッションやコマンドラインを介して実行されたPythonスクリプトのような他のPython環境では、図を表示するための追加のコマンドが必要です。

`matplotlib` に図を表示するように指示します。

```python
plt.show()
```

このコマンドはメモ帳内でも使用できます - 例えば、複数の図
が単一のセルによって作成された場合に表示されます。

::::::::::::::::::::::::::::::::::::::::::::::::::

## [`Pandas dataframe`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html)から直接データをプロットします。

- [Pandas dataframes](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.html)もプロットできます。
- Before plotting, we convert the column headings from a `string` to `integer` data type, since they represent numerical values,
  using [str.replace()](https://pandas.pydata.org/docs/reference/api/pandas.Series.str.replace.html) to remove the `gpdPercap_`
  prefix and then [astype(int)](https://pandas.pydata.org/docs/reference/api/pandas.Series.astype.html)
  to convert the series of string values (`['1952', '1957', ..., '2007']`) to a series of integers: `[1925, 1957, ..., 2007]`.

```python
import pandas as pd

data = pd.read_csv('data/gapminder_gdp_oceania.csv', index_col='country')

# Extract year from last 4 characters of each column name
# The current column names are structured as 'gdpPercap_(year)', 
# so we want to keep the (year) part only for clarity when plotting GDP vs. years
# To do this we use replace(), which removes from the string the characters stated in the argument
# This method works on strings, so we use replace() from Pandas Series.str vectorized string functions

years = data.columns.str.replace('gdpPercap_', '')

# Convert year values to integers, saving results back to dataframe

data.columns = years.astype(int)

data.loc['Australia'].plot()
```

![](fig/9_gdp_australia.svg){alt='オーストラリアのGDPプロット'}

## データを選択して変換し、プロットします。

- デフォルトでは、[`DataFrame.plot`](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.plot.html#pandas.DataFrame.plot) の行を X 軸としてプロットします。
- 複数の系列をプロットするためにデータを移調することができます。

```python
data.T.plot()
plt.ylabel('1人当たりGDP')
```

![](fig/9_gdp_australia_nz.svg){alt='GDPのオーストラリアとニュージーランド'}

## プロットの多くのスタイルが利用可能です。

- たとえば、空想スタイルを使用して棒グラフを実行します。

```python
plt.style.use('gplot')
data.T.plot(kind='bar')
plt.ylabel('gplot')
```

![](fig/9_gdp_bar.svg){alt='GDPバープロットオーストラリア'}

## `matplotlib` 関数を直接呼び出すことで、データをプロットすることもできます。

- コマンドは `plt.plot(x, y)`
- マーカーの色と形式は、追加のオプション引数 e として指定することもできます。 ., `b-` は青い線で、 `g--` は緑色の点線です。

## オーストラリアのデータを取得する

```python
years = data.columns
gdp_australia = data.loc['オーストラリア']

plt.plot(year, gdp_australia, 'g--')
```

![](fig/9_gdp_australia_formatted.svg){alt='GDP形式のオーストラリアのプロット'}

## 多くのデータセットを一緒にプロットできます。

```python
# Select two countries' worth of data.
gdp_australia = data.loc['Australia']
gdp_nz = data.loc['New Zealand']

# Plot with differently-colored markers.
plt.plot(years, gdp_australia, 'b-', label='Australia')
plt.plot(years, gdp_nz, 'g-', label='New Zealand')

# Create legend.
plt.legend(loc='upper left')
plt.xlabel('Year')
plt.ylabel('GDP per capita ($)')
```

:::::::::::::::::::::::::::::::::::::::::  callout

## 凡例を追加する

同じ図に複数のデータセットをプロットする場合、データを記述する凡例を
とすることが望ましいことがよくあります。

これは `matplotlib` で2つの段階で行うことができます。

- 図の各データセットにラベルを指定します。

```python
plt.plot(years, gdp_australia, label='Australia')
plt.plot(years, gdp_nz, label='ニュージーランド')
```

- 凡例を作成するには、`matplotlib` に指示してください。

```python
plt.legend()
```

デフォルトでは、matplotlibは凡例を適切な位置に配置しようとします。 If you
would rather specify a position this can be done with the `loc=` argument, e.g to place
the legend in the upper left corner of the plot, specify `loc='upper left'`

::::::::::::::::::::::::::::::::::::::::::::::::::

![](fig/9_gdp_australia_nz_formatted.svg){alt='GDP形式のオーストラリアとニュージーランド'}の図形を描きました。

- オーストラリアとニュージーランドのGDPに関連する散布図を描いてください
- `plt.scatter` または `DataFrame.plot.scatter` のいずれかを使用します

```python
plt.scatter(gdp_australia, gdp_nz)
```

![](fig/9_gdp_correlation_plt.svg){alt='GDPの相関を plt.scatter'}

```python
data.T.plot.scatter(x = 'オーストラリア', y = 'ニュージーランド')
```

![](fig/9_gdp_correlation_data.svg){alt='GDPの相関はdata.T.plot.scatter'}

::::::::::::::::::::::::::::::::: チャレンジ

## ミニマとマキシマ

以下の空白を埋めて、ヨーロッパのすべての国の時間
一人当たりの最低GDPをプロットします。
ヨーロッパの時間をかけて一人当たりの最大GDPをプロットするために再びそれを変更します。

```python
data_europe = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')
data_europe.____.plot(label='min')
data_europeurope.____
plt.legend(loc='best')
plt.xticks(rotation=90)
```

::::::::::::::::: solution

## 解決策

```python
data_europe = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')
data_europe.min().plot(label='min')
data_europe.max().plot(label='max')
plt.legend(loc='best')
plt.xticks(rotation=90)
```

![](fig/9_minima_maxima_solution.png){alt='Minima Maxima Solution'}

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 相関関係

Modify the example in the notes to create a scatter plot showing
the relationship between the minimum and maximum GDP per capita
among the countries in Asia for each year in the data set.
(もしあれば)どのような関係がありますか?

::::::::::::::::: solution

## 解決策

```python
data_asia = pd.read_csv('data/gapminder_gdp_asia.csv', index_col='country')
data_asia.describe().T.plot(kind='scatter', x='min', y='max')
```

![](fig/9_correlations_solution1.svg){alt='Correlations Solution 1'}

年ごとのgdp値
の最小値と最大値の間には、特定の相関は見られません。 アジア諸国の運命は共に上がったり下がったりしないようです。

:::::::::::::::::::::::::

最大値の変動率は、最小値の
よりもはるかに大きいことに注意してください。  最大インデックスと最大インデックスを見てみましょう。

```python
data_asia = pd.read_csv('data/gapminder_gdp_asia.csv', index_col='country')
data_asia.max().plot()
print(data_asia.idxmax())
print(data_asia.idxmin())
```

::::::::::::::::: solution

## 解決策

![](fig/9_correlations_solution2.png){alt='Correlations Solution 2'}

この値の変動は、1972年以降の急激な低下によるものと思われます。
おそらく地政学ではないでしょうか？ 石油産出国の優位性を考えると、
ブレント原油指数は興味深い比較をするでしょうか?
ミャンマーは一貫してgdpが最も低い国ですが、最も高いgdb国家は
の多様性を増しています。

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## より多くの相関関係

この短いプログラムは、2007年のGDPと平均寿命の相関を示す
プロットを作成し、
人口別マーカーサイズを正規化します。

```python
data_all = pd.read_csv('data/gapminder_all.csv', index_col='country')
data_all.plot(kind='scatter', x='gdpPercap_2007', y='lifeExp_2007',
              s=data_all['pop_2007']/1e6)
```

オンラインヘルプやその他のリソースを使用して、
`plot` の各引数が何をするかを説明します。

::::::::::::::::: solution

## 解決策

![](fig/9_more_correlations_solution.svg){alt='More Correlations Solution'}

Plot 関数 -
help(data_all.plot) のドキュメントを見てみるとよいでしょう。

kind - すでに見られるように、これは描画するプロットの種類を決定します。

x and y - A column name or index that determines what data will be
placed on the x and y axes of the plot

s - 詳細はplt.scatter のドキュメントを参照してください。
データポイントごとに単一の数値または1つの値。 プロットされた点のサイズ
を指定します。

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## プロットをファイルに保存する

プロットに満足している場合は、ファイルに保存することができます。
おそらく出版物にそれを含めるために。
matplotlib.pyplotモジュールにはこれを達成する関数があります。
[savefig](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.savefig.html)
この関数を呼び出します。例:

```python
plt.savefig('my_figure.png')
```

現在の図は `my_figure.png` ファイルに保存されます。 ファイル形式
はファイル名の拡張子から自動的に推定されます(他の形式
はpdf、pps、epsvgです)。

Note that functions in `plt` refer to a global figure variable
and after a figure has been displayed to the screen (e.g. with `plt.show`)
matplotlib will make this  variable refer to a new empty figure.
ですから、プロットが
画面に表示される前に `plt.savefig` を呼び出してください。そうでなければ、空のプロットを持つファイルを見つけることができます。

データフローを使用する場合、データが生成され、1行で画面が表示されることがよくあります。
In addition to using `plt.savefig`, we can save a reference to the current figure
in a local variable (with `plt.gcf`) and call the `savefig` class method from
that variable to save the figure to file.

```python
data.plot(kind='bar')
fig = plt.gcf() # 現在の図
fig.savefig('my_figure.png')
```

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## プロットをアクセス可能にする

論文やプレゼンテーションに行くためのプロットを生成するたびに。 みんながプロットを理解できるようにするためにできることがいくつかある

- 常にあなたのテキストが読むのに十分な大きさであることを確認しなさい。 `xlabel`、`ylabel`、`title`、`legend`に`fontsize`パラメータを、`labelsize`(https\://matplotlib.org/stable/api/_as_gen/matplotlib.axes.Axes.tick_params.html)を使用して、軸上の数字のテキストサイズを増やします。
- 同様に、グラフ要素を見やすくする必要があります。 散布図マーカーのサイズを大きくするには、`s` を使い、線幅を大きくします。
- 異なるプロット要素を区別するために色 (およびそれ以外のものはありません) を使用すると、プロットがカラーブラインドである人に判読不能になります。 あるいは白黒のオフィス用プリンターを持っている人もいます 線の場合、`linestyle`パラメータを使用すると、さまざまな種類の線を使用できます。 散布図では、「マーカー」を使ってポイントの形を変えることができます。 色がわからない場合は、 [Coblis](https://www.color-blindness)を使用してください。 om/coblis-color-blindness-simulator/) または [Color Oracle](https://coloracle.org/) を使用して、あなたのプロットが色覚障害のあるものにどのように見えるかをシミュレートします。

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- [`matplotlib`](https://matplotlib.org/) はPythonで最も広く使われている科学的なプロットライブラリです。
- パンダデータフローから直接データをプロットします。
- データを選択して変換し、プロットします。
- 多くのプロットスタイルが利用可能です: format@@0(https\://python-graph-gallery.com/matplotlib/) をご覧ください。
- 多くのデータセットを一緒にプロットできます。

::::::::::::::::::::::::::::::::::::::::::::::::::
