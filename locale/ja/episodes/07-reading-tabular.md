---
title: データフレームへの表形式データの読み込み中
teaching: 10
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- パンダライブラリをインポートします。
- Pandasを使用して単純なCSVデータセットをロードします。
- パンダデータフレームに関する基本情報を取得します。

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::

- 表形式のデータはどのように読み取れますか?

::::::::::::::::::::::::::::::::::::::::::::::::::

## 表形式のデータに関する統計を行うには、Pandasライブラリを使用します。

- [Pandas](https://pandas.pydata.org/) は統計のために広く使われているPythonライブラリで、特に表形式のデータです。
- Rのデータフローから多くの機能を生成します。
  - 列名が
    で、異なるデータ型を持つ可能性がある2次元テーブル。
- `import pandas as pd` で Pandas をロードします。 エイリアスの`pd`は、コード内でパンダのライブラリを参照するために一般的に使用されます。
- `pd.read_csv` でカンマ区切りの値(CSV)データファイルを読み込みます。
  - 引数は、読み込まれるファイルの名前です。
  - 変数に割り当てられるデータフローを返します。

```python
import pandas pd

data_oceania = pd.read_csv('data/gapminder_gdp_occsv')
print(data_oceania)
```

```output
       country  gdpPercap_1952  gdpPercap_1957  gdpPercap_1962  \
0    Australia     10039.59564     10949.64959     12217.22686
1  New Zealand     10556.57566     12247.39532     13175.67800

   gdpPercap_1967  gdpPercap_1972  gdpPercap_1977  gdpPercap_1982  \
0     14526.12465     16788.62948     18334.19751     19477.00928
1     14463.91893     16046.03728     16233.71770     17632.41040

   gdpPercap_1987  gdpPercap_1992  gdpPercap_1997  gdpPercap_2002  \
0     21888.88903     23424.76683     26997.93657     30687.75473
1     19007.19129     18363.32494     21050.41377     23189.80135

   gdpPercap_2007
0     34435.36744
1     25185.00911
```

- データフローの列は観測された変数で、行は観測結果です。
- Pandasはバックスラッシュ`\`を使用して、出力が幅が広すぎて画面に合わない場合にラップされた行を表示します。
- 記述的なデータフレーム名を使用すると、複数のデータフレームを区別するのに役立ちます。そのため、誤ってデータフレームを上書きしたり、間違ったデータから読み取ったりすることはありません。

:::::::::::::::::::::::::::::::::::::::::  callout

## ファイルが見つかりません

私たちのレッスンでは、データファイルを `data` サブディレクトリ
に格納しています。このため、ファイルへのパスは `data/gapminder_gdp_occsv` です。
If you forget to include `data/`,
or if you include it but your copy of the file is somewhere else,
you will get a [runtime error](04-built-in.md)
that ends with a line like this:

```error
FileNotFoundError: [Errno 2] そのようなファイルまたはディレクトリがありません: 'data/gapminder_gdp_occsv'
```

::::::::::::::::::::::::::::::::::::::::::::::::::

## 行の見出しとして使用する列の値を指定するには、 `index_col` を使用します。

- 行の見出しは数字（この場合は0と1）です。
- 本当に国別にインデックスを作成します。
- カラムの名前を `index_col` パラメータとして `read_csv` に渡します。
- data_oceania_countryという名前は、データに含まれる領域(`oceania`)とインデックス(`country`)を示します。

```python
data_oceania_country = pd.read_csv('data/gapminder_gdp_oceania.csv', index_col='country')
print(data_oceania_country)
```

```output
             gdpPercap_1952  gdpPercap_1957  gdpPercap_1962  gdpPercap_1967  \
country
Australia       10039.59564     10949.64959     12217.22686     14526.12465
New Zealand     10556.57566     12247.39532     13175.67800     14463.91893

             gdpPercap_1972  gdpPercap_1977  gdpPercap_1982  gdpPercap_1987  \
country
Australia       16788.62948     18334.19751     19477.00928     21888.88903
New Zealand     16046.03728     16233.71770     17632.41040     19007.19129

             gdpPercap_1992  gdpPercap_1997  gdpPercap_2002  gdpPercap_2007
country
Australia       23424.76683     26997.93657     30687.75473     34435.36744
New Zealand     18363.32494     21050.41377     23189.80135     25185.00911
```

## `DataFrame.info()`メソッドを使用して、データフローの詳細を調べます。

```python
data_oceania_country.info()
```

```output
<class 'pandas.core.frame.DataFrame'>
Index: 2 entries, Australia to New Zealand
Data columns (total 12 columns):
gdpPercap_1952    2 non-null float64
gdpPercap_1957    2 non-null float64
gdpPercap_1962    2 non-null float64
gdpPercap_1967    2 non-null float64
gdpPercap_1972    2 non-null float64
gdpPercap_1977    2 non-null float64
gdpPercap_1982    2 non-null float64
gdpPercap_1987    2 non-null float64
gdpPercap_1992    2 non-null float64
gdpPercap_1997    2 non-null float64
gdpPercap_2002    2 non-null float64
gdpPercap_2007    2 non-null float64
dtypes: float64(12)
memory usage: 208.0+ bytes
```

- これは「DataFrame」です
- `オーストラリア'`と\`ニュージーランド'という2つの行
- 12 列には、それぞれ 2 つの実際の 64 ビット浮動小数点値があります。
  - 欠落している観察記録を表すために使用される null 値については後で説明します。
- 208バイトのメモリを使用します。

## 変数`DataFrame.columns`は、データフローの列に関する情報を格納します。

- これはデータ、_not_ メソッドであることに注意してください。  （括弧はありません）
  - `math.pi`のように。
  - ですから、`()`を呼び出そうとしないでください。
- _メンバー変数_または_メンバー_と呼ばれます。

```python
print(data_oceania_country.columns)
```

```output
Index(['gdpPercap_1952', 'gdpPercap_1957', 'gdpPercap_1962', 'gdpPercap_1967',
       'gdpPercap_1972', 'gdpPercap_1977', 'gdpPercap_1982', 'gdpPercap_1987',
       'gdpPercap_1992', 'gdpPercap_1997', 'gdpPercap_2002', 'gdpPercap_2007'],
      dtype='object')
```

## データフローを移調するには、`DataFrame.T` を使用します。

- 列を行として扱いたい場合とその逆を扱いたい場合があります。
- Transpose (`.T`と書かれた) はデータをコピーせず、プログラムのビューを変更するだけです。
- `columns` と同様に、メンバ変数です。

```python
print(data_oceania_country.T)
```

```output
country           Australia  New Zealand
gdpPercap_1952  10039.59564  10556.57566
gdpPercap_1957  10949.64959  12247.39532
gdpPercap_1962  12217.22686  13175.67800
gdpPercap_1967  14526.12465  14463.91893
gdpPercap_1972  16788.62948  16046.03728
gdpPercap_1977  18334.19751  16233.71770
gdpPercap_1982  19477.00928  17632.41040
gdpPercap_1987  21888.88903  19007.19129
gdpPercap_1992  23424.76683  18363.32494
gdpPercap_1997  26997.93657  21050.41377
gdpPercap_2002  30687.75473  23189.80135
gdpPercap_2007  34435.36744  25185.00911
```

## データに関するサマリ統計を取得するには、`DataFrame.describe()`を使用してください。

`DataFrame.describe()` は、数値データを持つ列のみの要約統計量を取得します。
引数`include='all'`を使用しない限り、他のカラムはすべて無視されます。

```python
print(data_oceania_country.describe())
```

```output
       gdpPercap_1952  gdpPercap_1957  gdpPercap_1962  gdpPercap_1967  \
count        2.000000        2.000000        2.000000        2.000000
mean     10298.085650    11598.522455    12696.452430    14495.021790
std        365.560078      917.644806      677.727301       43.986086
min      10039.595640    10949.649590    12217.226860    14463.918930
25%      10168.840645    11274.086022    12456.839645    14479.470360
50%      10298.085650    11598.522455    12696.452430    14495.021790
75%      10427.330655    11922.958888    12936.065215    14510.573220
max      10556.575660    12247.395320    13175.678000    14526.124650

       gdpPercap_1972  gdpPercap_1977  gdpPercap_1982  gdpPercap_1987  \
count         2.00000        2.000000        2.000000        2.000000
mean      16417.33338    17283.957605    18554.709840    20448.040160
std         525.09198     1485.263517     1304.328377     2037.668013
min       16046.03728    16233.717700    17632.410400    19007.191290
25%       16231.68533    16758.837652    18093.560120    19727.615725
50%       16417.33338    17283.957605    18554.709840    20448.040160
75%       16602.98143    17809.077557    19015.859560    21168.464595
max       16788.62948    18334.197510    19477.009280    21888.889030

       gdpPercap_1992  gdpPercap_1997  gdpPercap_2002  gdpPercap_2007
count        2.000000        2.000000        2.000000        2.000000
mean     20894.045885    24024.175170    26938.778040    29810.188275
std       3578.979883     4205.533703     5301.853680     6540.991104
min      18363.324940    21050.413770    23189.801350    25185.009110
25%      19628.685413    22537.294470    25064.289695    27497.598692
50%      20894.045885    24024.175170    26938.778040    29810.188275
75%      22159.406358    25511.055870    28813.266385    32122.777857
max      23424.766830    26997.936570    30687.754730    34435.367440
```

- 2つのレコードだけでは特に有用ではありませんが、何千ものレコードがある場合に非常に役立ちます。

::::::::::::::::::::::::::::::::: チャレンジ

## 他のデータの読み取り

Read the data in `gapminder_gdp_americas.csv`
(which should be in the same directory as `gapminder_gdp_oceania.csv`)
into a variable called `data_americas`
and display its summary statistics.

::::::::::::::::: solution

## 解決策

CSV で読み込むには、 `pd.read_csv` を使い、ファイル名 `'data/gapminder_gdp_americas.csv'` を渡します。
また、国ごとにインデックスを作成するために、 `index_col` パラメータに `'country'` というカラム名を再度渡します。
要約統計量は `DataFrame.describe()` メソッドで表示できます。

```python
data_americas = pd.read_csv('data/gapminder_gdp_americas.csv', index_col='country')
data_americas.describe()
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## データの検査

アメリカ大陸のデータを読み取った後、
`help(data_americas.head)` と `help(data_americas.tail)`
を使用して、`DataFrame.head` と `DataFrame.tail` の動作を確認します。

1. どのメソッドの呼び出しでこのデータの最初の3行を表示しますか？
2. このデータの最後の3列を表示するメソッドの呼び出しは何ですか？
   (ヒント:データのビューを変更する必要がある場合があります。

::::::::::::::::: solution

## 解決策

1. DataFrameの始まりを見ることができる`data_americas`
   を実行することで、 `data_americas` の最初の5行を確認することができます。 `data_americas.head()`への呼び出しでパラメータ`n`を指定することで、
   の行数を指定することができます。
   最初の3行を表示するには、次を実行します。

```python
data_americas.head(n=3)
```

```output
          continent  gdpPercap_1952  gdpPercap_1957  gdpPercap_1962  \
country
Argentina  Americas     5911.315053     6856.856212     7133.166023
Bolivia    Americas     2677.326347     2127.686326     2180.972546
Brazil     Americas     2108.944355     2487.365989     3336.585802

          gdpPercap_1967  gdpPercap_1972  gdpPercap_1977  gdpPercap_1982  \
country
Argentina     8052.953021     9443.038526    10079.026740     8997.897412
Bolivia       2586.886053     2980.331339     3548.097832     3156.510452
Brazil        3429.864357     4985.711467     6660.118654     7030.835878

           gdpPercap_1987  gdpPercap_1992  gdpPercap_1997  gdpPercap_2002  \
country
Argentina     9139.671389     9308.418710    10967.281950     8797.640716
Bolivia       2753.691490     2961.699694     3326.143191     3413.262690
Brazil        7807.095818     6950.283021     7957.980824     8131.212843

           gdpPercap_2007
country
Argentina    12779.379640
Bolivia       3822.137084
Brazil        9065.800825
```

2. `data_americas` の最後の3行を調べるには、
   `americas.tail(n=3)`というコマンドを使います。 しかし、ここでは最後の3つの列を
   見てみたいので、ビューを変更し、`tail()`を使用します。 これを行うには、
   行と列が切り替わる新しいDataFrameを作成します。

```python
americas_flipped = data_americas.T
```

`americas_flipped`の最後の3つの列
を見て、`americas`の最後の3つの列を見ることができます。

```python
americas_flipped.tail(n=3)
```

```output
country        Argentina  Bolivia   Brazil   Canada    Chile Colombia  \
gdpPercap_1997   10967.3  3326.14  7957.98  28954.9  10118.1  6117.36
gdpPercap_2002   8797.64  3413.26  8131.21    33329  10778.8  5755.26
gdpPercap_2007   12779.4  3822.14   9065.8  36319.2  13171.6  7006.58

country        Costa Rica     Cuba Dominican Republic  Ecuador    ...     \
gdpPercap_1997    6677.05  5431.99             3614.1  7429.46    ...
gdpPercap_2002    7723.45  6340.65            4563.81  5773.04    ...
gdpPercap_2007    9645.06   8948.1            6025.37  6873.26    ...

country          Mexico Nicaragua   Panama Paraguay     Peru Puerto Rico  \
gdpPercap_1997   9767.3   2253.02  7113.69   4247.4  5838.35     16999.4
gdpPercap_2002  10742.4   2474.55  7356.03  3783.67  5909.02     18855.6
gdpPercap_2007  11977.6   2749.32  9809.19  4172.84  7408.91     19328.7

country        Trinidad and Tobago United States  Uruguay Venezuela
gdpPercap_1997             8792.57       35767.4  9230.24   10165.5
gdpPercap_2002             11460.6       39097.1     7727   8605.05
gdpPercap_2007             18008.5       42951.7  10611.5   11415.8
```

これは私たちが望むデータを示していますが、3行ではなく3列を表示することを好むかもしれません。
を反転できるようにします:

```python
americas_flipped.tail(n=3)。    
```

**注意：** コマンドを「チェーン」することで、上記のコードを1行で実行できます。

```python
data_Americas.T.tail(n=3).T
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 他のディレクトリ内のファイルを読み込み中

The data for your current project is stored in a file called `microbes.csv`,
which is located in a folder called `field_data`.
`thesis`と呼ばれる兄弟フォルダの`analysis.ipynb`
というノートブックで解析を行っています:

```output
your_home_directory
+-- field_data/
| +-- microbes.csv
+-- thesis/
    +-- analysis.ipynb
```

`analysis.ipynb`で`microbes.csv`を読み取るには、どのような値を`read_csv`に渡すべきですか？

::::::::::::::::: solution

## 解決策

`pd.read_csv` を呼び出す際に、関心のあるファイルへのパスを指定する必要があります。 We first need to 'jump' out of
the folder `thesis` using '../' and then into the folder `field_data` using 'field_data/'. 次に、filename \`microbes.csv を指定します。
結果は以下のとおりです。

```python
data_microbes = pd.read_csv('../field_data/microbes.csv')
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## データの書き込み

Pandasはファイルからデータを読み込むための`read_csv`関数と同様に、データをファイルに書き込むための`to_csv`関数を提供します。
ファイルから読み取ることについて学んだことを適用すると、
は `processed.csv` という名前のファイルにデータフレームを書き込みます。
`to_csv` の使い方については、 `help` を使うことができます。

::::::::::::::::: solution

## 解決策

`processed.csv`というファイルにDataFrame`data_americas`を書き込むには、次のコマンドを実行します。

```python
data_americas.to_csv('processed.csv')
```

`read_csv` または `to_csv` のヘルプについては、次のように実行できます。

```python
help(data_americas.to_csv)
help(pd.read_csv)
```

`help(to_csv)` または `help(pd.to_csv)` はエラーを投げます。 これは、`to_csv` がグローバルパンダ関数ではなく、DataFrameのメンバ関数である
が原因です。 これは、DataFrame
のインスタンス上でのみ呼び出すことができることを意味します。例えば、 `data_americas.to_csv` や `data_occsv`

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- 表形式のデータから基本的な統計を取得するには、Pandasライブラリを使用します。
- 行の見出しとして使用する列の値を指定するには、 `index_col` を使用します。
- `DataFrame.info` を使用して、データフローについての詳細を調べます。
- 変数`DataFrame.columns`は、データフローの列に関する情報を格納します。
- データフローを移調するには、`DataFrame.T` を使用します。
- データに関するサマリ統計を取得するには、`DataFrame.describe` を使用してください。

::::::::::::::::::::::::::::::::::::::::::::::::::
