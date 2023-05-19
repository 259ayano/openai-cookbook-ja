# enterprise-knowledge-retrieval

このアプリは、構造化されていないテキストドキュメントを利用して、使える知識ベースアプリケーションを作成することを目的とした、エンタープライズ知識検索を深く掘り下げたものです。

このレポにはノートブックと基本的なStreamlitアプリが含まれています：
- `enterprise_knowledge_retrieval.ipynb`：トークン化、チャンキング、ベクターデータベースへの埋め込み、チャットエージェントの構築、性能評価のステップを含むノートブックです。
- `chatbot.py`： Streamlitのアプリで、検索バーを使って知識ベースを照会し、簡単なQ&Aを提供します。

アプリを実行するには、以下の ``アプリ`` セクションにある指示に従ってください。

## ノートブック

ノートブックは、シンプルなバックエンドの知識検索サービスをセットアップして評価するためのエンドツーエンドのワークフローを説明するもので、始めるのに最も適した場所です：
- **セットアップ：** 変数を開始し、ベクターデータベースに接続します。
- **ストレージ：** データベースを設定し、データを準備し、検索のために埋め込みとメタデータを保存します。
- **検索：** 基本的な検索機能で関連するドキュメントを抽出し、LLMを使用して結果を簡潔な返答に要約して戻します。
- **回答：** ユーザーの問い合わせを処理し、フォローアップの質問のためのメモリを維持する、より洗練されたエージェントを追加します。
- **評価：** 私たちのサービスを使用して質問と回答のペアを取り、評価し、改善策をスコープアウトするためにそれらをプロットします。

ノートブックを検索段階まで実行したら、アプリをセットアップして実行するために必要なものが揃っているはずです。

## アプリ

標準的なセマンティック検索や[HyDE](https://arxiv.org/abs/2212.10496)検索を使って検索サービスをテストするために、Streamlitの基本アプリを用意しました。

これを使うには
- ノートブックの「セットアップとストレージ」の手順に従って、ベクターデータベースに検索可能なコンテンツを投入したことを確認します。
- ``virtualenv venv`` を実行して pip で仮想環境をセットアップします（``virtualenv`` がインストールされていることを確認します）。
- ``source venv/bin/activate`` を実行して、環境をアクティブにします。
- ``pip install -r requirements.txt`` を実行して、要件をインストールします。
- ``streamlit run chatbot.py`` を実行して、ブラウザ上でStreamlitアプリを起動させます。

## 制限事項

- このアプリではベクターデータベースとしてRedisを使用していますが、他にも様々なオプションがあり、必要に応じて `../examples/vector_databases` をハイライトします。
- このノートブックでは、最適化できそうな部分をたくさん紹介していますが、これらの部分については、次のクックブックで深く掘り下げます。

<!--
# Enterprise Knowledge Retrieval

This app is a deep dive on Enterprise Knowledge Retrieval, which aims to take some unstructured text documents and create a usable knowledge base application with it.

This repo contains a notebook and a basic Streamlit app:
- `enterprise_knowledge_retrieval.ipynb`: A notebook containing a step by step process of tokenising, chunking and embedding your data in a vector database, building a chat agent on top and running a basic evaluation of its performance.
- `chatbot.py`: A Streamlit app providing simple Q&A via a search bar to query your knowledge base.

To run the app, please follow the instructions below in the ```App``` section

## Notebook

The notebook is the best place to start, and takes you through an end-to-end workflow for setting up and evaluating a simple back-end knowledge retrieval service:
- **Setup:** Initiate variables and connect to a vector database.
- **Storage:** Configure the database, prepare our data and store embeddings and metadata for retrieval.
- **Search:** Extract relevant documents back out with a basic search function and use an LLM to summarise results into a concise reply.
- **Answer:** Add a more sophisticated agent which will process the user's query and maintain a memory for follow-up questions.
- **Evaluate:** Take question/answer pairs using our service, evaluate and plot them to scope out remedial action

Once you've run the notebook through to the Search stage, you should have what you need to set up and run the app.

## App

We've rolled in a basic Streamlit app that you can interact with to test your retrieval service using either standard semantic search or [HyDE](https://arxiv.org/abs/2212.10496) retrievals.

To use it:
- Ensure you followed the Setup and Storage steps from the notebook to populate a vector database with searchable content.
- Set up a virtual environment with pip by running ```virtualenv venv``` (ensure ```virtualenv``` is installed).
- Activate the environment by running ```source venv/bin/activate```.
- Install requirements by running ```pip install -r requirements.txt```.
- Run ```streamlit run chatbot.py``` to fire up the Streamlit app in your browser.

## Limitations

- This app uses Redis as a vector database, but there are many other options highlighted `../examples/vector_databases` depending on your need.
- We introduce many areas you may optimize in the notebook, but we'll deep dive on these in subsequent cookbooks.
-->
