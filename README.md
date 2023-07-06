# OpenAI Cookbook とは

[OpenAI Cookbook](https://github.com/openai/openai-cookbook) では、[OpenAI API] を使用して一般的なタスクを実行するためのサンプルコードを共有します。  
これらの例を実行するには、OpenAI アカウントとAPI キーが必要です。（[無料アカウントを作成](https://beta.openai.com/signup)）  
ほとんどのコード例は Python で記述されていますが、概念はどの言語でも適用できます。  

[![GitHubコードスペースで開く](https://github.com/codespaces/badge.svg)](https://github.com/codespaces/new?hide_repo_select=true&ref=main)

## 最近追加 / 更新された項目 🆕 ✨
- [Whisper prompting guide](examples/Whisper_prompting_guide.ipynb) [June 27, 2023]
- [Question answering using a search API and re-ranking](https://github.com/openai/openai-cookbook/blob/main/examples/Question_answering_using_a_search_API.ipynb) [June 16, 2023]
- [How to call functions with Chat models](https://github.com/openai/openai-cookbook/blob/main/examples/How_to_call_functions_with_chat_models.ipynb) [June 13, 2023]
- [ウェブ上の関連資料](#ウェブ上の関連資料) [May 22, 2023]
- [埋め込みの playground (streamlit app)](apps/embeddings-playground/README.md) [May 19, 2023]
- [ユニットテストを書くためにマルチステッププロンプトを使用する方法](examples/Unit_test_writing_using_a_multi-step_prompt.ipynb) [May 19, 2023]
- [DALL·E と Segment Anything を使ったダイナミックマスクの作り方](examples/dalle/How_to_create_dynamic_masks_with_DALL-E_and_Segment_Anything.ipynb) [May 19, 2023]

## ガイドとサンプル

* API の使い方
  * [レート制限の取り扱いについて](examples/How_to_handle_rate_limits.ipynb)
    * [レート制限にかからないようにする並列処理スクリプトの例](examples/api_request_parallel_processor.py)
  * [tiktokenを使ったトークンの数え方](examples/How_to_count_tokens_with_tiktoken.ipynb)
* GPT
  * [ChatGPTモデルへの入力のフォーマット方法](examples/How_to_format_inputs_to_ChatGPT_models.ipynb)
  * [完成品のストリーミング方法](examples/How_to_stream_completions.ipynb)
  * [ユニットテストを書くためにマルチステッププロンプトを使用する方法](examples/Unit_test_writing_using_a_multi-step_prompt.ipynb)
  * [ガイド: 大規模な言語モデルを操作する方法](how_to_work_with_large_language_models.md)
  * [ガイド: 信頼性を向上させるテクニック](techniques_to_improve_reliability.md)
* 埋め込み
  * [テキスト比較の例](text_comparison_examples.md)
  * [埋め込みを取得する方法](examples/Get_embeddings.ipynb)
  * [埋め込みを使用した質問応答](examples/Question_answering_using_embeddings.ipynb)
  * [埋め込み検索のためのベクトルデータベースの利用](examples/vector_databases/Using_vector_databases_for_embeddings_search.ipynb)
  * [埋め込みを使用したセマンティック検索](examples/Semantic_text_search_using_embeddings.ipynb)
  * [埋め込みを使用した推奨事項](examples/Recommendation_using_embeddings.ipynb)
  * [クラスタリング埋め込み](examples/Clustering.ipynb)
  * 埋め込みを[2D](examples/Visualizing_embeddings_in_2D.ipynb) または [3D](examples/Visualizing_embeddings_in_3D.ipynb)で視覚化する
  * [テキスト (長) の埋め込み](examples/Embedding_long_inputs.ipynb)
  * [埋め込みのplayground (streamlit app)](apps/embeddings-playground/README.md)
* アプリ
  * [ファイル Q&A](apps/file-q-and-a/)
  * [Webクロール Q&A](apps/web-crawl-q-and-a)
  * [ChatGPTと自社データで製品をパワーアップさせる](apps/chatbot-kickstarter/powering_your_products_with_chatgpt_and_your_data.ipynb)
* GPT-3の微調整
  * [ガイド:テキストを分類するためにGPT-3を微調整するためのベストプラクティス](https://docs.google.com/document/d/1rqj7dkuvl7Byd5KQPUJRxc19BJt8wo0yHNwK84KfU3Q/edit)
  * [微調整された分類](examples/Fine-tuned_classification.ipynb)
* DALL-E
  * [DALL·Eで画像を生成および編集する方法](examples/dalle/Image_generations_edits_and_variations_with_DALL-E.ipynb)
  * [DALL·EとSegment Anythingを使ったダイナミックマスクの作り方](examples/dalle/How_to_create_dynamic_masks_with_DALL-E_and_Segment_Anything.ipynb)
* Whisper
  - [Whisper prompting guide](examples/Whisper_prompting_guide.ipynb)
* Azure OpenAI (Microsoft Azureの代替API)
  * [Azure OpenAIでChatGPTを使う方法](examples/azure/chat.ipynb)
  * [Azure OpenAI から入力候補を取得する方法](examples/azure/completions.ipynb)
  * [Azure OpenAI から埋め込みを取得する方法](examples/azure/embeddings.ipynb)
  - [How to generate images with DALL·E fom Azure OpenAI](examples/azure/DALL-E.ipynb)
  - 
## 関連する OpenAI のリソース

ここにあるコード例以外にも、次のリソースから [OpenAI API] について学ぶことができます。

* [ChatGPT]を使った実験 
* [OpenAI Playground] のAPIをお試す
* [OpenAI Documentation] で API について読む
* [OpenAI Help Center] で助けてもらう
* [OpenAI Community Forum] または[OpenAI Discord channel]でAPIについて議論する
* [OpenAI Examples] でプロンプトの例を参照にする
* [OpenAI Blog]で最新情報を入手する

## ウェブ上の関連資料

GPTの出力を向上させるために、人々は素晴らしいツールや論文を書いています。ここでは、私たちが目にしたクールなものをいくつか紹介します：

### プロンプトライブラリ＆ツール

- [Guidance](https://github.com/microsoft/guidance): Microsoftが提供する便利そうなPythonライブラリで、Handlebarsテンプレートを使って生成、プロンプト、論理制御をインターリーブしています。
- [LangChain](https://github.com/hwchase17/langchain): 言語モデルプロンプトのシーケンスを連鎖させるための一般的なPython/JavaScriptライブラリです。
- [FLAML (A Fast Library for Automated Machine Learning & Tuning)](https://microsoft.github.io/FLAML/docs/Getting-Started/): モデル、ハイパーパラメータ、その他の調整可能な選択肢の選択を自動化するためのPythonライブラリです。
- [Chainlit](https://docs.chainlit.io/overview): チャットボットのインターフェースを作るためのPythonライブラリです。
- [Guardrails.ai](https://shreyar.github.io/guardrails/): 出力を検証し、失敗を再試行するための Python ライブラリです。まだアルファ版なので、鋭利な部分やバグがあることを予測してください。
- [Semantic Kernel](https://devblogs.microsoft.com/semantic-kernel/): Microsoftが提供するPython/C#ライブラリで、プロンプトテンプレート、関数チェイニング、ベクトル化メモリ、インテリジェントプランニングをサポートしています。
- [Outlines](https://github.com/normal-computing/outlines)： プロンプトと制約の生成を簡略化するためのドメイン固有言語を提供するPythonライブラリ。
- [Promptify](https://github.com/promptslab/Promptify): 言語モデルを使用してNLPタスクを実行するための小さなPythonライブラリです。
- [Scale Spellbook](https://scale.com/spellbook): 言語モデルアプリを構築、比較、出荷するための有償製品です。
- [PromptPerfect](https://promptperfect.jina.ai/prompts): プロンプトをテスト・改善するための有償製品です。
- [Weights & Biases](https://wandb.ai/site/solutions/llmops): トラッキングモデルのトレーニングやプロンプトエンジニアリング実験用の有償製品です。
- [OpenAI Evals](https://github.com/openai/evals): 言語モデルやプロンプトのタスク性能を評価するためのオープンソースライブラリです。
- [LlamaIndex](https://github.com/jerryjliu/llama_index): LLMアプリをプライベートデータ（個人、組織）で補強するためのPythonライブラリです。
- [Arthur Shield](https://www.arthur.ai/get-started): A paid product for detecting toxicity, hallucination, prompt injection, etc.
- [LMQL](https://lmql.ai): A programming language for LLM interaction with support for typed prompting, control flow, constraints, and tools.
- 
### プロンプティングガイド

- [Brex's Prompt Engineering Guide](https://github.com/brexhq/prompt-engineering): ブレックスの言語モデルやプロンプトエンジニアリングの紹介です。
- [promptingguide.ai](https://www.promptingguide.ai/): 多くのテクニックを披露するプロンプトエンジニアリングガイドです。
- [OpenAI Cookbook: Techniques to improve reliability](techniques_to_improve_reliability.md): 言語モデルをプロンプト化する技術について、少し古い（2022年9月）レビューです。
- [Lil'Log Prompt Engineering](https://lilianweng.github.io/posts/2023-03-15-prompt-engineering/): OpenAI研究員によるプロンプトエンジニアリング文献のレビューです。（2023年3月現在）。
- [learnprompting.org](https://learnprompting.org/): プロンプトエンジニアリングの入門コースです。

### ビデオ講座

- [Andrew Ng's DeepLearning.AI](https://www.deeplearning.ai/short-courses/chatgpt-prompt-engineering-for-developers/): 開発者のためのプロンプトエンジニアリング短期集中講座です。
- [Andrej Karpathy's Let's build GPT](https://www.youtube.com/watch?v=kCc8FmEb1nY): GPTの基礎となる機械学習を詳しく解説します。
- [Prompt Engineering by DAIR.AI](https://www.youtube.com/watch?v=dOxUroR57xs): プロンプトエンジニアリングの様々なテクニックを1時間のビデオで紹介します。

### 推論力向上のための高度なプロンプトに関する論文

- [Chain-of-Thought Prompting Elicits Reasoning in Large Language Models (2022)](https://arxiv.org/abs/2201.11903): 数発のプロンプトで、モデルに段階的に考えさせることで、推理力を向上させる。PaLMの数学の単語問題（GSM8K）のスコアが18%から57%に向上しています。
- [Self-Consistency Improves Chain of Thought Reasoning in Language Models (2022)](https://arxiv.org/abs/2203.11171): 複数の出力から投票することで、さらに精度が向上します。40の出力から投票することで、PaLMの数学の単語問題のスコアは57%から74%に、`code-davinci-002`は60%から78%にさらに向上しています。
- [Tree of Thoughts: Deliberate Problem Solving with Large Language Models (2023)](https://arxiv.org/abs/2305.10601): ステップバイステップの推論のツリーを検索することは、思考の鎖を投票すること以上に役立ちます。GPT-4`の創作活動やクロスワードのスコアを引き上げています。
- [Language Models are Zero-Shot Reasoners (2022)](https://arxiv.org/abs/2205.11916): 指示追従型モデルに段階的に考えるよう指示することで、推理力が向上します。text-davinci-002`の数学の単語問題（GSM8K）のスコアを13%から41%に引き上げます。
- [Large Language Models Are Human-Level Prompt Engineers (2023)](https://arxiv.org/abs/2211.01910): プロンプトの候補を自動検索したところ、数学の単語問題（GSM8K）のスコアを43%に引き上げ、「言語モデルはゼロショット推論機」の人力プロンプトを2ポイント上回るプロンプトを発見しました。
- [Reprompting: Automated Chain-of-Thought Prompt Inference Through Gibbs Sampling (2023)](https://arxiv.org/abs/2305.09993):ChatGPTのスコアは、いくつかのベンチマークで0～20%ポイント向上しました。
- [Faithful Reasoning Using Large Language Models (2022)](https://arxiv.org/abs/2208.14271): 選択と推論のプロンプトによって生成される思考の連鎖、選択と推論のループを停止するタイミングを選択するハルターモデル、複数の推論経路を探索する価値関数、幻覚を避けるための文章ラベルなどを組み合わせたシステムによって、推論を改善することができます。
- [STaR: Bootstrapping Reasoning With Reasoning (2022)](https://arxiv.org/abs/2203.14465): 思考の連鎖の推論は、ファインチューニングによってモデルに焼き付けることができます。答えのあるタスクの場合、言語モデルによって思考の連鎖の例を生成することができます。
- [ReAct: Synergizing Reasoning and Acting in Language Models (2023)](https://arxiv.org/abs/2210.03629): 道具や環境があるタスクの場合、「Re（推論）」（何をすべきか考える）と「Act（演技）」（道具や環境から情報を得る）を規定的に交互に行うことで、思考の連鎖がうまく機能します。
- [Reflexion: an autonomous agent with dynamic memory and self-reflection (2023)](https://arxiv.org/abs/2303.11366): 過去の失敗を記憶している状態でタスクに再挑戦すると、その後のパフォーマンスが向上します。
- [Demonstrate-Search-Predict: Composing retrieval and language models for knowledge-intensive NLP (2023)](https://arxiv.org/abs/2212.14024): 「検索して読む」によって知識を増強したモデルは、マルチホップチェーンの検索で改善することができます。
- [Improving Factuality and Reasoning in Language Models through Multiagent Debate (2023)](https://arxiv.org/abs/2305.14325): 数人のChatGPTエージェントが数ラウンドにわたってディベートを行うことで、様々なベンチマークのスコアが向上しました。数学の単語問題のスコアは77%から85%に上昇しました。

## 貢献する

見てみたい例やガイドがあれば、[issues page]で気軽に提案してください。また、レポの範囲に合うものであれば、質の高いプルリクエストを喜んでお受けします。

[ChatGPT]: https://chat.openai.com/
[OpenAI API]: https://openai.com/api/
[API Signup]: https://beta.openai.com/signup
[OpenAI Playground]: https://beta.openai.com/playground
[OpenAI Documentation]: https://beta.openai.com/docs/introduction
[OpenAI Community Forum]: https://community.openai.com/top?period=monthly
[openai discord channel]: https://discord.com/invite/openai
[OpenAI Help Center]: https://help.openai.com/en/
[OpenAI Examples]: https://beta.openai.com/examples
[OpenAI Blog]: https://openai.com/blog/
[issues page]: https://github.com/openai/openai-cookbook/issues

![badge](https://img.shields.io/endpoint.svg?url=https%3A%2F%2Fgezf7g7pd5.execute-api.ap-northeast-1.amazonaws.com%2Fdefault%2Fsource_up_to_date%3Fowner%3Dopenai%26repos%3Dopenai-cookbook%26ref%3Dmain%26path%3DREADME.md%26commit_hash%3D59c12ef6dc5ce21ed1f0c83042a70dfeb88084ed)


