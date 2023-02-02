# テキストを書く

大規模な言語モデルは、テキストの記述に優れており、あらゆる種類の作業を支援することができます。

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

GPT-3を動かす最も簡単な方法は「何が欲しいか」を伝えることです。たとえば、電子メールを書いてほしいなら、次のようなプロンプトを使うことができます。

```text
ジルという名前の同僚に、彼女の昇進を祝うメールを書いてください。  
口調（トーン）は温かみがありながらもプロフェッショナルでなければなりません。  
彼女がこれまで取り組んできた仕事をどのように賞賛しているかを述べてください。  
彼女のペットのトカゲであるマックスがバッタを食べるのが好きだというジョークを含めてください。  
来週のチームのオフサイトをいかに楽しみにしているのかを述べてください。
```
Jill という名前の同僚に昇進を祝うメールを書いてください。口調は暖かく、かつプロフェッショナルであるべきです。
彼女の仕事ぶりに感心していることを述べましょう。 ペットのトカゲのMaxがバッタを好んで食べるというジョークも添えて。来週のチームオフサイトがいかに楽しみであるかを述べる。

[出力](https://beta.openai.com/playground/p/fUeh5saVLI2dhU0WU3nZtIiU):

```text
件名：ジル、昇進おめでとう

親愛なるジルへ

昇進おめでとう！私はあなたの素晴らしい仕事に感心しており、あなたの成功を本当に嬉しく思います.  
トカゲのマックスも一緒に祝っていることでしょう。バッタを食べるのが大好きだそうですから、特別におやつをご馳走してあげてくださいね。

来週のチームオフサイトでお会いできるのを楽しみにしています。きっと、皆さんの成功を祝う素晴らしい機会になると思います。

これからも頑張ってね。
```

一般に、ライティングは、指示であれ、従うべき一連の例であれ、どのようなスタイルのプロンプトでもうまくいきます。あなたの用途に最も適した方法を試してみてください。
また、ライティングは、どのようなタイプのモデルにも対応しますが、それぞれに長所と短所があります。

|                                                            | Advantages                                                                    | Disadvantages                                                                    |
| ---------------------------------------------------------- | ----------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| 命令に従うモデル<br>(e.g., `text-davinci-003`) | 最も使いやすい                                                                | あまり創造的ではありません。多様性が低い。トーン、長さなどのコントロールが難しい。  |
| ベースモデル<br>(e.g., `davinci`)                           | よりクリエイティブに                                                                 | より高価です（プロンプトで例のデモンストレーションを含めるとトークンが必要になるため） |
| 微調整されたモデル                                          | 多くの例から訓練できます。プロンプトに例を含めるよりも安価 | トレーニングデータの収集が難しい。トレーニングは反復を遅くし、より高価にします |

<!--
# Text writing examples

Large language models are excellent at writing. They can assist with all sorts of tasks:

* Blog posts
* Email copy
* Ad copy
* Website copy
* Product descriptions
* Memos
* Storytelling
* Brainstorming
* Question generation
* etc.

The easiest way to prompt GPT-3 is to tell it what you'd like. For example, if you want it to write an email, you could use a prompt like this:

```text
Write an email to a colleague named Jill congratulating her on her promotion. The tone should be warm yet professional. Mention how you admire the work she's been putting in.  Include a joke about how her pet lizard Max enjoys eating grasshoppers. Mention how you're looking forward to the team off-site next week.
```

[Output](https://beta.openai.com/playground/p/fUeh5saVLI2dhU0WU3nZtIiU):

```text
Subject: Congratulations on Your Promotion, Jill!

Dear Jill,

Congratulations on your promotion! I'm so proud of you and all the hard work you've been putting in. It's been inspiring to watch you grow in your career.

I'm sure Max the lizard is also celebrating with you. I hear he loves eating grasshoppers, so you should treat him to a special snack!

I'm looking forward to seeing you at the team off-site next week. I'm sure it will be a great opportunity to celebrate your success.

All the best,

[Your Name]
```

In general, writing can work with any style of prompt, whether it's an instruction or a series of examples to follow. Experiment to see what works best for your use case.

Writing also works with any type of model, though they each have strengths and weaknesses.

|                                                            | Advantages                                                                    | Disadvantages                                                                    |
| ---------------------------------------------------------- | ----------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| Instruction-following models<br>(e.g., `text-davinci-003`) | Easiest to use                                                                | Less diverse; less creative; sometimes harder to steer tone, style, etc.                |
| Base models<br>(e.g., `davinci`)                           | Potentially more creative and diverse                                                                 | Harder to prompt well, more expensive (as examples in the prompt cost extra tokens) |
| Fine-tuned models                                          | Can train off of many examples; cheaper than including examples in the prompt | Hard to gather training data; training makes iteration slower and more expensive |
-->
