# Latex-Template
個人的なLaTeXのテンプレートです．かなりふざけまくってますが，そんなに堅い資料にしたくないだけです（震え声）
「これを書くにはこれがいい」とか，「このpackageはよくない」等々，ご意見ありましたらコメント等で教えてください．

なお，documentclassやpackageについては，個人的によく使うものを全部入れしています．
使用する際は足したり消したりして，自分だけのオリジナルテンプレを作ってください．

# \documentclassや\usepackageについて
よくわからない人もいると思うので，上記二つについて簡単に説明しようと思います．
基本的な数式の書き方とかは，Google大先生に頼ってみてください．

## \documentclass
documentclassとは，「どんな文章を書くのか」というのを設定できるものだと思っています．
書き方は，以下のような感じです．
```tex
\documentclass[option]{paper class}
```
optionには文字サイズだったり，紙のサイズだったりを入力します．
また，paper classでは「article」「report」「book」の設定ができます．
ここで，ファイル内のコードを見てみましょう．
```tex
\documentclass[11pt, a4paper, titlepage]{jsarticle}
```
この書き方だと，「文字サイズ11ptで，A4サイズのarticleを生成してくれ．あ，表紙込みでｵﾅｼｬｽ．」といった感じですね．
更に詳しい内容については，以下のサイトがとても参考になるかと思います．

