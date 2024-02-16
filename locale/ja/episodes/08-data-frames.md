---
title: Pandas DataFrames
teaching: 15
exercises: 15
---

::::::::::::::::::::::::::::::::::::::: objectives

- パンダデータフローから個々の値を選択します。
- データフローから行全体または列全体を選択します。
- 単一の操作でデータフローから行と列の両方のサブセットを選択します。
- 単一のブール値基準でデータフローのサブセットを選択します。

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::

- 表形式データの統計分析を行うにはどうすればよいですか?

::::::::::::::::::::::::::::::::::::::::::::::::::

## パンダデータフレーム/シリーズについての注意

A [DataFrame][pandas-dataframe] is a collection of [Series][pandas-series];
The DataFrame is the way Pandas represents a table, and Series is the data-structure
Pandas use to represent a column.

Pandas is built on top of the [Numpy][numpy] library, which in practice means that
most of the methods defined for Numpy Arrays apply to Pandas Series/DataFrames.

What makes Pandas so attractive is the powerful interface to access individual records
of the table, proper handling of missing values, and relational-databases operations
between DataFrames.

## 値の選択

DataFrameの位置`[i,j]`で値にアクセスするには、2つのオプションがあります。 使用中の「i」の意味は、
によって異なります。
Remember that a DataFrame provides an _index_ as a way to identify the rows of the table;
a row, then, has a _position_ inside the table as well as a _label_, which
uniquely identifies its _entry_ in the DataFrame.

## `DataFrame.iloc[..., ...]` を使用して、値を選択します (エントリ)

- 文字列中の文字選択の2Dバージョンと同様に数値インデックスで位置を指定することができます。

```python
import pandas pd
data = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')
print(data.iloc[0, 0])
```

```output
1601.056136
```

## `DataFrame.loc[..., ...]` を使用して、その（エントリ）ラベルで値を選択します。

- 行または列名で場所を指定できます。

```python
print(data.loc["Albania", "gdpPercap_1952"])
```

```output
1601.056136
```

## すべての列またはすべての行を意味するには、単独で `:` を使用します。

- Pythonの通常のスライス表記と同じように。

```python
print(data.loc["Albania", :])
```

```output
gdpPercap_1952    1601.056136
gdpPercap_1957    1942.284244
gdpPercap_1962    2312.888958
gdpPercap_1967    2760.196931
gdpPercap_1972    3313.422188
gdpPercap_1977    3533.003910
gdpPercap_1982    3630.880722
gdpPercap_1987    3738.932735
gdpPercap_1992    2497.437901
gdpPercap_1997    3193.054604
gdpPercap_2002    4604.211737
gdpPercap_2007    5937.029526
Name: Albania, dtype: float64
```

- `data.loc["Albania"]`を（2番目のインデックスなしで）出力します。

```python
print(data.loc[:, "gdpPercap_1952"])
```

```output
country
Albania                    1601.056136
Austria                    6137.076492
Belgium                    8343.105127
⋮ ⋮ ⋮
Switzerland               14734.232750
Turkey                     1969.100980
United Kingdom             9979.508487
Name: gdpPercap_1952, dtype: float64
```

- `data["gdpPercap_1952"]` を同じ結果に出力します。
- `data.gdpPercap_1952` も同じ結果を出力します（メソッドでは `.` 表記と簡単に混同されるため、お勧めしません）

## `DataFrame.loc` と名前付きスライスを使用して、複数の列または行を選択します。

```python
print(data.loc['イタリア':'ポーランド', 'gdpPercap_1962':'gdpPercap_1972'])
```

```output
             gdpPercap_1962  gdpPercap_1967  gdpPercap_1972
country
Italy           8243.582340    10022.401310    12269.273780
Montenegro      4649.593785     5907.850937     7778.414017
Netherlands    12790.849560    15363.251360    18794.745670
Norway         13450.401510    16361.876470    18965.055510
Poland          5338.752143     6557.152776     8006.506993
```

In the above code, we discover that **slicing using `loc` is inclusive at both
ends**, which differs from **slicing using `iloc`**, where slicing indicates
everything up to but not including the final index.

## スライスの結果は、さらなる操作で使用できます。

- 通常、スライスを印刷するだけではありません。
- すべての統計演算子は、データフレーム
  全体で動作しますが、スライスでも同じように動作します。
- 例えば、スライスの最大値を計算します。

```python
print(data.loc['イタリア':'ポーランド', 'gdpPercap_1962':'gdpPercap_1972'].max())
```

```output
gdpPercap_1962 13450.40151
gdpPercap_1967 16361.8867
gdpPercap_1972 18965.0551
dtype: float64
```

