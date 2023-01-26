# 大規模言語モデルの扱い方
## 大規模言語モデルの仕組み

大規模な言語モデルは、テキストをテキストにマップする関数です。テキストの入力文字列が与えられると、大規模な言語モデルが次に来るテキストを予測しようとします。

大規模な言語モデルの魔法は、膨大な量のテキストでこの予測エラーを最小限に抑えるようにトレーニングすることで、モデルが最終的にこれらの予測に役立つ概念を学習することです。たとえば、次のような概念を学びます。

* スペルの書き方
* 文法のしくみ
* どのように言い換えるか
* 質問にどう答えるか
* 会話を続け方
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

十分なトレーニング例があれば、カスタムモデルを微調整できます。この場合、モデルは提供されたトレーニングデータからタスクを学習できるため、指示は不要になります。ただし、プロンプトが終了して出力を開始するタイミングをモデルに伝えるために、セパレータシーケンス (例: ->または###または入力に一般的に表示されない任意の文字列) を含めると役立つ場合があります。セパレータシーケンスがないと、モデルはあなたが見たい答えに着手するのではなく、入力テキストを推敲し続ける危険性があります。

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

## コード機能

大規模な言語モデルはテキストだけでなく、コードも得意とします。OpenAI の専門的なコードモデルは [Codex] と呼ばれています。

Codex は、以下を含む [70 以上の製品][Codex Apps Blog Post] に使用されています。

* [GitHub Copilot] (VS Code およびその他の IDE でコードをオートコンプリートします)
* [Pygma](https://pygma.app/) (Figma のデザインをコードに変換)
* [Replit](https://replit.com/) (「コードの説明」ボタンとその他の機能があります)
* [Warp](https://www.warp.dev/) （AIコマンド検索付きスマート端末）
* [Machinet](https://machinet.net/) (Java 単体テスト テンプレートを記述)

指示に従うテキスト モデル (例: text-davinci-003 ) とは異なり、Codex は指示に従うようにトレーニングされて *いない* ことに注意してください。その結果、優れたプロンプトを設計するには、より注意を払う必要があります。

### その他のプロンプトアドバイス

その他のプロンプトの例については、[OpenAI Examples] をご覧ください。

一般的に、入力プロンプトはモデルの出力を向上させるための最良のレバーです。以下のようなトリックを試すことができます。

* **より明示的な指示を与える。** 例えば、カンマ区切りのリストを出力させたい場合は、カンマ区切りのリストを返すように指示します。答えがわからないときに「わからない」と言わせたい場合は「答えがわからないときは "わからない" と言ってください」と指示します。
* **よりよい例を与えて下さい。** プロンプトで例を示す場合は、例が多様で質の高いものであることを確認します。
* **専門家であるかのように答えるようにモデルに依頼する。** モデルに高品質な出力や専門家が書いたような出力を明示的に求めると、モデルは専門家が書いたと思うような高品質の答えを出すようになります。例えば、"次の答えは正しく、高品質で、専門家によって書くようにしてください。"
* **モデルにその理由を説明する一連のステップを書き出すように促す。** 例えば、回答の前に "Let's think step by step. "のような言葉を添えます。最終的な答えの前に、モデルに推論の説明をするよう促すことで、最終的な答えが一貫した正しいものである可能性を高めることができます。

<!--
# How to work with large language models

## How large language models work

[Large language models][Large language models Blog Post] are functions that map text to text. Given an input string of text, a large language model predicts the text that should come next.

The magic of large language models is that by being trained to minimize this prediction error over vast quantities of text, the models end up learning concepts useful for these predictions. For example, they learn:

* how to spell
* how grammar works
* how to paraphrase
* how to answer questions
* how to hold a conversation
* how to write in many languages
* how to code
* etc.

None of these capabilities are explicitly programmed in—they all emerge as a result of training.

GPT-3 powers [hundreds of software products][GPT3 Apps Blog Post], including productivity apps, education apps, games, and more.

## How to control a large language model

Of all the inputs to a large language model, by far the most influential is the text prompt.

Large language models can be prompted to produce output in a few ways:

* **Instruction**: Tell the model what you want
* **Completion**: Induce the model to complete the beginning of what you want
* **Demonstration**: Show the model what you want, with either:
  * A few examples in the prompt
  * Many hundreds or thousands of examples in a fine-tuning training dataset

An example of each is shown below.

### Instruction prompts

Instruction-following models (e.g., `text-davinci-003` or any model beginning with `text-`) are specially designed to follow instructions. Write your instruction at the top of the prompt (or at the bottom, or both), and the model will do its best to follow the instruction and then stop. Instructions can be detailed, so don't be afraid to write a paragraph explicitly detailing the output you want.

Example instruction prompt:

```text
Extract the name of the author from the quotation below.

“Some humans theorize that intelligent species go extinct before they can expand into outer space. If they're correct, then the hush of the night sky is the silence of the graveyard.”
― Ted Chiang, Exhalation
```

Output:

```text
Ted Chiang
```

### Completion prompt example

Completion-style prompts take advantage of how large language models try to write text they think is mostly likely to come next. To steer the model, try beginning a pattern or sentence that will be completed by the output you want to see. Relative to direct instructions, this mode of steering large language models can take more care and experimentation. In addition, the models won't necessarily know where to stop, so you will often need stop sequences or post-processing to cut off text generated beyond the desired output.

Example completion prompt:

```text
“Some humans theorize that intelligent species go extinct before they can expand into outer space. If they're correct, then the hush of the night sky is the silence of the graveyard.”
― Ted Chiang, Exhalation

The author of this quote is
```

Output:

```text
 Ted Chiang
```

### Demonstration prompt example (few-shot learning)

Similar to completion-style prompts, demonstrations can show the model what you want it to do. This approach is sometimes called few-shot learning, as the model learns from a few examples provided in the prompt.

Example demonstration prompt:

```text
Quote:
“When the reasoning mind is forced to confront the impossible again and again, it has no choice but to adapt.”
― N.K. Jemisin, The Fifth Season
Author: N.K. Jemisin

Quote:
“Some humans theorize that intelligent species go extinct before they can expand into outer space. If they're correct, then the hush of the night sky is the silence of the graveyard.”
― Ted Chiang, Exhalation
Author:
```

Output:

```text
 Ted Chiang
```

### Fine-tuned prompt example

With enough training examples, you can [fine-tune][Fine Tuning Docs] a custom model. In this case, instructions become unnecessary, as the model can learn the task from the training data provided. However, it can be helpful to include separator sequences (e.g., `->` or `###` or any string that doesn't commonly appear in your inputs) to tell the model when the prompt has ended and the output should begin. Without separator sequences, there is a risk that the model continues elaborating on the input text rather than starting on the answer you want to see.

Example fine-tuned prompt (for a model that has been custom trained on similar prompt-completion pairs):

```text
“Some humans theorize that intelligent species go extinct before they can expand into outer space. If they're correct, then the hush of the night sky is the silence of the graveyard.”
― Ted Chiang, Exhalation

###


```

Output:

```text
 Ted Chiang
```

## Code Capabilities

Large language models aren't only great at text - they can be great at code too. OpenAI's specialized code model is called [Codex].

Codex powers [more than 70 products][Codex Apps Blog Post], including:

* [GitHub Copilot] (autocompletes code in VS Code and other IDEs)
* [Pygma](https://pygma.app/) (turns Figma designs into code)
* [Replit](https://replit.com/) (has an 'Explain code' button and other features)
* [Warp](https://www.warp.dev/) (a smart terminal with AI command search)
* [Machinet](https://machinet.net/) (writes Java unit test templates)

Note that unlike instruction-following text models (e.g., `text-davinci-002`), Codex is *not* trained to follow instructions. As a result, designing good prompts can take more care.

### More prompt advice

For more prompt examples, visit [OpenAI Examples][OpenAI Examples].

In general, the input prompt is the best lever for improving model outputs. You can try tricks like:

* **Give more explicit instructions.** E.g., if you want the output to be a comma separated list, ask it to return a comma separated list. If you want it to say "I don't know" when the it doesn't know the answer, tell it 'Say "I don't know" if you do not know the answer.'
* **Supply better examples.** If you're demonstrating examples in your prompt, make sure that your examples are diverse and high quality.
* **Ask the model to answer as if it was an expert.** Explicitly asking the model to produce high quality output or output as if it was written by an expert can induce the model to give higher quality answers that it thinks an expert would write. E.g., "The following answer is correct, high-quality, and written by an expert."
* **Prompt the model to write down the series of steps explaining its reasoning.** E.g., prepend your answer with something like "[Let's think step by step](https://arxiv.org/pdf/2205.11916v1.pdf)." Prompting the model to give an explanation of its reasoning before its final answer can increase the likelihood that its final answer is consistent and correct.
-->


[Fine Tuning Docs]: https://beta.openai.com/docs/guides/fine-tuning
[Codex Apps Blog Post]: https://openai.com/blog/codex-apps/
[Large language models Blog Post]: https://openai.com/blog/better-language-models/
[GitHub Copilot]: https://copilot.github.com/
[Codex]: https://openai.com/blog/openai-codex/
[GPT3 Apps Blog Post]: https://openai.com/blog/gpt-3-apps/
[OpenAI Examples]: https://beta.openai.com/examples
