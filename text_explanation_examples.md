# テキストを説明する例

大規模な言語モデルは、長いテキストから情報を抽出するのに有効です。その用途は以下の通りです。

* テキストについての質問に答える例
  * 知らないことを調べるためにナレッジベースへ問い合わせをする
  * 見慣れないドキュメントを照会して、その中身を理解する
  * タグ、クラス、エンティティなどを抽出するために、構造化された質問でドキュメントをクエリする
* テキストを要約する例
  * 長い文書を要約する
  * 電子メールのやりとりやメッセージスレッドの要約する
  * 重要なポイントと次のステップを含む詳細な会議メモの要約する
* テキストを分類する例
  * 顧客からのフィードバック メッセージをトピックまたはタイプ別に分類
  * トピックまたはタイプによるドキュメントの分類
  * テキストのトーンまたは感情の分類
* エンティティを抽出する例
  * 顧客メッセージから連絡先情報を抽出する
  * 文書から人名、会社名、製品名を抽出する
  * 顧客レビューやフィードバックに記載されている事柄の抽出

以下は、それぞれの簡単な例です。

## テキストの一部に関する質問に答える

以下は、テキストの一部についての質問に答えるプロンプトの例です。


```text
次のテキストを使って質問に答えてください。もし答えがテキストに含まれていなければ、"わからない"と言ってください。

テキスト
"""
中央アフリカの西海岸にあるガボンのオクロにあるオクロ鉱山（オクロリアクターまたはオクロマインということもある）は、唯一の天然の核分裂炉であると考えられている。
オクロは、約17億年前に自立した核分裂反応が起こり、数十万年続いたとされる16カ所の遺跡から構成されている。その間の熱出力は平均100kW以下と推定されている。
"""

質問です。天然の核分裂炉は今までいくつ発見されているのでしょうか？

答え
```