```python
print(data.loc['イタリア':'ポーランド', 'gdpPercap_1962':'gdpPercap_1972'].min())
```

```output
gdpPercap_1962 4649.593785
gdpPercap_1967 5907.850937
gdpPercap_1972 7778.414017
dtype: float64
```

## 比較を使用して、値に基づいてデータを選択します。

- 比較は要素ごとに適用されます。
- `True` と `False` に似た形のデータフレームを返します。

```python
# Use a subset of data to keep output readable.
subset = data.loc['Italy':'Poland', 'gdpPercap_1962':'gdpPercap_1972']
print('Subset of data:\n', subset)

# Which values were greater than 10000 ?
print('\nWhere are values large?\n', subset > 10000)
```

```output
Subset of data:
             gdpPercap_1962  gdpPercap_1967  gdpPercap_1972
country
Italy           8243.582340    10022.401310    12269.273780
Montenegro      4649.593785     5907.850937     7778.414017
Netherlands    12790.849560    15363.251360    18794.745670
Norway         13450.401510    16361.876470    18965.055510
Poland          5338.752143     6557.152776     8006.506993

Where are values large?
            gdpPercap_1962 gdpPercap_1967 gdpPercap_1972
country
Italy                False           True           True
Montenegro           False          False          False
Netherlands           True           True           True
Norway                True           True           True
Poland               False          False          False
```

## ブールマスクを使用して値またはNaNを選択します。

- Booleanのフルフレームは、使用方法から_マスク_と呼ばれることがあります。

```python
mask = subset > 10000
print(subset[mask])
```

```output
             gdpPercap_1962  gdpPercap_1967  gdpPercap_1972
country
Italy                   NaN     10022.40131     12269.27378
Montenegro              NaN             NaN             NaN
Netherlands     12790.84956     15363.25136     18794.74567
Norway          13450.40151     16361.87647     18965.05551
Poland                  NaN             NaN             NaN
```

- mask が true の場所で値を取得し、NaN (数値ではない) が false の場所で値を取得します。
- NaN は最大、最小、平均などの操作によって無視されるので便利です。

```python
print(subset[subset > 10000].describe())
```

```output
       gdpPercap_1962  gdpPercap_1967  gdpPercap_1972
count        2.000000        3.000000        3.000000
mean     13120.625535    13915.843047    16676.358320
std        466.373656     3408.589070     3817.597015
min      12790.849560    10022.401310    12269.273780
25%      12955.737547    12692.826335    15532.009725
50%      13120.625535    15363.251360    18794.745670
75%      13285.513523    15862.563915    18879.900590
max      13450.401510    16361.876470    18965.055510
```

## グループ化: 分割適用-結合

::::::::::::::::::::::::::::::::::::: instructor
Learners often struggle here, many may not work with financial data and concepts so they
find the example concepts difficult to get their head around.
の最大の問題は、wellth_scoreを生成する行ですが、このステップは
を通して話さなければなりません。

- これまで
  コースでカバーされていなかったブール値とフロート値の間の暗黙的変換を使用します。
- axis=1引数は明確に説明する必要があります。
  :::::::::::::::::::::::::::::::::::::::::::::::::

Pandas vectorizing methods and grouping operations are features that provide users
much flexibility to analyse their data.

例えば、欧州諸国
がGDPに応じてどのように分割されているかについて、明確な見方をしたいとしましょう。

1. 調査された年の間に国を二つのグループに分割することによって、私たちは一目見ることができるかもしれません
   ヨーロッパ平均よりも_高い_GDPを示した人と_低い_GDPを示した人。
2. その後、歴史的(1962年から2007年まで)の値に基づいて、_裕福なスコア_を見積もります。
   では、ある国が_より低い_または_より高い_GDPのグループに参加した回数を記録しています。

```python
mask_higher = data > data.mean()
bilth_score = mask_higher.aggregate('sum', axis=1) / len(data.columns)
print(wellth_score)
```

```output
country
Albania                   0.000000
Austria                   1.000000
Belgium                   1.000000
Bosnia and Herzegovina    0.000000
Bulgaria                  0.000000
Croatia                   0.000000
Czech Republic            0.500000
Denmark                   1.000000
Finland                   1.000000
France                    1.000000
Germany                   1.000000
Greece                    0.333333
Hungary                   0.000000
Iceland                   1.000000
Ireland                   0.333333
Italy                     0.500000
Montenegro                0.000000
Netherlands               1.000000
Norway                    1.000000
Poland                    0.000000
Portugal                  0.000000
Romania                   0.000000
Serbia                    0.000000
Slovak Republic           0.000000
Slovenia                  0.333333
Spain                     0.333333
Sweden                    1.000000
Switzerland               1.000000
Turkey                    0.000000
United Kingdom            1.000000
dtype: float64
```

