# Answers、Classification、Search の非推奨化

2021年、OpenAI は Answers、Classification、Search に特化したエンドポイントをベータ版でリリースしましたが、
これらのエンドポイントは便利な反面、以下2つの欠点がありました。

1. これらの特殊なエンドポイントは、より良い結果を出す他の技術に負けた。
2. カスタマイズが難しく、個々のユースケースに最適化しにくい。

その結果、**The Answers, Classifications, and Search のエンドポイントは廃止される** こととなりました。

## 廃止のタイムライン

これらのエンドポイントを使用していない方にとっては、アクセスができなくなること以外は何も変わりません。

**これらのエンドポイントの既存のユーザーについては2022年12月3日までアクセスが継続されます** ので、その前により良い結果をもたらす新しい技術に切り替えることを強くお勧めします。

## 移行方法

非推奨のAPIエンドポイントからより良い手法に移行するためのガイドとコード例を書きました。

### Answers

[ガイド: Answers エンドポイントから移行する方法](https://help.openai.com/en/articles/6233728-answers-transition-guide)

* オプション1: 埋め込み型検索への移行 **（推奨）**
  * サンプルコード [Semantic_text_search_using_embeddings.ipynb](../examples/Semantic_text_search_using_embeddings.ipynb)
* オプション2：Answersのエンドポイント機能を再実装する
  * サンプルコード [answer_functionality_example.py](answer_functionality_example.py)

### Classifications

[ガイド: Classifications エンドポイントからの移行方法](https://help.openai.com/en/articles/6272941-classifications-transition-guide)

* オプション1：fine-tuning への移行 **（推奨）**
  * サンプルコード [Fine-tuned_classification.ipynb](../examples/Fine-tuned_classification.ipynb)
* オプション2：embeddings への移行
  * サンプルコード [Semantic_text_search_using_embeddings.ipynb](../examples/Semantic_text_search_using_embeddings.ipynb)
* オプション3：Classifications エンドポイント機能を再実装する
  * サンプルコード [classification_functionality_example.py](classification_functionality_example.py)

### Search

[ガイド: Search エンドポイントからの移行方法](https://help.openai.com/en/articles/6272952-search-transition-guide)

* オプション1: embeddings-based search への移行 **（推奨）**
  * サンプルコード [Semantic_text_search_using_embeddings.ipynb](../examples/Semantic_text_search_using_embeddings.ipynb)
* オプション2：Search エンドポイント機能を再実装する
  * サンプルコード [search_functionality_example.py](search_functionality_example.py)。

<!--
# Deprecation of Answers, Classification, and Search

In 2021, OpenAI released specialized endpoints in beta for Answers, Classification, and Search.

While these specialized endpoints were convenient, they had two drawbacks:

1. These specialized endpoints were eclipsed by techniques that achieved better results.
2. These specialized endpoints were more difficult to customize and optimize for individual use cases.

As a result, **the Answers, Classifications, and Search endpoints are being deprecated.**

## Timeline of deprecation

For those who have not used these endpoints, nothing will change except that access will no longer be available.

**For existing users of these endpoints, access will continue until December 3, 2022.** Before that date, we strongly encourage developers to switch over to newer techniques which produce better results.

## How to transition

We've written guides and code examples for transitioning from the deprecated API endpoints to better methods.

### Answers

[Guide: How to transition off the Answers endpoint](https://help.openai.com/en/articles/6233728-answers-transition-guide)

* Option 1: transition to embeddings-based search **(recommended)**
  * Example code: [Semantic_text_search_using_embeddings.ipynb](../examples/Semantic_text_search_using_embeddings.ipynb)

* Option 2: reimplement Answers endpoint functionality
  * Example code: [answers_functionality_example.py](answers_functionality_example.py)

### Classification

[Guide: How to transition off the Classifications endpoint](https://help.openai.com/en/articles/6272941-classifications-transition-guide)

* Option 1: transition to fine-tuning **(recommended)**
  * Example code: [Fine-tuned_classification.ipynb](../examples/Fine-tuned_classification.ipynb)
* Option 2: transition to embeddings
  * Example code: [Semantic_text_search_using_embeddings.ipynb](../examples/Semantic_text_search_using_embeddings.ipynb)
* Option 3: reimplement Classifications endpoint functionality
  * Example code: [classification_functionality_example.py](classification_functionality_example.py)

### Search

[Guide: How to transition off the Search endpoint](https://help.openai.com/en/articles/6272952-search-transition-guide)

* Option 1: transition to embeddings-based search **(recommended)**
  * Example code: [Semantic_text_search_using_embeddings.ipynb](../examples/Semantic_text_search_using_embeddings.ipynb)
* Option 2: reimplement Search endpoint functionality
  * Example code: [search_functionality_example.py](search_functionality_example.py)
-->