[出力](https://beta.openai.com/playground/p/c8ZL7ioqKK7zxrMT2T9Md3gJ)。

```text
ひとつ。オクロ鉱山は、唯一の天然核分裂炉と考えられている。
```

質問したいテキストがトークン制限（`text-davinci-002`/`-003`では〜4000トークン、それ以前のモデルでは〜2000トークン）より長い場合、テキストを細かく分割して関連性でランク付けし、最も関連性の高そうな部分のみを使用して質問することができます。これは[Question_answering_using_embeddings.ipynb](examples/Question_answering_using_embeddings.ipynb)で実証されています。

学生がノートにアクセスできるようにするとテストの成績が良くなるのと同じように、GPT-3 は答えを含むテキストを与えられると質問にうまく答えることができるようになります。
メモがない場合、GPT-3 は自身の長期記憶（内部重み）に頼らざるを得ず、答えが混乱したり幻覚を見たりしやすくなります。

## 要約する

以下はテキストを要約するための簡単なプロンプトの例です。

```text
次のテキストを要約してください。

テキスト
"""
スイスのジュネーブに近いヨーロッパの高エネルギー物理学研究所であるCERNで、今朝二つの独立した実験がその結果を報告されました。両方とも、約125ギガ電子ボルトの重さの新しいボソン粒子の説得力のある証拠を示しており、これまでのところ、理論物理学者によって以前になされたヒッグスの予測に適合しています。

素人の私が言うのもなんですが、"我々はボソン粒子を発見した"。あなたはそう思いますか? CERN のロルフ・ディーター・ホイヤー事務局長は満員の聴衆にそう問いかけた。そこに集まった物理学者たちは拍手喝采を浴びた。
"""

要約：
```

[出力](https://beta.openai.com/playground/p/pew7DNB908TkUYiF0ZOdaIGc):

```text
CERN の事務局長は、満員の聴衆に向かって二つの独立した実験がヒッグス粒子の予言に合致する新しいボゾン粒子の説得力のある証拠を発見したことに同意するかどうかを尋ね、そこに集まった物理学者たちは拍手でそれに応えたのである。
```

GPT-3は、`<>`、`{}`、`###`など、ほとんどの区切り文字を認識することができます。長い文章の場合、あるセクションの終わりと次のセクションの始まりを明確にするために、何らかのデリミタを使用することをお勧めします。

## 分類する

テキストを分類したい場合、最適なアプローチはクラスが事前に分かっているかどうかによります。

クラスが事前に分かっている場合、[Fine-tuned_classification.ipynb](examples/Fine-tuned_classification.ipynb) で示したように、分類には微調整を行ったモデルが最適な場合があります。

クラスが事前にわからない場合（例えば、ユーザーによって設定されたり、その場で生成されたりする場合）、クラスを含む命令を与えるか、あるいは、どのクラスラベル（または他の分類されたテキスト）がテキストに最も似ているかを見るために、埋め込みを使ってゼロショット分類を試すことができます。
（ [Zero-shot_classification.ipynb](examples/Zero-shot_classification_with_embeddings.ipynb) でデモンストレーションされています）

## エンティティ抽出

以下はエンティティ抽出のプロンプト例です。

```text
以下のテキストから、以下の形式でエンティティを抽出します。
企業。<コンマで区切られた言及された企業のリスト
人物と肩書き <コンマで区切られた言及された人物のリスト (括弧内にタイトルまたはロールが付加されている)>。

テキスト
"""
1981年3月、United States v. AT&Tは、William Baxter 司法長官補佐官のもとで裁判が行われることになった。AT&T の会長 Charles L. Brown は、会社が根こそぎ潰されると思った。彼は、AT&T が負けることを悟り、1981年12月に司法省との交渉を再開した。そして1981年12月、AT&T が負けることを覚悟で、司法省との交渉を再開し、1ヵ月もしないうちにブラウン会長は現実的かつ最善の方法である「会社分割」に合意した。この決定により AT&T は研究・製造部門を維持することができた。最終判決の修正と題されたこの判決は、1956年1月14日に出された同意判決を修正したものである。Harold H. Greene 判事が、この修正された判決に対する権限を与えられた....

1982年、アメリカ政府はAT&Tが独占的な存在でなくなることを発表した。1984年1月1日、米国内の地域電話サービスを扱うため、Bell South、Bell Atlantic、NYNEX、American Information Technologies、Southwestern Bell、US West、Pacific Telesisの7つの小さな地域会社に分割された。AT&Tは長距離サービスの支配権を保持するが、競争から守られることはもはやなかった。
"""
```

[出力](https://beta.openai.com/playground/p/of47T7N5CtHF4RlvwFkTu3pN)

``テキスト
企業 AT&T、ベルサウス、ベルアトランティック、NYNEX、アメリカンインフォメーションテクノロジー、サウスウエスタンベル、USウエスト、パシフィックテレシス
人物と肩書き ウィリアム・バクスター（司法長官補佐官）、チャールズ・L・ブラウン（AT&T会長）、ハロルド・H・グリーン（判事）。


<!--
# Text explanation examples

Large language models are useful for distilling information from long texts. Applications include:

* Answering questions about a piece of text, e.g.:
  * Querying an knowledge base to help people look up things they don't know
  * Querying an unfamiliar document to understand what it contains
  * Querying a document with structured questions in order to extract tags, classes, entities, etc.
* Summarizing text, e.g.:
  * Summarizing long documents
  * Summarizing back-and-forth emails or message threads
  * Summarizing detailed meeting notes with key points and next steps
* Classifying text, e.g.:
  * Classifying customer feedback messages by topic or type
  * Classifying documents by topic or type
  * Classifying the tone or sentiment of text
* Extracting entities, e.g.:
  * Extracting contact information from a customer message
  * Extracting names of people or companies or products from a document
  * Extracting things mentioned in customer reviews or feedback

Below are some simple examples of each.

## Answering questions about a piece of text

Here's an example prompt for answering questions about a piece of text:

```text
Using the following text, answer the following question. If the answer is not contained within the text, say "I don't know."

Text:
"""
Oklo Mine (sometimes Oklo Reactor or Oklo Mines), located in Oklo, Gabon on the west coast of Central Africa, is believed to be the only natural nuclear fission reactor. Oklo consists of 16 sites at which self-sustaining nuclear fission reactions are thought to have taken place approximately 1.7 billion years ago, and ran for hundreds of thousands of years. It is estimated to have averaged under 100 kW of thermal power during that time.
"""

Question: How many natural fission reactors have ever been discovered?

Answer:
```

[Output](https://beta.openai.com/playground/p/c8ZL7ioqKK7zxrMT2T9Md3gJ):

```text
 One. Oklo Mine is believed to be the only natural nuclear fission reactor.
```

If the text you wish to ask about is longer than the token limit (~4,000 tokens for `text-davinci-002`/`-003` and ~2,000 tokens for earlier models), you can split the text into smaller pieces, rank them by relevance, and then ask your question only using the most-relevant-looking pieces. This is demonstrated in [Question_answering_using_embeddings.ipynb](examples/Question_answering_using_embeddings.ipynb).

In the same way that students do better on tests when allowed to access notes, GPT-3 does better at answering questions when it's given text containing the answer.
Without notes, GPT-3 has to rely on its own long-term memory (i.e., internal weights), which are more prone to result in confabulated or hallucinated answers.

## Summarization

Here's a simple example prompt to summarize a piece of text:

```text
Summarize the following text.

Text:
"""
Two independent experiments reported their results this morning at CERN, Europe's high-energy physics laboratory near Geneva in Switzerland. Both show convincing evidence of a new boson particle weighing around 125 gigaelectronvolts, which so far fits predictions of the Higgs previously made by theoretical physicists.

"As a layman I would say: 'I think we have it'. Would you agree?" Rolf-Dieter Heuer, CERN's director-general, asked the packed auditorium. The physicists assembled there burst into applause.
"""

Summary:
```

[Output](https://beta.openai.com/playground/p/pew7DNB908TkUYiF0ZOdaIGc):

```text
CERN's director-general asked a packed auditorium if they agreed that two independent experiments had found convincing evidence of a new boson particle that fits predictions of the Higgs, to which the physicists assembled there responded with applause.
```

The triple quotation marks `"""` used in these example prompts aren't special; GPT-3 can recognize most delimiters, including `<>`, `{}`, or `###`. For long pieces of text, we recommend using some kind of delimiter to help disambiguate where one section of text ends and the next begins.

## Classification

If you want to classify the text, the best approach depends on whether the classes are known in advance.

If your classes _are_ known in advance, classification is often best done with a fine-tuned model, as demonstrated in [Fine-tuned_classification.ipynb](examples/Fine-tuned_classification.ipynb).

If your classes are not known in advance (e.g., they are set by a user or generated on the fly), you can try zero-shot classification by either giving an instruction containing the classes or even by using embeddings to see which class label (or other classified texts) are most similar to the text (as demonstrated in [Zero-shot_classification.ipynb](examples/Zero-shot_classification_with_embeddings.ipynb)).

## Entity extraction

Here's an example prompt for entity extraction:

```text
From the text below, extract the following entities in the following format:
Companies: <comma-separated list of companies mentioned>
People & titles: <comma-separated list of people mentioned (with their titles or roles appended in parentheses)>

Text:
"""
In March 1981, United States v. AT&T came to trial under Assistant Attorney General William Baxter. AT&T chairman Charles L. Brown thought the company would be gutted. He realized that AT&T would lose and, in December 1981, resumed negotiations with the Justice Department. Reaching an agreement less than a month later, Brown agreed to divestiture—the best and only realistic alternative. AT&T's decision allowed it to retain its research and manufacturing arms. The decree, titled the Modification of Final Judgment, was an adjustment of the Consent Decree of 14 January 1956. Judge Harold H. Greene was given the authority over the modified decree....

In 1982, the U.S. government announced that AT&T would cease to exist as a monopolistic entity. On 1 January 1984, it was split into seven smaller regional companies, Bell South, Bell Atlantic, NYNEX, American Information Technologies, Southwestern Bell, US West, and Pacific Telesis, to handle regional phone services in the U.S. AT&T retains control of its long distance services, but was no longer protected from competition.
"""
```

[Output](https://beta.openai.com/playground/p/of47T7N5CtHF4RlvwFkTu3pN):

```text

Companies: AT&T, Bell South, Bell Atlantic, NYNEX, American Information Technologies, Southwestern Bell, US West, Pacific Telesis
People & titles: William Baxter (Assistant Attorney General), Charles L. Brown (AT&T chairman), Harold H. Greene (Judge)
```
-->