最後に、`weelth_score`表の各グループについて、チェーン付きのメソッドを使用して調査された年間にわたって彼らの(金融)貢献
を合計します。

```python
print(data.groupby(wealth_score).sum())
```

```output
          gdpPercap_1952  gdpPercap_1957  gdpPercap_1962  gdpPercap_1967  \
0.000000    36916.854200    46110.918793    56850.065437    71324.848786   
0.333333    16790.046878    20942.456800    25744.935321    33567.667670   
0.500000    11807.544405    14505.000150    18380.449470    21421.846200   
1.000000   104317.277560   127332.008735   149989.154201   178000.350040   

          gdpPercap_1972  gdpPercap_1977  gdpPercap_1982  gdpPercap_1987  \
0.000000    88569.346898   104459.358438   113553.768507   119649.599409   
0.333333    45277.839976    53860.456750    59679.634020    64436.912960   
0.500000    25377.727380    29056.145370    31914.712050    35517.678220   
1.000000   215162.343140   241143.412730   263388.781960   296825.131210   

          gdpPercap_1992  gdpPercap_1997  gdpPercap_2002  gdpPercap_2007  
0.000000    92380.047256   103772.937598   118590.929863   149577.357928  
0.333333    67918.093220    80876.051580   102086.795210   122803.729520  
0.500000    36310.666080    40723.538700    45564.308390    51403.028210  
1.000000   315238.235970   346930.926170   385109.939210   427850.333420
```

::::::::::::::::::::::::::::::::: チャレンジ

## 個々の値の選択

Assume Pandas has been imported into your notebook
and the Gapminder GDP data for Europe has been loaded:

```python
import pandas pd

data_europe = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')
```

2007でセルビアのPer CapitaGDPを見つけるために表現を書きます。

::::::::::::::::: solution

## 解決策

選択は行("セルビア")と列("gdpPercap_2007")の両方のラベルを使用して行うことができます。

```python
print(data_europe.loc['Serbia', 'gdpPercap_2007'])
```

出力は

```output
9786.534714
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## スライスの範囲

1. 以下の2つのステートメントは同じ出力を生成しますか?
2. これに基づいて、
   何が数字スライスに含まれている(あるいは含まれていない)とパンダでスライスに名前を付けられているのか?

```python
print(data_europe.iloc[0:2, 0:2])
print(data_europe.loc['Albania':'ベルギー', 'gdpPercap_1952':'gdpPercap_1962'])
```

::::::::::::::::: solution

## 解決策

いいえ、彼らは同じ出力を生成しません! 最初の文の出力は次のとおりです。

```output
        gdpPercap_1952 gdpPercap_1957
country                                
Albania 1601.056136 1942.284244
オーストリア 6137.076492 8842.598030
```

2 番目の文は以下のように与えられます。

```output
        gdpPercap_1952 gdpPercap_1957 gdpPercap_1962
