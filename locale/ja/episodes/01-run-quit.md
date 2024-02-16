---
title: 実行中と終了
teaching: 15
exercises: 0
---

::::::::::::::::::::::::::::::::::

- JupyterLabサーバーを起動します。
- Create a new Python script.
- Jupyter ノートブックを作成します。
- JupyterLabサーバーをシャットダウンします。
- PythonスクリプトとJupyterノートブックの違いを理解します。
- ノートブックにマークダウンセルを作成します。
- ノートブックでPythonセルを作成して実行します。

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::

- Pythonプログラムを実行するにはどうすればいいですか?

::::::::::::::::::::::::::::::::::::::::::::::::::

Pythonを実行するには、\[jupyter] [JupyterLab][jupyterlab] を経由してformat@@3 "Jupyter Notebooks" を使用します。 Jupyter notebooks はデータサイエンスや可視化に一般的であり、Pythonコードをインタラクティブに実行するための便利な共通分母体験として、Pythonコードの結果を簡単に表示して共有することができます。

コードの編集、管理、実行には他の方法があります。 ソフトウェア開発者は、 [PyCharm](https://www.jetbrains) のような統合開発環境 (IDE) をよく使用します。 om/pycharm/) または [Visual Studio Code](https://code.visualstudio.com/), または Vim や Emacs のようなテキストエディタを使って Python プログラムを作成し編集します。 Pythonプログラムを編集して保存したら、IDE自体またはコマンドラインで直接これらのプログラムを実行できます。 これとは対照的に、Jupyter notebooks はPythonコードの結果をすぐにノートブック内で見ることができます。

JupyterLabには他にも便利な機能がいくつかあります:

- コードのブロックを簡単に入力、編集、コピー、貼り付けできます。
- Tab complete allows you to easily access the names of things you are using
  and learn more about them.
- It allows you to annotate your code with links, different sized text, bullets, etc.
  to make it more accessible to you and your collaborators.
- コードの横に図を表示し、
  を生成して分析のストーリーを伝えることができます。

各ノートブックには、コード、テキスト、または画像を含む1つ以上のセルが含まれています。

## JupyterLab 入門

JupyterLab is an application server with a web user interface from [Project Jupyter][jupyter] that
enables one to work with documents and activities such as Jupyter notebooks, text editors, terminals,
and even custom components in a flexible, integrated, and extensible manner. JupyterLab requires a
reasonably up-to-date browser (ideally a current version of Chrome, Safari, or Firefox); Internet
Explorer versions 9 and below are _not_ supported.

JupyterLab は Anaconda Python ディストリビューションの一部として含まれています。 If you have not already
installed the Anaconda Python distribution, see [the setup instructions](../learners/setup.md)
for installation instructions.

このレッスンではJupyterLabを自分のマシンでローカルで実行するので、
AnacondaとJupyterLabをダウンロードしてインストールするための最初の接続以外のインターネット接続は必要ありません。

- JupyterLabサーバーを起動する
- JupyterLabサーバーに接続する特別なlocalhostURLを開くには、Webブラウザを使用してください
- JupyterLabサーバーは作業を行い、Webブラウザは結果をレンダリングします
- ブラウザにコードを入力し、JupyterLabサーバーがコードの実行を終了した後に結果を確認してください

:::::::::::::::::::::::::::::::::::::::::  callout

## JupyterLab? Jupyter notebooksはどうですか?

JupyterLab は format@@0(https\://jupyterlab.readthedocs.io/en/stable/getting_started/overview\.html#overview) の進化の次の段階です。
Jupyterノートブックを使った経験がある方は、JupyterLabに何を期待すべきかをお勧めします。

Experienced users of Jupyter notebooks interested in a more detailed discussion of the similarities and differences
between the JupyterLab and Jupyter notebook user interfaces can find more information in the
[JupyterLab user interface documentation][jupyterlab-ui].

::::::::::::::::::::::::::::::::::::::::::::::::::

## JupyterLabを開始

JupyterLabサーバーは、コマンドラインまたは
`Anaconda Navigator` と呼ばれるアプリケーションから起動できます。 Anaconda Navigatorは、Anaconda Python配布物の一部として含まれています。

### macOS - コマンドライン

JupyterLab サーバーを起動するには、ターミナルからコマンドラインにアクセスする必要があります。
Mac上でターミナルを開くには2つの方法があります。

1. ApplicationsフォルダでUtilitiesを開き、ターミナルをダブルクリックします
2. <kbd>コマンド</kbd> + <kbd>スペースバー</kbd> を押してSpotlightを起動します。 Type `Terminal` and then
   double-click the search result or hit <kbd>Enter</kbd>

Terminal を起動したら、JupyterLab サーバーを起動するコマンドを入力します。

```bash
$ jupyter lab
```

### Windowsユーザー - コマンドライン

JupyterLab サーバーを起動するには、Anaconda Prompt にアクセスする必要があります。

<kbd>Windowsロゴキー</kbd> を押し、`Anaconda Prompt`を検索し、結果をクリックするか、Enterキーを押します。

Anaconda Promptを起動したら、次のコマンドを入力します。

```bash
$ jupyter lab
```

### Anaconda Navigator

JupyterLab サーバーをAnaconda Navigatorから起動するには、まず[Anaconda Navigatorを起動(macOS、Windows、Linuxの詳細な手順についてはクリック)](https://docs.anaconda.com/free/navigator/getting-started/#navigator-starting-navigator)する必要があります。 You can search for Anaconda Navigator via Spotlight on macOS (<kbd>Command</kbd> + <kbd>spacebar</kbd>), the Windows search function (<kbd>Windows Logo Key</kbd>) or opening a terminal shell and executing the `anaconda-navigator` executable from the command line.

Anaconda Navigatorを起動したら、JupyterLabの下にある「Launch」ボタンをクリックします。 下にスクロールするには、
が必要かもしれません。

ここでは、macOS
またはWindowsのいずれかで開くはずのAnaconda Navigatorページのスクリーンショットを示します。

<p align='center'>
  <img alt="Anaconda Navigator landing page" src="fig/0_anaconda_navigator_landing_page.png" width="750"/>
</p>

And here is a screenshot of a JupyterLab landing page that should be similar to the one that opens in your
default web browser after starting the JupyterLab server on either macOS or Windows.

<p align='center'>
  <img alt="JupyterLab landing page" src="fig/0_jupyterlab_landing_page.png" width="750"/>
</p>

## JupyterLabインターフェイス

JupyterLabには従来の統合開発環境(IDE)で見られる多くの機能がありますが、
はインタラクティブで探索的なコンピューティングのための柔軟な構成要素を提供することに焦点を当てています。

The [JupyterLab Interface][jupyterlab-ui]
consists of the Menu Bar, a collapsable Left Side Bar, and the Main Work Area which contains tabs
of documents and activities.

### メニューバー

JupyterLabの上部にあるメニューバーには、JupyterLabで利用可能なさまざまなアクション
をキーボードショートカット(該当する場合)とともに公開する最上位メニューがあります。 以下の
メニューがデフォルトで含まれています。

- **ファイル:** _新規_、_開く_、_閉じる_、_保存_などのファイルやディレクトリに関連するアクション。 _ファイル_ メニューには、JupyterLab サーバーのシャットダウンに使用する _シャットダウン_ アクションも含まれています。
- **編集:** _元に戻す_、_切り取り_、_コピー_、_貼り付け_など、ドキュメントの編集やその他のアクティビティに関連するアクション。
- **View:** JupyterLabの外観を変更するアクション。
- **実行:** ノートブックやコードコンソールなど、さまざまなアクティビティでコードを実行するためのアクション（以下で説明します）
- **カーネル:** カーネルを管理するためのアクション。 木星のケルネルについては、以下で詳しく説明します。
- **タブ:** メインワークエリアで開かれたドキュメントとアクティビティのリストです。
- **設定:** JupyterLabの共通設定は、このメニューを使用して設定できます。 また、ドロップダウンメニューには、JupyterLabの設定と設定オプションの詳細な制御を提供する_詳細設定エディタ_ オプションもあります。
- **ヘルプ:** JupyterLabとカーネルヘルプの一覧です。

:::::::::::::::::::::::::::::::::::::::::  callout

## カーネルズ

JupyterLab [docs](https://jupyterlab.readthedocs.io/en/stable/user/documents_kernels.html)
はカーネルを「異なるプログラミング言語と環境でコードを実行するサーバによって開始された別々のプロセス」として定義しています。
Jupyter Notebookを開くと、コードを実行するプロセスであるカーネルを起動します。
このレッスンでは、対話的に Python 3 コードを実行できるようにする Jupyter ipyton カーネルを使用します。

Using other Jupyter [kernels for other programming languages](https://github.com/jupyter/jupyter/wiki/Jupyter-kernels) would let us
write and execute code in other programming languages in the same JupyterLab interface, like R, Java, Julia, Ruby, JavaScript, Fortran,
etc.

::::::::::::::::::::::::::::::::::::::::::::::::::

デフォルトのメニューバーのスクリーンショットは以下に示されています。

<p align='center'>   <img alt="JupyterLab Menu Bar" src="fig/0_jupyterlab_menu_bar.png" width="750"/>
</p>

### Left Sidebar

The left sidebar contains a number of commonly used tabs, such as a file browser (showing the
contents of the directory where the JupyterLab server was launched), a list of running kernels
and terminals, the command palette, and a list of open tabs in the main work area.
のスクリーンショットは以下に示されています。

<p align='center'>   <img alt="JupyterLab Left Side Bar" src="fig/0_jupyterlab_left_side_bar.png" width="250"/>
</p>

左側のサイドバーは、アクティブなサイドバータブをクリックして、ビューメニューの「左側のバーを表示」または
を選択することで、折りたたみまたは展開することができます。

### 主な作業エリア

JupyterLabの主な作業領域では、ドキュメント(ノートブック、テキストファイルなど)を配置できます。
その他のアクティビティ (端末、コードコンソールなど) タブのパネルに切り替えることも、
が細分されます。 デフォルトのメインワークエリアのスクリーンショットを以下に示します。

Launcherタブが表示されない場合は、「ファイル」と「編集」メニューの下にある青いプラス記号をクリックすると表示されます。

<p align='center'>   <img alt="JupyterLab Main Work Area" src="fig/0_jupyterlab_main_work_area.png" width="750"/>
</p>

タブをタブパネルの中央にドラッグして、タブをパネルに移動します。 タブパネルを、
パネルの左、右、上、または下にドラッグして分割します。 作業領域には、単一の現在の
アクティビティがあります。 現在のアクティビティのタブには、上部の枠線が色付きで表示されます (既定では青)。

## Python スクリプトの作成

- 新しいPythonプログラムを書き始めるには、メインワークエリアのランチャータブの _Other_ ヘッダーの下にあるテキストファイルアイコンをクリックします。
  - メニューバーの _File_ メニューから _New -> Text File_ を選択することで、新しいプレーンテキストファイルを作成することもできます。
- このプレーンテキストファイルをPythonプログラムに変換する メニューバーの _File_ メニューから _Save File As_ アクションを選択し、新しいテキストファイルに `で終わる名前を付けます。 y`エクステンション
  - `.py`拡張子により、誰もがこのテキストファイルがPythonプログラムであることを知ることができます。
  - これは規則であり、要件ではありません。

## Jupyter Notebook の作成

To open a new notebook click the Python 3 icon under the _Notebook_ header in the Launcher tab in
the main work area. メニューバーの _ファイル_ メニューから _New -> Notebook_ を選択して、新しいノートブックを作成することもできます。

Jupyter ノートブックの追加ノート。

- メモ帳ファイルには、プレーンテキストのPythonプログラムと区別するための拡張子`.ipynb`があります。
- Notebooks はコマンドラインから実行できる Python スクリプトとしてエクスポートすることができます。

以下はJupyterLab内で動作するJupyterノートブックのスクリーンショットです。
の詳細に興味がある場合は、\[公式ノートブックドキュメント[jupyterlab-notebook-docs] を参照してください。

<p align='center'>   <img alt="Example Jupyter Notebook" src="fig/0_jupyterlab_notebook_screenshot.png" width="750"/>
</p>

:::::::::::::::::::::::::::::::::::::::::  callout

## 保管方法

- メモ帳ファイルは JSON という形式で保存されます。
- ウェブページのように保存されているものは、ブラウザで表示されるものとは異なります。
- しかし、この形式はJupyterがソースコード、テキスト、および画像をすべて1つのファイルに混ぜることを可能にします。

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## タブのパネルにドキュメントを配置

JupyterLab メインワークエリアでは、ドキュメントをタブのパネルに配置できます。 こちらは\[公式ドキュメント
]からの[jupyterlab]例です。

<p align='center'>   <img alt="Multi-panel JupyterLab" src="fig/0_multipanel_jupyterlab_screenshot.png" width="750"/>
</p>

まず、テキストファイル、Pythonコンソール、端末ウィンドウを作成し、メインのワークエリアに3つの
パネルに配置します。 次に、ノートブック、端末ウィンドウ、テキストファイルを作成し、
メインのワークエリアに3つのパネルを配置します。 最後に、
パネルとタブの独自の組み合わせを作成します。
ワークフローで最も役に立つのはどのパネルとタブの組み合わせだと思いますか？

::::::::::::::::: solution

## 解決策

After creating the necessary tabs, you can drag one of the tabs to the center of a panel to
move the tab to the panel; next you can subdivide a tab panel by dragging a tab to the left,
right, top, or bottom of the panel.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## コードとテキスト

Jupyter は、セルと呼ばれるさまざまな種類のブロックにコードとテキストをミックスします。 "
"code"という用語は、"Pythonなどの言語で書かれたソフトウェアのソースコード"を意味することがよくあります。
ノートブックの「コードセル」は、ソフトウェアを含むセルです。
「テキストセル」とは、人間のために書かれた普通の散文を含むものです。

::::::::::::::::::::::::::::::::::::::::::::::::::

## メモ帳にはコマンドと編集モードがあります。

- <kbd>Esc</kbd> と <kbd>Return</kbd> を交互に押すと、コードセルの外枠はグレーから青に変わります。
- これらはノートブックの **Command** (グレー) と **Edit** (青) モードです。
- format@@0モードでは、ノートブックレベルの機能を編集でき、format@@1モードではセルの内容が変更されます。
- When in Command mode (esc/gray),
  - <kbd>b</kbd> キーは、現在選択されているセルの下に新しいセルを作成します。
  - <kbd>a</kbd> key will make one above.
  - <kbd>x</kbd> キーで現在のセルが削除されます。
  - <kbd>z</kbd> キーを押すと、最後のセル操作(削除、作成など)が取り消されます。
- すべてのアクションはメニューを使用して行うことができますが、スピードアップするためのキーボードショートカットがたくさんあります。

::::::::::::::::::::::::::::::::: チャレンジ

## (Command) 対。 編集

Jupyterノートブックページでは、現在コマンドまたは編集モードにいますか?\
モードを切り替える。
ショートカットを使用して新しいセルを生成します。
ショートカットを使用してセルを削除します。
最後に実行したセル操作を元に戻すにはショートカットを使用します。

::::::::::::::::: solution

## 解決策

コマンドモードにはグレーの境界線があり、編集モードには青の境界線があります。
モードを切り替えるには、 <kbd>Esc</kbd> と <kbd>Return</kbd> を使用します。
コマンドモードにする必要があります(セルが青色の場合は、 <kbd>Esc</kbd> を押します)。  <kbd>b</kbd> または <kbd>a</kbd> と入力します。
コマンドモードにする必要があります(セルが青色の場合は、 <kbd>Esc</kbd> を押します)。  <kbd>x</kbd> と入力します。
コマンドモードにする必要があります(セルが青色の場合は、 <kbd>Esc</kbd> を押します)。  <kbd>z</kbd> と入力します。

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

### キーボードとマウスを使用してセルを選択および編集します。

- <kbd>Return</kbd> キーを押すと、境界線が青色になり、編集モードが有効になります。このモードでは、セル内に
  を入力できます。
- 1つのセルに多くのコードを書けるようにしたいからです
  を押すと <kbd></kbd> キーを返すと、編集モード (青) では、テキストエディタのようにセル内の次の行
  にカーソルが移動します。
- 私たちは、セル内のものを実行したいとノートブックに伝えるためのいくつかの他の方法が必要です。
- <kbd>Shift</kbd>+<kbd>Return</kbd> を押すと、セルの内容が実行されます。
- Notice that the <kbd>Return</kbd> and <kbd>Shift</kbd> keys on the right of the keyboard are
  right next to each other.

### ノートブックはMarkdownをきれいに印刷されたドキュメントに変換します。

- ノートブックは [Markdown][markdown] をレンダリングすることもできます。
  - リスト、リンク、
    などを書くためのシンプルなプレーンテキスト形式です。
  - 同様に、あなたが古い電子メールで送るもののように見えるHTMLのサブセット。
- コマンドモード (<kbd>Esc</kbd>/gray)
  を入力して、現在のセルをマークダウンセルに変換し、 <kbd>M</kbd> キーを押します。
- `In [ ]:`は消えてコードセルではなくなり、
  マークダウンで書くことができます。
- コマンドモード (<kbd>Esc</kbd>/gray ) を入力し、 <kbd>y</kbd> キーを押して、現在のセルをコードセルにします。

### MarkdownはHTMLが行うことのほとんどを行います。

<div class="row">

  <div class="col-md-6" markdown="1">

```
* アスタリスク
* を使用して
* 箇条書きリストを作成します。
```

  

  <div class="col-md-6" markdown="1">

- アスタリスクを使用
- 作成する
- 箇条書きリストだ

  </div>

</div>

<div class="row">

  <div class="col-md-6" markdown="1">

```
1. 数字
1を使用して、
1. 番号付きリストを作成します。
```

  

  <div class="col-md-6" markdown="1">

1. 数字を使用
2. 作成する
3. 番号付きリスト

  

</div>

<div class="row">

  <div class="col-md-6" markdown="1">

```
*  You can use indents
	*  To create sublists 
	*  of the same type
*  Or sublists
	1. Of different
	1. types
```

  

  <div class="col-md-6" markdown="1">

- インデントを使用できます
  - サブリストを作成するには
  - 同じ種類の
- またはサブリスト

  1. さまざまな
  2. types

  </div>

</div>

<div class="row">

  <div class="col-md-6" markdown="1">

```
# A Level-1 Heading
```

  

  <div class="col-md-6" markdown="1">

## レベル1の見出し

  

</div>

<div class="row">

  <div class="col-md-6" markdown="1">

```
## レベル 2 見出し (etc.)
```

  

  <div class="col-md-6" markdown="1">

## レベル2の見出し（等）

  

</div>

<div class="row">

  <div class="col-md-6" markdown="1">

```

改行は関係ありません。

空白の行
は新しい段落を作成します。
```

  

  <div class="col-md-6" markdown="1">

改行
は関係ありません。

しかし、空白行
は新しい段落を作成します。

  

</div>

<div class="row">

  <div class="col-md-6" markdown="1">

```
[Create links](http://software-carpentry.org) with `[...](...)` .
Or use [name-links][data_carpentry].

[data_carpentry]: http://datacarpentry.org
```

  

  <div class="col-md-6" markdown="1">

[Create links](https://software-carpentry.org) with `[...](...)`.
または、[nameed links][data_carpentry] を使用してください。

  

</div>

::::::::::::::::::::::::::::::::: チャレンジ

## Markdown でリストを作成する

次のようなノートブックのMarkdownセルにネストされたリストを作成します。

1. 資金を得る。
2. 仕事をしなさい。

- デザインの実験。
- データを収集する。
- 分析する

3. 手を挙げて。
4. 公開

::::::::::::::::: solution

## 解決策

このチャレンジは、番号付きリストと箇条書きリストの両方を統合します。
箇条書きリストは 2 つのスペースでインデントされており、番号付きリストの項目とインラインになります。

```
1. 資金を得る。
2. 仕事をする。
    * 設計実験。
    * データを収集する。
    * 分析。
3. 準備する。
4. 公開。
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## さらに多くのMath

複数の計算を含むノートブック
のPythonセルが実行されると、何が表示されますか?
たとえば、このセルが実行された場合はどうなりますか?

```python
7 * 3
2 + 1
```

::::::::::::::::: solution

## 解決策

Python は最後の計算の出力を返します。

```python
3
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## コードからマークダウンに既存のセルを変更

What happens if you write some Python in a code cell
and then you switch it to a Markdown cell?
例えば、
は以下をコードセルに入れます。

```python
x = 6 * 7 + 12
print(x)
```

そして、 <kbd>Shift</kbd>+<kbd>で実行し、コードセルとして動作することを確認するために</kbd> を返します。
セルに戻り、 <kbd>Esc</kbd> と <kbd>m</kbd> を使用してセルを Markdown
に切り替え、シフト <kbd>Shift</kbd>+<kbd>Return</kbd> を使用します。
何が起こり、これはどのように有用でしょうか?

::::::::::::::::: solution

## 解決策

Python コードは Markdown テキストのように扱われます。
行は連続する段落の一部であるかのように表示されます。
これは、複数の目的で使用されるノートブックのセルを一時的にオン/オフする場合に便利です。

```python
x = 6 * 7 + 12 print(x)
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::: チャレンジ

## 式

標準的なマークダウン(これらのノートに使用しているような)は、
式はレンダリングされませんが、ノートブックはレンダリングされます。
新しいMarkdown セル
を作成し、次のように入力します:

```
$\sum_{i=1}^{N} 2^{-i} \approx 1$
```

(コピーして貼り付ける方が簡単でしょう。
何を表示しますか？
アンダースコア、`_`、surflex、`^`、ドル記号、`$`はどう思いますか？

::::::::::::::::: solution

## 解決策

ノートブックには、LaTeX式構文からレンダリングされる式が表示されます。
`$`のドル記号はMarkdownに、テキストの間にLaTeXの式があることを伝えるために使われます。
LaTeX、underscore、`_`をよく知らない場合は、subscriptsやsurflexに使われます。`^`は上付き文字に使われます。
組の中括弧、 `{` と `}`、 は、テキストをグループ化するために使用されます。`i=1` が下付き文字になり、`N` が上付き文字になります。
同様に、`-i`は中括弧内にあり、文全体を`2`の上付き文字にします。
`\sum` と `\approx` は、 "sum over" と "approximate" シンボルの LaTeX コマンドです。

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

## JupyterLab を閉じる

- メニューバーから「ファイル」メニューを選択し、ドロップダウンメニューの下部にある「シャットダウン」を選択します。 JupyterLabサーバーをシャットダウンすることを確認するメッセージが表示されます(作業を保存することを忘れないでください)。 JupyterLabサーバーをシャットダウンするには、「シャットダウン」をクリックします。
- JupyterLab サーバーを再起動するには、シェルから次のコマンドを再実行する必要があります。

```
$ jupyter lab
```

::::::::::::::::::::::::::::::::: チャレンジ

## JupyterLab を閉じる

JupyterLabサーバーを閉じて再起動する練習をします。

::::::::::::::::::::::::::::::::::::::::::::::::::

[jupyterlab]: https://jupyterlab.readthedocs.io/en/stable/

[jupyterlab-ui]: https://jupyterlab.readthedocs.io/en/stable/user/interface.html

[jupyterlab-notebook-docs]: https://jupyterlab.readthedocs.io/en/stable/user/notebook.html

[markdown]: https://en.wikipedia.org/wiki/Markdown

[data_carpentry]: https://datacarpentry.org

:::::::::::::::::::::::::::::::::::::::: keypoints

- Python スクリプトはプレーンテキストファイルです。
- Pythonの編集と実行にはJupyter Notebook を使用してください。
- メモ帳にはコマンドと編集モードがあります。
- キーボードとマウスを使用してセルを選択および編集します。
- ノートブックはMarkdownをきれいに印刷されたドキュメントに変換します。
- MarkdownはHTMLが行うことのほとんどを行います。

::::::::::::::::::::::::::::::::::::::::::::::::::
