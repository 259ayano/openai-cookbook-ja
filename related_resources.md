# ウェブ上の関連リソース

GPT からのアウトプットを改善するための素晴らしいツールや論文を書いている人がいる。私たちが目にしたクールなものをいくつか紹介します：

## プロンプトライブラリとツール (アルファベット順)

- [Arthur Shield](https://www.arthur.ai/get-started): A paid product for detecting toxicity, hallucination, prompt injection, etc.
- [Chainlit](https://docs.chainlit.io/overview): チャットボットのインターフェースを作るためのPythonライブラリです。
- [FLAML (A Fast Library for Automated Machine Learning & Tuning)](https://microsoft.github.io/FLAML/docs/Getting-Started/): モデル、ハイパーパラメータ、その他の調整可能な選択肢の選択を自動化するためのPythonライブラリです。
- [Guardrails.ai](https://shreyar.github.io/guardrails/): 出力を検証し、失敗を再試行するための Python ライブラリです。まだアルファ版なので、鋭利な部分やバグがあることを予測してください。
- [Guidance](https://github.com/microsoft/guidance): Microsoftが提供する便利そうなPythonライブラリで、Handlebarsテンプレートを使って生成、プロンプト、論理制御をインターリーブしています。
- [Haystack](https://github.com/deepset-ai/haystack): Open-source LLM orchestration framework to build customizable, production-ready LLM applications in Python.
- [LangChain](https://github.com/hwchase17/langchain): 言語モデルプロンプトのシーケンスを連鎖させるための一般的なPython/JavaScriptライブラリです。
- [LiteLLM](https://github.com/BerriAI/litellm): A minimal Python library for calling LLM APIs with a consistent format. 
- [LlamaIndex](https://github.com/jerryjliu/llama_index): LLMアプリをプライベートデータ（個人、組織）で補強するためのPythonライブラリです。
- [LMQL](https://lmql.ai): A programming language for LLM interaction with support for typed prompting, control flow, constraints, and tools.
- [OpenAI Evals](https://github.com/openai/evals): 言語モデルやプロンプトのタスク性能を評価するためのオープンソースライブラリです。
- [Outlines](https://github.com/normal-computing/outlines)： プロンプトと制約の生成を簡略化するためのドメイン固有言語を提供するPythonライブラリ。
- [Promptify](https://github.com/promptslab/Promptify): 言語モデルを使用してNLPタスクを実行するための小さなPythonライブラリです。
- [PromptPerfect](https://promptperfect.jina.ai/prompts): プロンプトをテスト・改善するための有償製品です。
- [Prompttools](https://github.com/hegelai/prompttools): モデルやベクターデータベース、プロンプトのテストや評価に使用されるオープンソースの Python ツール。
- [Scale Spellbook](https://scale.com/spellbook): 言語モデルアプリを構築、比較、出荷するための有償製品です。
- [Semantic Kernel](https://github.com/microsoft/semantic-kernel): Microsoftが提供するPython/C#/Java ライブラリで、プロンプトテンプレート、関数チェイニング、ベクトル化メモリ、インテリジェントプランニングをサポートしています。
- [Weights & Biases](https://wandb.ai/site/solutions/llmops): トラッキングモデルのトレーニングやプロンプトエンジニアリング実験用の有償製品です。
- [YiVal](https://github.com/YiVal/YiVal): An open-source GenAI-Ops tool for tuning and evaluating prompts, retrieval configurations, and model parameters using customizable datasets, evaluation methods, and evolution strategies.

## プロンプティングガイド

- [Brex's Prompt Engineering Guide](https://github.com/brexhq/prompt-engineering): ブレックスの言語モデルやプロンプトエンジニアリングの紹介です。
- [learnprompting.org](https://learnprompting.org/): プロンプトエンジニアリングの入門コースです。
- [Lil'Log Prompt Engineering](https://lilianweng.github.io/posts/2023-03-15-prompt-engineering/): OpenAI研究員によるプロンプトエンジニアリング文献のレビューです。（2023年3月現在）。
- [OpenAI Cookbook: Techniques to improve reliability](techniques_to_improve_reliability.md): 言語モデルをプロンプト化する技術について、少し古い（2022年9月）レビューです。
- [promptingguide.ai](https://www.promptingguide.ai/): 多くのテクニックを披露するプロンプトエンジニアリングガイドです。

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