country                                                
Albania 1601.056136 1942.284244 2312.888958
オーストリア 6137.076497 8842.598030 10750.721110
ベルギー 8343.105127 9714.960623 10991.206760
```

明らかに、2 番目の文は、最初の文と比較して追加の列と追加の行を生成します。\
どのような結論を出せますか？ 数字のスライス、0:2、_省略_、最終的なインデックスがあることがわかります。 index 2)
が指定された範囲内の
が 'gdpPercap_1952':'gdpPercap_1962', \*最終要素が含まれています。

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## データの再構築

`first`, `second`などには何がありますか？

```python
first = pd.read_csv('data/gapminder_all.csv', index_col='country')
second = first['csv'] == 'Americas']
third = second.drop('Puerto Rico')
fth = third.drop('csv', axis = 1)
furth.to_csv('result.csv')
```

::::::::::::::::: solution

## 解決策

このコードを一行ずつ見ていきましょう。

```python
first = pd.read_csv('data/gapminder_all.csv', index_col='country')
```

この行は、すべての国のGDPデータを含むデータセットを
`first` と呼ばれるデータフローにロードします。 `index_col='country'`パラメータは、データフローの
行のラベルとして使用する列を選択します。

```python
second = first['大陸'] == 'Americas']
```

この行は選択します。'大陸' 列が
'Americas' に一致する列の `first` のみが抽出されます。 括弧
`first['continent'] == 'Americas'` 内のブール値の式が、式が true の行のみを選択するために使用されていることに注意してください。
この式を印刷してみてください！ また、それぞれの True/False 要素も印刷できますか?
(ヒント: 最初に式を変数に割り当てます)

```python
third = second.drop('プエルトリコ)
```

構文が示すように、この行はラベルが「プエルトリコ」の「second」から行をドロップします。 結果として生成された
は、元の `second` よりも 1 つの行を持っています。

```python
4番目= third.drop('大陸', axis = 1)
```

ドロップ関数を適用しますが、この場合は行ではなく列全体をドロップします。
これを実現するには、 `axis` パラメータも指定する必要があります(インデックス1を持つ2番目の列
をドロップします)。

```python
fth.to_csv('result.csv')
```

最後のステップは、csvファイルに取り組んでいるデータを書き込むことです。 パンダは `to_csv()` 関数で
を簡単にします。 関数に必要な引数はファイル名だけです。
ファイルは、Jupyter または Python セッションを開始したディレクトリに書き込まれます。

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## インデックスの選択

以下の短いプログラムで `idxmin` と `idxmax` が何をするかを簡単な用語で説明します。
これらの方法はいつ使われますか。

```python
data = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')
print(data.idxmin())
print(data.idxmax())
```

::::::::::::::::: solution

## 解決策

`data`の各列に対して、`idxmin`は各列の最小値に対応するインデックス値を返します。
`idxmax` は各列の最大値に対して同じ動作をします。

これらの関数は、実際の最小/最大値ではなく、最小/最大値の行インデックスを取得したいときはいつでも使用できます。

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 選択肢を使って練習

パンダが輸入され、ヨーロッパのGapminderGDPデータがロードされたと仮定してください。
以下のいずれかを選択する式を記述します。

1. 1982年の全ての国の一人当たりGDP。
2. デンマークの一人当たりGDPは何年も続いています
3. 1985年以降の全ての国の一人当たりGDP\*。
4. 2007年の各国の一人当たりGDPは、1952年の
   一人当たりGDPの倍数である。

::::::::::::::::: solution

## 解決策

1:

```python
data['gdpPercap_1982']
```

2:

```python
data.loc['Denmark',:]
```

3:

```python
data.loc[:,'gdpPercap_1985':)
```

Pandasはカラムラベルの末尾にある数字を認識するのに十分スマートであり、エラーは発生しません。 `gdpPercap_1985`という名前の列は実際には存在しません。 これは、後でCSVファイルに新しい列を追加する場合に便利です。

4:

```python
data['gdpPercap_2007']/data['gdpPercap_1952']
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## アクセスの多くの方法

DataFrameには、名前またはインデックスで値またはスライスにアクセスするには、少なくとも2つの方法があります。
しかし、他にもたくさんあります。 例えば、1つの列または行は、`DataFrame`
または`Series`オブジェクトとしてアクセスできます。

DataFrameで以下の操作を行うさまざまな方法を提案します:

1. 単一列にアクセス
2. 1行にアクセス
3. 個々の DataFrame 要素にアクセス
4. 複数の列にアクセス
5. 複数の行にアクセス
6. 特定の行と列のサブセットにアクセスします
7. 行範囲と列範囲のサブセットにアクセス

::::::::::::::::: solution

## 解決策

1\. 単一列へのアクセス:

```python
# by name
data["col_name"]   # as a Series
data[["col_name"]] # as a DataFrame

# by name using .loc
data.T.loc["col_name"]  # as a Series
data.T.loc[["col_name"]].T  # as a DataFrame

# Dot notation (Series)
data.col_name

# by index (iloc)
data.iloc[:, col_index]   # as a Series
data.iloc[:, [col_index]] # as a DataFrame

# using a mask
data.T[data.T.index == "col_name"].T
```

2\. 1行へのアクセス:

```python
# by name using .loc
data.loc["row_name"] # as a Series
data.loc[["row_name"]] # as a DataFrame

# by name
data.T["row_name"] # as a Series
data.T[["row_name"]].T # as a DataFrame

# by index
data.iloc[row_index]   # as a Series
data.iloc[[row_index]]   # as a DataFrame

# using mask
data[data.index == "row_name"]
```

3\. 個々のDataFrame要素にアクセス:

```python
# by column/row names
data["column_name"]["row_name"]         # as a Series

data[["col_name"]].loc["row_name"]  # as a Series
data[["col_name"]].loc[["row_name"]]  # as a DataFrame

data.loc["row_name"]["col_name"]  # as a value
data.loc[["row_name"]]["col_name"]  # as a Series
data.loc[["row_name"]][["col_name"]]  # as a DataFrame

data.loc["row_name", "col_name"]  # as a value
data.loc[["row_name"], "col_name"]  # as a Series. Preserves index. Column name is moved to `.name`.
data.loc["row_name", ["col_name"]]  # as a Series. Index is moved to `.name.` Sets index to column name.
data.loc[["row_name"], ["col_name"]]  # as a DataFrame (preserves original index and column name)

# by column/row names: Dot notation
data.col_name.row_name

# by column/row indices
data.iloc[row_index, col_index] # as a value
data.iloc[[row_index], col_index] # as a Series. Preserves index. Column name is moved to `.name`
data.iloc[row_index, [col_index]] # as a Series. Index is moved to `.name.` Sets index to column name.
data.iloc[[row_index], [col_index]] # as a DataFrame (preserves original index and column name)

# column name + row index
data["col_name"][row_index]
data.col_name[row_index]
data["col_name"].iloc[row_index]

# column index + row name
data.iloc[:, [col_index]].loc["row_name"]  # as a Series
data.iloc[:, [col_index]].loc[["row_name"]]  # as a DataFrame

# using masks
data[data.index == "row_name"].T[data.T.index == "col_name"].T
```

4\. 複数の列にアクセス:

```python
# by name
data[["col1", "col2", "col3"]]
data.loc[:, ["col1", "col2", "col3"]]

# by index
data.iloc[:, [col1_index, col2_index, col3_index]]
```

5\. 複数の行にアクセス

```python
# by name
data.loc[["row1", "row2", "row3"]]

# by index
data.iloc[[row1_index, row2_index, row3_index]]
```

6\. 特定の行と列のサブセットにアクセスします

```python
# by names
data.loc[["row1", "row2", "row3"], ["col1", "col2", "col3"]]

# by indices
data.iloc[[row1_index, row2_index, row3_index], [col1_index, col2_index, col3_index]]

# column names + row indices
data[["col1", "col2", "col3"]].iloc[[row1_index, row2_index, row3_index]]

# column indices + row names
data.iloc[:, [col1_index, col2_index, col3_index]].loc[["row1", "row2", "row3"]]
```

7\. 行範囲と列範囲のサブセットにアクセス

```python
# by name
data.loc["row1":"row2", "col1":"col2"]

# by index
data.iloc[row1_index:row2_index, col1_index:col2_index]

# column names + row indices
data.loc[:, "col1_name":"col2_name"].iloc[row1_index:row2_index]

# column indices + row names
data.iloc[:, col1_index:col2_index].loc["row1":"row2"]
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## `dir()`関数を使って利用可能なメソッドを探索する

Python には `dir()` 関数が含まれており、データオブジェクトに組み込まれている利用可能なすべてのメソッド (関数) を表示できます。  第4話では、いくつかのメソッドを文字列で使用しました。 しかし、`dir()`を使用することで、より多くのものが利用可能になります。

```python
my_string = 'Hello world!' # string object 
dir(my_string)
```

このコマンドは以下を返します:

```python
['__add__',
...
'__subclasshook__',
'capitalize',
'casefold',
'center',
...
'upper',
'zfill']
```

`help()` または <kbd>Shift</kbd>+<kbd>Tab</kbd> を使用すると、これらのメソッドの詳細情報を取得できます。

パンダがインポートされ、ヨーロッパのGapminderGDPデータが「data」としてロードされたとします。  次に、`dir()`
を使用して、毎年その情報が入手可能なすべてのヨーロッパ諸国で一人当たりGDPの中央値を出力する関数を見つけます。

::::::::::::::::: solution

## 解決策

多くの選択肢の中で、`dir()`は`median()`関数を可能としてリストしています。  したがって、

```python
data.median()
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 解説

ポーランドの国境は1945年、
以来安定していますが、それ以前の数年間で数回変わりました。
20世紀全体にわたってポーランド
の一人当たりGDPの表を作っていたら、どのように対処するでしょうか。

::::::::::::::::::::::::::::::::::::::::::::::::::

[pandas-dataframe]: https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.html

[pandas-series]: https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.html

[numpy]: https://www.numpy.org/

:::::::::::::::::::::::::::::::::::::::: keypoints

- 整数の位置で値を選択するには、`DataFrame.iloc[..., ...]` を使用します。
- すべての列またはすべての行を意味するには、単独で `:` を使用します。
- `DataFrame.loc` と名前付きスライスを使用して、複数の列または行を選択します。
- スライスの結果は、さらなる操作で使用できます。
- 比較を使用して、値に基づいてデータを選択します。
- ブールマスクを使用して値またはNaNを選択します。

::::::::::::::::::::::::::::::::::::::::::::::::::
