# テキスト比較の例

[OpenAI API embeddings endpoint](https://beta.openai.com/docs/guides/embeddings) は、テキストの断片間の関連性や類似性を測定するために使用することができます。

GPT-3のテキストに対する理解を活用し、これらの埋め込みは教師なし学習と転移学習のベンチマークで[最先端の結果を達成](https://arxiv.org/abs/2201.10005)しています。

埋め込みは、意味検索、レコメンデーション、クラスタ分析、重複検出などに利用することができます。

詳しくは、OpenAI のブログ記事のお知らせをご覧ください。

* [テキストとコードの埋め込みの紹介(2022年1月)](https://openai.com/blog/introducing-text-and-code-embeddings/)
* [新しく改良された埋め込みモデル(2022年12月)](https://openai.com/blog/new-and-improved-embedding-model/)

## セマンティック検索

エンベッディングはそれ自体でも、より大きなシステムの中の機能としても、検索に使うことができます。

最も簡単な検索への埋め込みの使い方は以下の通りです。

* 検索を行う前（precompute）:
  * テキストコーパスをトークン制限（`text-embedding-ada-002` は 8,191 トークン）より小さいチャンクに分割する。
  * 各チャンクのテキストを埋め込む
  * 埋め込み情報を自分のデータベースか、[Pinecone](https://www.pinecone.io) 、 [Weaviate](https://weaviate.io) や[Qdrant](https://qdrant.tech)などのベクトル検索プロバイダに保存する。
* 検索時（livecompute）:
  * 検索クエリを埋め込む
  * データベースから最も近い埋め込みを探す
  * 検索結果の上位を返す

検索に埋め込みを使う例は [Semantic_text_search_using_embeddings.ipynb](examples/Semantic_text_search_using_embeddings.ipynb) で示されています。

より高度な検索システムでは、埋め込みのコサイン類似度は、検索結果のランキングのための多くの特徴のうちの1つとして使われます。

## 質問応答

GPT-3 から信頼性の高い回答を得るための最良の方法は、GPT-3 が正しい回答を見つけることができるような原文を与えることである。上記のセマンティック検索を用いると、関連する情報のために文書のコーパスを安価に検索し、その情報をプロンプトを介してGPT-3に与え、質問に回答させることができる。
[Question_answering_using_embeddings.ipynb](examples/Question_answering_using_embeddings.ipynb) でデモを行っています。

## レコメンデーション

レコメンデーションは、自由形式のテキストクエリの代わりに、セット内のアイテムを入力することを除けば、検索と非常に似ています。

レコメンデーションにエンベッディングを使う例は [Recommendation_using_embeddings.ipynb](examples/Recommendation_using_embeddings.ipynb) で示されています。

検索と同様に、これらのcosine類似度スコアはそれ自体でアイテムのランク付けに使われることも、より大きなランク付けアルゴリズムの特徴として使われることもあります。

## エンベッディングのカスタマイズ

OpenAIの埋め込みモデルの重みは微調整できませんが、それでも、学習データを使って埋め込みをアプリケーションに合わせてカスタマイズすることは可能です。

[Customizing_embeddings.ipynb](examples/Customizing_embeddings.ipynb) では、学習データを使ってエンベッディングをカスタマイズする方法を例として挙げています。このメソッドのアイデアは、新しいカスタマイズされた埋め込みを得るために、埋め込みベクトルを掛け合わせるカスタム行列を学習することです。良い学習データがあれば、このカスタム行列は、学習ラベルに関連する特徴を強調するのに役立ちます。この行列の乗算は、(a)埋め込みベクトルの修正、(b)埋め込みベクトル間の距離を測るための距離関数の修正と考えることができます。

<!--
# Text comparison examples

The [OpenAI API embeddings endpoint](https://beta.openai.com/docs/guides/embeddings) can be used to measure relatedness or similarity between pieces of text.

By leveraging GPT-3's understanding of text, these embeddings [achieved state-of-the-art results](https://arxiv.org/abs/2201.10005) on benchmarks in unsupervised learning and transfer learning settings.

Embeddings can be used for semantic search, recommendations, cluster analysis, near-duplicate detection, and more.

For more information, read OpenAI's blog post announcements:

* [Introducing Text and Code Embeddings (Jan 2022)](https://openai.com/blog/introducing-text-and-code-embeddings/)
* [New and Improved Embedding Model (Dec 2022)](https://openai.com/blog/new-and-improved-embedding-model/)

## Semantic search

Embeddings can be used for search either by themselves or as a feature in a larger system.

The simplest way to use embeddings for search is as follows:

* Before the search (precompute):
  * Split your text corpus into chunks smaller than the token limit (8,191 tokens for `text-embedding-ada-002`)
  * Embed each chunk of text
  * Store those embeddings in your own database or in a vector search provider like [Pinecone](https://www.pinecone.io) or [Weaviate](https://weaviate.io)
* At the time of the search (live compute):
  * Embed the search query
  * Find the closest embeddings in your database
  * Return the top results

An example of how to use embeddings for search is shown in [Semantic_text_search_using_embeddings.ipynb](examples/Semantic_text_search_using_embeddings.ipynb).

In more advanced search systems, the the cosine similarity of embeddings can be used as one feature among many in ranking search results.

## Question answering

The best way to get reliably honest answers from GPT-3 is to give it source documents in which it can locate correct answers. Using the semantic search procedure above, you can cheaply search a corpus of documents for relevant information and then give that information to GPT-3, via the prompt, to answer a question. We demonstrate in [Question_answering_using_embeddings.ipynb](examples/Question_answering_using_embeddings.ipynb).

## Recommendations

Recommendations are quite similar to search, except that instead of a free-form text query, the inputs are items in a set.

An example of how to use embeddings for recommendations is shown in [Recommendation_using_embeddings.ipynb](examples/Recommendation_using_embeddings.ipynb).

Similar to search, these cosine similarity scores can either be used on their own to rank items or as features in larger ranking algorithms.

## Customizing Embeddings

Although OpenAI's embedding model weights cannot be fine-tuned, you can nevertheless use training data to customize embeddings to your application.

In [Customizing_embeddings.ipynb](examples/Customizing_embeddings.ipynb), we provide an example method for customizing your embeddings using training data. The idea of the method is to train a custom matrix to multiply embedding vectors by in order to get new customized embeddings. With good training data, this custom matrix will help emphasize the features relevant to your training labels. You can equivalently consider the matrix multiplication as (a) a modification of the embeddings or (b) a modification of the distance function used to measure the distances between embeddings.
-->