[LaTeX 文章の設定 - Yamamoto's Laboratory](http://www.yamamo10.jp/yamamoto/comp/latex/make_doc/doc_settings/index.php)

## \usepackage
packageは，いろんな機能を追加するものです．Pythonでいう「ライブラリ」，C/C++でいう「ヘッダーファイル」ですね，多分．

ではでは，ファイルに書いてあるpackageについて説明を書いてきますね．

### graphicx
画像を挿入したり，回転したり，拡大・縮小するためのpackageです．
```tex
\usepackage[dvipdfmx]{graphicx}
```
画像の取り込みについては，実はLaTeX自体に機能として存在していません．そのため，packageとして追加してあげる必要があります．

また，PDFへの出力は「ドライバ」が担当します．
上記コードの```dvipdfmx```がドライバですね．
これについては，```dvips```とかいろいろあります．
このドライバについては，ご自身の環境に合わせて設定してあげてください．
もれなく，コンパイラが喜びます．

なお，画像の挿入例は，以下の通りです．
```tex
\begin{figure}[htb]
    \centerline{\includegraphics[scale=0.3, clip]{hogefugapiyo.jpg}}
    \caption{関係図}
    \label{hogefugapiyo2}
\end{figure}
```
細かい使い方については，Google大先生に聞いてみてください．
いっぱい画像をｷﾞｭｲﾝｷﾞｭｲﾝしましょうね．ｷﾞｭｲﾝｷﾞｭｲﾝ．

### \usepackage{listings}
ソースコードを直接LaTeXに書き込むためのpackageです．それだけです．使わない気がしてきた...

### \usepackage{amsmath, amssymb}
様々な数式記号を記述するためのpackageです，僕は超絶使ってます．
二項演算子と関係演算子，累積，アクセント，句読点・点，矢印などなど...大量に追加されます．
内容については，以下のサイトがとても参考になります．

[LaTeX 数式amsmath (記号) - Yamamoto's Laboratory](http://www.yamamo10.jp/yamamoto/comp/latex/make_doc/formula/amsmath_symbol/index.php)，
[数学記号（等号、不等号、演算子、集合） - LaTeX入門](https://medemanabu.net/latex/operators/)

### \usepackage{amsthm}
定理や補題，それらの証明について書くときに使用するpackageです．それぞれに対して，勝手に通し番号を付けてくれます．僕は理論屋さんなので，めちゃくちゃ使っています．

初期設定で，"theorem"や"Lemma"といった感じで英語で表示されるので，```\newtheorem```を使って好きなように設定し直してください．
以下，僕のサンプルです．
```tex
\newtheorem{thm}{定理}
\newtheorem{lem}{補題}
\newtheorem{asm}{前提}
\newtheorem{rmk}{注意}
\newtheorem*{prb}{問題設定}
```
なお，その下のｸｿ長いコードについては，もっといい書き方があると思います．
proofを頑張って日本語に変換しています．
```tex
\renewcommand{\proofname}{証明}
\newcommand{\argmin}{\mathop{\rm arg~min}\limits}

\makeatletter % use at mark
\renewenvironment{proof}[1][\proofname]{\par
	\pushQED{\qed}%
	\normalfont \topsep6\p@\@plus6\p@\relax
	\trivlist
	\item[\hskip\labelsep
	\itshape
	{\bf\underline{#1}}]\ignorespaces
	% {\bf\underline{#1}\@addpunct{.}}]\ignorespaces % ピリオドあり
}{%
	\popQED\endtrivlist\@endpefalse
}
```
調べた時に，ぱっと出てきたものをそのままコピペしただけなので...あ，殴らないで...

### \usepackage{bbm}
要素がすべて1のベクトルとかを，二重文字で書くときに使用します．ただ，特定の環境以外では使えないので，あんまりお勧めしません．
**ちなみに僕は，中間発表のポスターでこれ関係でちょっとやらかしました．**

### \usepackage{siunitx}
国際単位系（SI単位系）を書くためのpackageです．細かい使い方は，以下のサイトを参考にしてください．
ヤードポンド法は，滅びるべし（圧倒的使命感）．

[LaTeX数値・単位 (siunitx) - Yamamoto's Laboratory](http://www.yamamo10.jp/yamamoto/comp/latex/make_doc/unit/index.php)，
[SI単位（国際単位系） - siunitxパッケージのマクロ - LaTeX入門](https://medemanabu.net/latex/siunitx-macro/)

### \usepackage{algorithmic}, \usepackage{algorithm}
模擬アルゴリズムを記載するためのpackageです．最適化とか，最適制御の論文でよく見るやつですね．以下のようなものが生成できるようになります．

![image](https://user-images.githubusercontent.com/64090468/203940769-cf8035aa-dd14-4012-86c8-c190e97ed0ab.png)

ちなみに，これのコードは
```tex
\begin{algorithm}[H]
    \caption{Calculate hoge theorem with buriburi Algorithm}
    \label{BRA}
    \begin{algorithmic}[1]
        \STATE hogehoge
        \FOR{$k = 0, 1, 2, \dots$}
        \STATE 現在の$buriburi$における$buri$の$piyopiyo$を計算
        \STATE buri空間内の最大値$fugafuga$を次の$\nabla hoge$と更新
        \ENDFOR
    \end{algorithmic}
\end{algorithm}
```

以下のサイトが参考になります．

[TeX論文にアルゴリズム（疑似コード）を書く方法 - Qiita](https://qiita.com/jirojiro/items/0ae13aac9112a804f8d5)

### \usepackage{ascmac}
枠付き文章を書くためのpackageです，研究の進捗報告書内の定理紹介とかでよく使います．

![image](https://user-images.githubusercontent.com/64090468/203939835-e7dbf794-3241-40b4-aae9-be2afe45470c.png)

数学の教科書とカで見る感じのやつですね．
ちなみに，生成コードは
```tex
\begin{itembox}[l]{hogeの定理}
    hogeの定理は，hoge・fugaによってhogehoge年に発表されたfugafugaについての定理である．
    hogeは特定のfuga空間について，piyoの関係性から以下のburiburiを満たす．
    \begin{align*}
        piyopiyo = \max_{fugafuga \in fuga} \left(\nabla buri - \nabla hoge \right)
    \end{align*}
\end{itembox}
```

これについては，以下のサイトが参考になります．
[LaTeX枠付き文章 - Yamamoto's Laboratory](http://www.yamamo10.jp/yamamoto/comp/latex/make_doc/box/box.php)

# 最後に
参考サイト，いくつか```http```になっているので，いいサイトを見つけたら差し替える予定です．（セキュリティ的に不安）
ザッと書きましたが，他に書いてほしいものがありましたら，教えてください．
