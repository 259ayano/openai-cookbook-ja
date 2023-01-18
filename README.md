# はじめに
[OpenAI Cookbook](https://github.com/openai/openai-cookbook) の日本語訳です。  
機械翻訳したものをベースに、少しでも補正して読み易くなれば良いなと考えています。 
元となるリポジトリへの追従、一貫性のある読み易い翻訳のガイドなど、他のリポジトリを参考にしながら進めたいと思います。


![badge](https://img.shields.io/endpoint.svg?url=https%3A%2F%2Fgezf7g7pd5.execute-api.ap-northeast-1.amazonaws.com%2Fdefault%2Fsource_up_to_date%3Fowner%3Dopenai%26repos%3Dopenai-cookbook%26ref%3Dmain%26path%3DREADME.md%26commit_hash%3Daeec6d9c1bae9c8c779ad62ac5b78e8ec479bf78)

# OpenAI Cookbook

このリポジトリは [OpenAI API] で一般的なタスクを実行するためのサンプル コードとサンプル プロンプトを共有しています。

これらの例を自分で試すには、OpenAI アカウントが必要です。始めるには無料のアカウントを作成してください。

ほとんどのコード例は Python で記述されていますが、概念はどの言語でも適用できます。

料理本のレシピが考えられるすべての食事やテクニックを網羅していないのと同じように、これらの例は考えられるすべての使用例や方法を網羅しているわけではありません。それらを、精緻化、発見、発明するための出発点として使用してください。

## 関連リソース

ここにあるコード例以外にも、次のリソースから [OpenAI API] について学ぶことができます。

* [OpenAI Playground] で GPT-3 を試す
* [OpenAI Documentation] で API について読む
* [OpenAI Community Forum] API について議論する
* [OpenAI Help Center] でヘルプを探す
* [OpenAI Examples] でプロンプトの例を参照してください

## 機能別に整理された例


<table id="verticalalign">
<thead>
  <tr>
    <th></th>
    <th>テキスト（文章）</th>
    <th>コード（プログラム）</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>書く</td>
    <td>
        <li><a href='#1-テキストを書く'>コピーライティング</a></li>
        <li><a href='#1-テキストを書く'>ブログ投稿</a></li>
        <li><a href='#1-テキストを書く'>商品説明</a></li>
        <li><a href='#1-テキストを書く'>質問の作成</a></li>
    </td>
    <td>
        <li><a href='#1-コードを書く'>コード補完（GitHub-Copilotなど）</a></li>
        <li><a href='#1-コードを書く'>自然言語ソフトウェアインターフェイス</a></li>
        <li><a href='#1-コードを書く'>テキストからコードへ</a></li>
        <li><a href='#1-コードを書く'>単体テスト</a></li>
    </td>
  </tr>
  <tr>
    <td>説明する</td>
    <td>
        <li><a href='#テキストに関する質問に答える'>ドキュメントに関する Q&A</a></li>
        <li><a href='#エンティティ抽出'>エンティティ抽出</a></li>
        <li><a href='#要約'>要約</a></li>
        <li><a href='#分類'>分類</a></li>
    </td>
    <td>
        <li><a href='#2-コードの説明'>コードのドキュメント</a></li>
        <li><a href='#2-コードの説明'>コードの説明</a></li>
        <li><a href='#2-コードの説明'>Docstrings</a></li>
    </td>
  </tr>
  <tr>
    <td>編集する</td>
    <td>
        <li><a href='#3-テキストを編集する'>編集</a></li>
        <li><a href='#翻訳'>翻訳</a></li>
    </td>
    <td>
        <li><a href='#3-コードを編集する'>言語またはスタイル間の変換</a></li>
        <li><a href='#3-コードを編集する'>バグ修正</a></li>
    </td>
  </tr>
  <tr>
    <td>比較する</td>
    <td>
        <li><a href='#semantic-search'>セマンティック検索</a></li>
        <li><a href='#recommendations'>推奨事項</a></li>
        <li><a href='#4-テキストを比較する'>クラスタリング</a></li>
        <li><a href='#4-テキストを比較する'>重複の検出</a></li>
    </td>
    <td>
        <li><a href='#4-テキストを比較する'>コード検索</a></li>
        <li><a href='#4-テキストを比較する'>コードクラスタリング</a></li>
    </td>
  </tr>
</tbody>
</table>

## 大規模言語モデルの仕組み

大規模な言語モデルは、テキストをテキストにマップする関数です。テキストの入力文字列が与えられると、大規模な言語モデルが次に来るテキストを予測しようとします。

大規模な言語モデルの魔法は、膨大な量のテキストでこの予測エラーを最小限に抑えるようにトレーニングすることで、モデルが最終的にこれらの予測に役立つ概念を学習することです。たとえば、次のような概念を学びます。

* 綴り方
* 文法の仕組み
* 言い換える方法
* 質問に答える方法
* 会話の持ち方
* 多くの言語で書く方法
* コーディング方法
* など

これらの機能は、明示的にプログラムされているわけではなく、すべてトレーニングの結果として現れます。

GPT-3 の機能は現在、生産性アプリ、教育アプリ、ゲームなど、何百もの異なるソフトウェア製品を支えています。

## 大規模な言語モデルを制御する方法

大規模な言語モデルへのすべての入力の中で、最も影響力があるのはテキスト プロンプトです。

大規模な言語モデルは、いくつかの方法で出力を生成するように促すことができます。

* **指示** ：モデルにあなたが望むものを伝えてください
* **完成** ：モデルを誘導して、必要なものの始まりを完成させます
* **デモンストレーション** ：次のいずれかを使用して、必要なものをモデルに表示します。
  * プロンプトのいくつかの例
  * 微調整トレーニング データセット内の数百または数千の例

それぞれの例を以下に示します。

### 指示プロンプト

命令に従うモデル (例: text-davinci-003またはtext-で始まる任意のモデル) は、命令に従うように特別に設計されています。指示をプロンプトの上部 (または下部、またはその両方) に書くと、モデルは指示に従って最善を尽くしてから停止します。指示は詳細に記述できるので、恐れずに、必要な出力を明示的に詳述する段落を記述してください。

命令プロンプトの例:

```text
以下の引用文から著者名を抜き出してください。

「一部の人間は、知的種族が宇宙空間に進出する前に絶滅すると理論づけています。
　それが正しければ、夜空の静けさは墓地の静けさです。」
― テッド・チャン
```

Output:

```text
テッド・チェン
```

### 完了プロンプトの例

補完スタイルのプロンプトは、言語モデルが次に来る可能性が最も高いと思われるテキストを書き込もうとする方法を利用します。モデルを操作するには、見たい出力によって完了するパターンまたは文を開始してみてください。直接的な指示と比較して、この大規模な言語モデルを操作するモードは、より注意を払い、実験を行う必要があります。さらに、モデルはどこで停止するかを必ずしも認識していないため、目的の出力を超えて生成されたテキストを切り取るために、停止シーケンスまたは後処理が必要になることがよくあります。

完了プロンプトの例::

```text
「一部の人間は、知的種族が宇宙空間に進出する前に絶滅すると理論づけています。
　それが正しければ、夜空の静けさは墓地の静けさです。」
― テッド・チャン

この引用の著者は、
```

Output:

```text
テッド・チェン
```

### デモプロンプトの例（数ショット学習）

補完スタイルのプロンプトと同様に、デモンストレーションはモデルに何をしてもらいたいかを示すことができます。このアプローチは、モデルがプロンプトで提供されるいくつかの例から学習するため、少数ショット学習と呼ばれることがあります。

デモンストレーション プロンプトの例:

```text
引用：
「推論する心が何度も何度も不可能に立ち向かわなければならないとき、それは適応するしかありません。」
― NK Jemisin、The Fifth Season
作者: NK ジェミシン

引用：
「一部の人間は、知的種族が宇宙空間に進出する前に絶滅すると理論づけています。それが正しければ、夜空の静けさは墓地の静けさです。」
― テッド・チャン
著者：
```

Output:

```text
テッド・チェン
```

### 微調整されたプロンプトの例

十分なトレーニング例があれば、カスタム モデルを微調整できます。この場合、モデルは提供されたトレーニング データからタスクを学習できるため、指示は不要になります。ただし、プロンプトが終了して出力を開始するタイミングをモデルに伝えるために、セパレータ シーケンス (例: ->または###または入力に一般的に表示されない任意の文字列) を含めると役立つ場合があります。セパレータ シーケンスがないと、モデルが、表示したい回答から開始するのではなく、入力テキストの詳細化を続行するリスクがあります。

微調整されたプロンプトの例 (同様のプロンプトと完了のペアでカスタム トレーニングされたモデルの場合):

```text
「一部の人間は、知的種族が宇宙空間に進出する前に絶滅すると理論づけています。それが正しければ、夜空の静けさは墓地の静けさです。」
― テッド・チャン

###


```

Output:

```text
テッド・チェン
```

### より迅速なアドバイス

より迅速な例については、[OpenAI Examples][OpenAI Examples] を参照してください。

一般に、入力プロンプトは、モデルの出力を改善するための最良の手段です。次のようなトリックを試すことができます。

* **もっと明確な指示を出してください。** たとえば、出力をコンマ区切りのリストにしたい場合は、コンマ区切りのリストを返すように要求します。答えがわからないときに「わかりません」と言わせたい場合は、「答えがわからない場合は「わかりません」と言ってください」と伝えます。
* **より良い例を提供してください。** プロンプトで例を示す場合は、例が多様で高品質であることを確認してください。
* **モデルに専門家のように答えてもらいます。** 高品質の出力または専門家によって書かれたかのような出力を生成するようにモデルに明示的に要求すると、モデルは、専門家が記述すると思われるより高品質の回答を与えることができます。例: 「次の回答は正確で、質が高く、専門家によって書かれています。」
* **モデルにその理由を説明する一連のステップを書き留めるよう促します。** たとえば、「[Let's think step by step](https://arxiv.org/pdf/2205.11916v1.pdf).」のような文を回答の先頭に追加します。最終的な答えの前にその理由を説明するようにモデルに促すことで、最終的な答えが一貫して正しい可能性を高めることができます。

## テキスト機能
### 1. テキストを書く

大規模な言語モデルは、テキストの記述に優れています。彼らは次のことを支援できます。

* ブログ投稿
* Email copy
* 広告コピー
* ウェブサイトのコピー
* 商品説明
* メモ
* ストーリーテリング
* ブレーンストーミング
* 質問の生成
* など

命令に従うモデルのプロンプトの例:

```text
ジルという名前の同僚に、彼女の昇進を祝うメールを書きます。  
トーンは温かみがありながらもプロフェッショナルでなければなりません。  
彼女がこれまで取り組んできた仕事をどのように賞賛しているかを述べてください。  
彼女のペットのトカゲであるマックスがバッタを食べるのが好きだというジョークを含めてください。  
来週のチームのオフサイトをどのように楽しみにしているのかを述べてください.
```

Output:

```text
親愛なるジルへ

昇進おめでとう！私はあなたの素晴らしい仕事に感心しており、あなたの成功を本当に嬉しく思います.  
トカゲのマックスも興奮しているに違いありません - 彼はもっと多くのバッタを食べるのを楽しみにしているに違いありません!

来週のチームオフサイトがとても楽しみです。みんなに追いついて、新しいアイデアをブレインストーミングするのは素晴らしいことです。

一番、

[あなたの名前]
```

一般に、書き込みはどのスタイルのプロンプトでも機能します。実験して、ユースケースに最適なものを確認してください。

|                                                            | Advantages                                                                    | Disadvantages                                                                    |
| ---------------------------------------------------------- | ----------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| 命令に従うモデル<br>(e.g., `text-davinci-003`) | 最も使いやすい                                                                | あまり創造的ではありません。多様性が低い。トーン、長さなどのコントロールが難しい。  |
| ベースモデル<br>(e.g., `davinci`)                           | よりクリエイティブに                                                                 | より高価です（プロンプトで例のデモンストレーションを含めるとトークンが必要になるため） |
| 微調整されたモデル                                          | 多くの例から訓練できます。プロンプトに例を含めるよりも安価 | トレーニングデータの収集が難しい。トレーニングは反復を遅くし、より高価にします |

### 2. テキストの説明

大規模な言語モデルの機能の 1 つは、テキストから情報を抽出することです。これには以下が含まれます。

* テキストに関する質問に答える。例:
  * ナレッジベースのクエリを実行して、人々が知らないことを調べられるようにする
  * なじみのないドキュメントにクエリを実行して、内容を理解する
  * タグ、クラス、エンティティなどを抽出するために、構造化された質問でドキュメントをクエリします。
* テキストの要約、例えば:
  * 長い文書の要約
  * やり取りされるメールやメッセージ スレッドの要約
  * 重要なポイントと次のステップを含む詳細な会議メモの要約
* テキストの分類、例:
  * 顧客からのフィードバック メッセージをトピックまたはタイプ別に分類する
  * トピックまたはタイプによるドキュメントの分類
  * テキストのトーンまたは感情の分類
* エンティティの抽出、例:
  * 顧客メッセージから連絡先情報を抽出する
  * ドキュメントから人物、会社、または製品の名前を抽出する
  * カスタマーレビューやフィードバックで言及されているものを抽出する

#### テキストに関する質問に答える

テキストに関する質問に答えるプロンプトの例:

```text
次のテキストを使用して、次の質問に答えてください。答えがテキストに含まれていない場合は、「わからない」と言ってください。

文章：
"""
中央アフリカの西海岸にあるガボンのオクロにあるオクロ鉱山 (時にはオクロ原子炉またはオクロ鉱山) は、 
唯一の天然の核分裂炉であると考えられています。 Oklo は、約 17 億年前に自己持続的な核分裂反応が起こり、 
数十万年にわたって続いたと考えられている 16 のサイトで構成されています。 
その間、平均して 100 kW 未満の火力があったと推定されています。
"""

質問: これまでに発見された天然核分裂炉の数は?

答え：
```

Output:

```text
 One
```

質問したいテキストがトークン制限 ( text-davinci-003 4,000 トークン、以前のモデルでは最大 2,000 トークン) よりも長い場合は、テキストを細かく分割し、関連性でランク付けしてから質問することをお勧めします。最も関連性の高い作品。

#### 要約

要約のプロンプトの例:

```text
次の文章を要約してください。

文章：
"""
スイスのジュネーブ近くにあるヨーロッパの高エネルギー物理学研究所 CERN で今朝、2 つの独立した実験結果が報告されました。  
どちらも、重さ約 125 ギガ電子ボルトの新しいボソン粒子の説得力のある証拠を示しており、  
これまでのところ、理論物理学者によって以前に行われたヒッグスの予測に適合しています。

「素人として、私はこう言うでしょう:『私たちはそれを持っていると思います』。あなたは同意しますか?」  
CERN の事務局長である Rolf-Dieter Heuer 氏は、満員の講堂にこう尋ねました。そこに集まった物理学者たちは拍手喝采した。
"""

概要：
```

Output:

```text
CERN は新しい粒子、ヒッグス粒子の発見を発表しました。  
この粒子は理論物理学者によって予測されており、宇宙の理解における大きな前進です。
```

#### 分類

テキストを分類する最善の方法は、クラスが事前にわかっているかどうかによって異なります。

クラスが事前にわかっている場合は、[Fine-tuned_classification.ipynb](examples/Fine-tuned_classification.ipynb) で示されているように、微調整されたモデルを使用して分類を行うのが最適です。

クラスが事前にわかっていない場合 (たとえば、ユーザーが設定したり、オンザフライで生成されたりする場合)、クラスを含む命令を与えるか、埋め込みを使用してどのクラス ラベルを確認するかによって、ゼロショット分類を試すことができます (または他の分類されたテキスト) は、テキスト ([Zero-shot_classification.ipynb](examples/Zero-shot_classification_with_embeddings.ipynb)) に最も類似しています。

#### エンティティ抽出

エンティティ抽出のプロンプトの例:

```text
以下のテキストから、次のエンティティを次の形式で抽出します。
会社: <記載されている会社のカンマ区切りリスト>
人物と役職: <言及された人物のコンマ区切りリスト (役職または役割を括弧内に追加)>

文章：
"""
1981 年 3 月、米国対 AT&T 事件は、ウィリアム バクスター司法次官補の下で裁判にかけられました。  
AT&T の会長であるチャールズ L. ブラウンは、会社が全滅すると考えていました。  
彼は AT&T が負けることを悟り、1981 年 12 月に司法省との交渉を再開しました。  
1 か月も経たないうちに合意に達し、ブラウンは売却に同意しました。これは、最良かつ唯一の現実的な選択肢です。  
AT&T の決定により、同社は研究部門と製造部門を維持することができました。  
最終判決の修正と題された法令は、1956 年 1 月 14 日の同意判決の調整であった。  
ハロルド H. グリーン判事は、修正された法令に対する権限を与えられた....

1982 年、米国政府は、AT&T が独占企業として存在しなくなると発表しました。  
1984 年 1 月 1 日、米国内の地域電話サービスを扱うために、ベル サウス、ベル アトランティック、NYNEX、  
アメリカン インフォメーション テクノロジーズ、サウスウェスタン ベル、US ウェスト、パシフィック テレシスの
7つの小さな地域企業に分割されました。距離サービスを提供していましたが、もはや競争から保護されていませんでした。
"""
```

Output:

```text
企業: United States v. AT&T、AT&T、司法省、Bell South、Bell Atlantic、NYNEX、American Information Technologies、Southwestern Bell、US West、Pacific Telesis
人物と役職: William Baxter (司法長官補佐)、Charles L. Brown (AT&T 会長)、Harold H. Greene (裁判官)
```

### 3. テキストを編集する

[completion API endpoint][Completion API Docs] に加えて、OpenAI は [edit API endpoint][Edit API Docs] を提供するようになりました ([blog post][GPT3 Edit Blog Post])。 1 つのテキスト入力のみを受け取る補完とは対照的に、編集は 2 つのテキスト入力 (指示と変更するテキスト) を受け取ります。

編集プロンプトの例:

命令入力:

```text
OCR エラーを修正する
```

テキスト入力:

```text
Therewassomehostilityntheenergybehindthe researchreportedinPerceptrons.... 
Part of ourdrivecame,aswequiteplainlyacknoweldgednourbook, 
fromhe facthatfundingndresearchnergywerebeingdissipatedon. . . 
misleadingttemptsouseconnectionistmethodsnpracticalappli-cations.
```

Output:

```text
There was some hostility in the energy behind the research reported in Perceptrons.... 
Part of our drive came, as we quite plainly acknowledged in our book, 
from the fact that funding and research energy were being dissipated on... 
misleading attempts to use connectionist methods in practical applications.
```

#### 翻訳

翻訳は、大規模な言語モデルのもう 1 つの新しい機能です。 2021 年には、 GPT-3 を使用して、WMT14 英仏ベンチマークで教師なし翻訳の最新記録を打ち立てました。

edits エンドポイントを使用した翻訳プロンプトの例:

命令入力:

```text
フランス語への翻訳
```

テキスト入力:

```text
That's life.
```

Output:

```text
C'est la vie.
```

補完エンドポイントを使用した翻訳プロンプトの例:

```text
次の文章を英語からフランス語に訳してください。

English: That's life.
French:
```

Output:

```text
C'est la vie.
```

翻訳のヒント:

* パフォーマンスは、最も一般的な言語で最高です
* 命令が最終言語で与えられた場合、より良いパフォーマンスが見られました (したがって、フランス語に翻訳する場合 `Translate the following text from English to French.` ではなく、`Traduire le texte de l'anglais au français.` という命令を与えます)。
* バックトランスレーション (ここで説明されているように) もパフォーマンスを向上させることができます
* コロンと重い句読点を含むテキストは、特に命令がコロンを使用している場合 (例 `English: {​​​​english text}​​​​ French:` )、命令に従うモデルを失敗させる可能性があります。
* edits エンドポイントは、翻訳と一緒にテキスト入力を繰り返すことがあることが確認されています。

翻訳に関して言えば、大規模な言語モデルは、翻訳と一緒に他の命令を組み合わせる際に特に優れています。たとえば、GPT-3 にスロベニア語を英語に翻訳するように依頼できますが、すべての LaTeX 組版コマンドは変更されません。次のノートブックは、スロベニアの数学の本を英語に翻訳した方法を詳しく説明しています。

[Translation of a Slovenian math book into English](examples/book_translation/translate_latex_book.ipynb)

### 4. テキストを比較する

[OpenAI API embeddings endpoint][Embeddings Docs] を使用して、テキスト間の類似性を測定できます ([blog post][Embeddings Blog Post])。 GPT-3 のテキストの理解を活用することで、これらの埋め込みは、教師なし学習と転移学習の両方の設定で、ベンチマークで最先端の結果を達成しました。

埋め込みは、セマンティック検索、レコメンデーション、クラスター分析、ほぼ重複の検出などに使用できます。

#### セマンティック検索

埋め込みは、単独で、または大規模なシステムの機能として検索に使用できます。

埋め込みを検索に使用する最も簡単な方法は次のとおりです。

* 検索前 (事前計算):
  * テキスト コーパスをトークン制限よりも小さいチャンクに分割します (例: <8,000 トークン)
  * 各チャンクを埋め込む
  * これらの埋め込みを独自のデータベースまたは [Pinecone](https://www.pinecone.io) や [Weaviate](https://weaviate.io) などのベクター検索プロバイダーに保存します
  * 
* 検索時 (ライブ コンピューティング):
  * 検索クエリを埋め込む
  * データベースで最も近い埋め込みを見つける
  * コサイン類似度でランク付けされた上位の結果を返します

[Semantic_text_search_using_embeddings.ipynb](examples/Semantic_text_search_using_embeddings.ipynb) に、埋め込みを検索に使用する方法の例が示されています。

より高度な検索システムでは、埋め込みのコサイン類似度を、検索結果のランク付けにおける多くの特徴の 1 つとして使用できます。

#### 推奨事項

レコメンデーションは検索とよく似ていますが、入力が自由形式のテキスト クエリではなく、セット内のアイテムである点が異なります。

レコメンデーションに埋め込みを使用する方法の例は、[Recommendation_using_embeddings.ipynb](examples/Recommendation_using_embeddings.ipynb) に示されています。

検索と同様に、これらのコサイン類似度スコアは、アイテムをランク付けするために単独で使用することも、より大きなランキング アルゴリズムの機能として使用することもできます。

#### 埋め込みのカスタマイズ

OpenAI の埋め込みモデルの重みを微調整することはできませんが、トレーニング データを使用してアプリケーションへの埋め込みをカスタマイズすることはできます。

次のノートブックでは、トレーニング データを使用して埋め込みをカスタマイズする方法の例を示します。この方法のアイデアは、新しいカスタマイズされた埋め込みを取得するために、埋め込みベクトルを乗算するようにカスタム マトリックスをトレーニングすることです。適切なトレーニング データを使用すると、このカスタム マトリックスはトレーニング ラベルに関連する特徴を強調表示し、残りを抑制します。行列の乗算は、(a) 埋め込みの修正、または (b) 埋め込み間の距離を測定するために使用される距離関数の修正と同等に考えることができます。

* [Customizing_embeddings.ipynb](examples/Customizing_embeddings.ipynb)

## コード機能

大規模な言語モデルはテキストだけでなく、コードにも優れています。 OpenAI の特殊なコード モデルは [Codex] と呼ばれます。

Codex は、以下を含む [70 以上の製品][Codex Apps Blog Post] に使用されています。

* [GitHub Copilot] (VS Code およびその他の IDE でコードをオートコンプリートします)
* [Pygma](https://pygma.app/) (Figma のデザインをコードに変換)
* [Replit](https://replit.com/) (「コードの説明」ボタンとその他の機能があります)
* [Warp](https://www.warp.dev/) （AIコマンド検索付きスマート端末）
* [Machinet](https://machinet.net/) (Java 単体テスト テンプレートを記述)

指示に従うテキスト モデル (例: text-davinci-003 ) とは異なり、Codex は指示に従うようにトレーニングされて *いない* ことに注意してください。その結果、優れたプロンプトを設計するには、より注意を払う必要があります。

### 1.コードを書く

`code-davinci-002` でコードを書くためのプロンプトの例:

```text
SQL テーブル (および列):
* 顧客(customer_id, signup_date)
* ストリーミング (customer_id、video_id、watch_date、watch_minutes)

2020年3月にサインアップし、最初の30日間で50時間以上のビデオを視聴した顧客を一覧表示する適切に作成された SQL クエリ:
```

Output:

```sql
SELECT c.customer_id
FROM Customers c
JOIN Streaming s
ON c.customer_id = s.customer_id
WHERE c.signup_date BETWEEN '2020-03-01' AND '2020-03-31'
AND s.watch_date BETWEEN c.signup_date AND DATE_ADD(c.signup_date, INTERVAL 30 DAY)
GROUP BY c.customer_id
HAVING SUM(s.watch_minutes) > 50 * 60
```

`code-davinci-002` は変数名から推測できます。たとえば、`watch_minutes` の単位は分であるため、50 時間と比較する前に 60 倍に変換する必要があると推測されます。

### 2. コードの説明

コードの説明は、多くのユース ケースに適用できます。

* コード内ドキュメントの生成 (例: Python docstring、git commit メッセージ)
* コード外のドキュメントの生成 (man ページなど)
* インタラクティブなコード探索ツールで
* 自然言語インターフェースを介してプログラムの結果をユーザーに伝える

`code-davinci-002` でコードを説明するプロンプトの例:

````text
SQL クエリ:
```
SELECT c.customer_id
FROM Customers c
JOIN Streaming s
ON c.customer_id = s.customer_id
WHERE c.signup_date BETWEEN '2020-03-01' AND '2020-03-31'
AND s.watch_date BETWEEN c.signup_date AND DATE_ADD(c.signup_date, INTERVAL 30 DAY)
GROUP BY c.customer_id
HAVING SUM(s.watch_minutes) > 50 * 60
```

質問:
1. SQL クエリは何をしますか?
2. なぜこの時期に興味を持つ人がいるのですか?
3. 企業がこの SQL クエリに関心を持つ理由は何ですか?

答え:
````

Output:

```text
1. SQL クエリは、2020 年 3 月にサインアップし、サインアップ後最初の 30 日間に 50 時間以上のコンテンツを視聴したすべての顧客を検索します。
2. COVID-19 パンデミックの最初の月であるため、この期間は興味深いものです。
3. 企業は、パンデミックが自社のビジネスにどのような影響を与えたかを理解するのに役立つため、この SQL クエリに関心を持っている可能性があります。
```

### 3.コードを編集する

OpenAI の edit エンドポイントは、コードの編集に特に役立ちます。

`code-davinci-edit-001` へのテキスト入力例:

```python
def tribonacci(n):
    if n == 0:
        return 0
    elif n == 1:
        return 1
    elif n == 2:
        return 1
    elif n == 3:
        return 2
    else:
        return tribonacci(n-1) + tribonacci(n-2) + tribonacci(n-3)
```

命令入力の例:

```text
ドキュメントストリングを追加する
入力を追加する
ランタイムを改善する
テストを追加する
JavaScript (または Rust、Lisp、または任意の言語) に翻訳します。
```

ランタイムを改善して JavaScript に変換した後の出力例:

```JavaScript
function tribonacci(n) {​​​​
  let a = 0;
  let b = 1;
  let c = 1;
  for (let i = 0; i < n; i++) {​​​​
    [a, b, c] = [b, c, a + b + c];
  }​​​​
  return a;
}​​​​
```

ご覧のとおり、`code-davinci-edit-001` は、関数の実行時間を指数関数から線形に短縮し、Python から JavaScript に変換することに成功しました。

### 4. コードを比較する

OpenAI API には、コード検索の埋め込み機能もあり、コードのセクションとテキスト クエリとの関連性、またはコードの 2 つのセクション間の類似性を測定できます。

OpenAI コード検索埋め込みは、[CodeSearchNet] 評価スイートの最先端を大幅に改善し、以前の記録である 77.4% に対して 93.5% のスコアを獲得しました。

OpenAI のコード埋め込みの詳細については、[ブログ投稿のお知らせ][Embeddings Blog Post]または[ドキュメント][Embeddings Docs]をご覧ください。

コードの埋め込みは、次のようなユース ケースに役立ちます。

* コード検索
* コードベースのクラスタリングと分析

コード検索の例は [Code_search.ipynb](examples/Code_search.ipynb) に示されています。

コード クラスタリングの例を書いていませんが、考え方は [Clustering.ipynb](examples/Clustering.ipynb) のテキスト クラスタリングと同じです。

[OpenAI API]: https://openai.com/api/
[Embeddings Docs]: https://beta.openai.com/docs/guides/embeddings
[Edit API Docs]: https://beta.openai.com/docs/api-reference/edits
[Completion API Docs]: https://beta.openai.com/docs/api-reference/completions
[Fine Tuning Docs]: https://beta.openai.com/docs/guides/fine-tuning
[CodeSearchNet]: https://github.com/github/CodeSearchNet
[Embeddings Blog Post]: https://openai.com/blog/introducing-text-and-code-embeddings/
[Codex Apps Blog Post]: https://openai.com/blog/codex-apps/
[GPT3 Edit Blog Post]: https://openai.com/blog/gpt-3-edit-insert/
[Large language models Blog Post]: https://openai.com/blog/better-language-models/
[GitHub Copilot]: https://copilot.github.com/
[Codex]: https://openai.com/blog/openai-codex/
[API Signup]: https://beta.openai.com/signup
[GPT3 Apps Blog Post]: https://openai.com/blog/gpt-3-apps/
[OpenAI Playground]: https://beta.openai.com/playground
[OpenAI Documentation]: https://beta.openai.com/docs/introduction
[OpenAI Community Forum]: https://community.openai.com/top?period=monthly
[OpenAI Help Center]: https://help.openai.com/en/
[OpenAI Examples]: https://beta.openai.com/examples

[OpenAI Cookbook]: https://github.com/102yuta/openai-cookbook-ja
