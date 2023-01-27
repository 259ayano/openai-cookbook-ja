# テキストを編集する例

[completion API endpoint][Completion API Docs] に加えて、OpenAI は [edit API endpoint][Edit API Docs] を提供するようになりました ([blog post][GPT3 Edit Blog Post])。 1 つのテキスト入力のみを受け取る補完とは対照的に、編集は 2 つのテキスト入力 (指示と変更するテキスト) を受け取ります。

OpenAIでは、[completion API endpoint][Completion API Docs] に加えて、[edits API endpoint][Edit API Docs] が提供されています。詳しくは以下を参照してください。

* [Blog post announcement (Mar 2022)][GPT3 Edit Blog Post]
* [Edit API documentation][Edit API Docs]

補完はテキストを1つだけ入力しますが、編集は指示と変更するテキストの2つのテキストを入力します。例えば

指示の入力:

```text
OCR エラーを修正する
```

テキストの入力:

```text
Therewassomehostilityntheenergybehindthe researchreportedinPerceptrons.... 
Part of ourdrivecame,aswequiteplainlyacknoweldgednourbook, 
fromhe facthatfundingndresearchnergywerebeingdissipatedon. . . 
misleadingttemptsouseconnectionistmethodsnpracticalappli-cations.
```

出力:

```text
There was some hostility in the energy behind the research reported in Perceptrons.... 
Part of our drive came, as we quite plainly acknowledged in our book, 
from the fact that funding and research energy were being dissipated on... 
misleading attempts to use connectionist methods in practical applications.
```

一般に、指示は命令形、現在形、過去形のいずれでもかまいません。あなたの用途に合ったものを試してみてください。

## 翻訳

edit API の応用の1つに翻訳があります。

大規模な言語モデルは、一般的な言語間の翻訳に優れています。2021年には GPT-3 を使用して、WMT14 英仏ベンチマークで教師なし翻訳の最新記録を打ち立てました。

ここでは、editエンドポイントを使ってテキストを翻訳する例を紹介します。

指示の入力:

```text
フランス語への翻訳してください
```

テキストの入力:

```text
That's life.
```

Output:

```text
C'est la vie.
```

もちろん、editsエンドポイントで実現できる多くのタスクは、completionsエンドポイントでも実現可能です。例えば、次のような指示を前置きして翻訳を依頼することができます。

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

* 最も一般的な言語であれば、パフォーマンスが最も高くなります。
* 指示が最終言語で与えられている場合、我々はより良いパフォーマンスを見てきました。
（だからフランス語に翻訳する場合、`Translate the following text from English to French.` ではなく、`Traduire le texte de l'anglais au français.` という指示を与えて下さい）
* バックトランスレーション ([ここ](https://arxiv.org/abs/2110.05448)で説明されているように) によりパフォーマンスを向上させることができます。
* コロンや句読点が多いテキストは、特に命令がコロンを使用している場合 (例 `English: {​​​​english text}​​​​ French:` )、命令に従うモデルを失敗させる可能性があります。
* edits エンドポイントは、翻訳と一緒にテキスト入力を繰り返すことがあることが確認されています。
* 編集のエンドポイントでは、翻訳と一緒に元のテキスト入力が繰り返されることがありますが、これは監視とフィルタリングが可能です。


翻訳に関して言えば、大規模な言語モデルは、翻訳と一緒に他の指示を組み合わせることに特に優れています。例えば、GPT-3 にスロベニア語から英語への翻訳を依頼する際に、LaTeX の組版コマンドは変更しないようにすることができます。次のノートブックでは、スロベニア語の数学の本をどのように英語に翻訳したかを詳しく説明しています。

[Translation of a Slovenian math book into English](examples/book_translation/translate_latex_book.ipynb)

<!--
# Text editing examples

In addition to the [completions API endpoint][Completion API Docs], OpenAI offers an [edits API endpoint][Edit API Docs]. Read more at:

* [Blog post announcement (Mar 2022)][GPT3 Edit Blog Post]
* [Edit API documentation][Edit API Docs]

In contrast to completions, which only take a single text input, edits take two text inputs: the instruction and the text to be modified. For example:

Instruction input:

```text
Fix the OCR errors
```

Text input:

```text
Therewassomehostilityntheenergybehindthe researchreportedinPerceptrons....Part of ourdrivecame,aswequiteplainlyacknoweldgednourbook,fromhe facthatfundingndresearchnergywerebeingdissipatedon. . .misleadingttemptsouseconnectionistmethodsnpracticalappli-cations.
```

[Output](https://beta.openai.com/playground/p/5W5W6HHlHrGsLu1cpx0VF4qu):

```text
There was some hostility in the energy behind the research reported in Perceptrons....Part of our drive came, as we quite plainly acknowledged in our book, from the fact that funding and research energy were being dissipated on...misleading attempts to use connectionist methods in practical applications.
```

In general, instructions can be imperative, present tense, or past tense. Experiment to see what works best for your use case.

## Translation

One application of the edit API is translation.

Large language models are excellent at translating across common languages. In 2021, [GPT-3 set](https://arxiv.org/abs/2110.05448) a new state-of-the-art record in unsupervised translation on the WMT14 English-French benchmark.

Here's an example of how to translate text using the edits endpoint:

Instruction input:

```text
translation into French
```

Text input:

```text
That's life.
```

[Output](https://beta.openai.com/playground/p/6JWAH8a4ZbEafSDyRsSVdgKr):

```text
C'est la vie.
```

Of course, many tasks that can be accomplished with the edits endpoint can also be done by the completions endpoint too. For example, you can request a translate by prepending an instruction as follows:

```text
Translate the following text from English to French.

English: That's life.
French:
```

[Output](https://beta.openai.com/playground/p/UgaPfgjBNTRRPeNcMSNtGzcu):

```text
 C'est la vie.
```

Tips for translation:

* Performance is best on the most common languages
* We've seen better performance when the instruction is given in the final language (so if translating into French, give the instruction `Traduire le texte de l'anglais au français.` rather than `Translate the following text from English to French.`)
* Backtranslation (as described [here](https://arxiv.org/abs/2110.05448)) can also increase performance
* Text with colons and heavy punctuation can trip up the instruction-following models, especially if the instruction uses colons (e.g., `English: {english text} French:`)
* The edits endpoint sometimes repeats the original text input alongside the translation, which can be monitored and filtered

When it comes to translation, large language models particularly shine at combining other instructions alongside translation. For example, you can ask GPT-3 to translate Slovenian to English but keep all LaTeX typesetting commands unchanged. The following notebook details how we translated a Slovenian math book into English:

[Translation of a Slovenian math book into English](examples/book_translation/translate_latex_book.ipynb)
-->

[Edit API Docs]: https://beta.openai.com/docs/api-reference/edits
[Completion API Docs]: https://beta.openai.com/docs/api-reference/completions
[GPT3 Edit Blog Post]: https://openai.com/blog/gpt-3-edit-insert/
