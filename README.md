# はじめに
[OpenAI Cookbook](https://github.com/openai/openai-cookbook) の日本語訳です。  
機械翻訳したものをベースに、少しでも補正して読み易くなれば良いなと考えています。 
元となるリポジトリへの追従、一貫性のある読み易い翻訳のガイドなど、他のリポジトリを参考にしながら進めたいと思います。

私は以下の方法で[本家](https://github.com/openai/openai-cookbook)に追随しようと考えています（もっと良い方法があると思うので教えて下さい）

1. ローカルリポジトリに以下のブランチを用意
```
① 本家リポ追随ブランチ（英語）：pitcher
② 和訳元ブランチ（英語）      ：batter
③ 和訳済みブランチ（日本語）  ：master
```
2. ①を本家とマージ
```
git remote add upstream [本家リポURL]
git fetch upstream # 本家をフェッチ
git checkout pitcher #本家とマージしたいブランチをチェックアウト
git merge upstream/main
```
3. ①と②のdiffを確認
```
git diff --name-only pitcher batter  #変更されたファイルを確認
git diff batter:[ファイル名] pitcher:[ファイル名] 
```
4. diffで確認した差分（英文）を和訳して、③に反映


![badge](https://img.shields.io/endpoint.svg?url=https%3A%2F%2Fgezf7g7pd5.execute-api.ap-northeast-1.amazonaws.com%2Fdefault%2Fsource_up_to_date%3Fowner%3Dopenai%26repos%3Dopenai-cookbook%26ref%3Dmain%26path%3DREADME.md%26commit_hash%3Daeec6d9c1bae9c8c779ad62ac5b78e8ec479bf78)

# OpenAI Cookbook とは

[OpenAI Cookbook](https://github.com/openai/openai-cookbook) では、OpenAI API を使用して一般的なタスクを実行するためのサンプルコードを共有しています。  
これらの例を実行するには、OpenAI アカウントと関連する API キーが必要です。（[無料アカウントを作成](https://beta.openai.com/signup)）  
ほとんどのコード例は Python で記述されていますが、概念はどの言語でも適用できます。  

## ガイド ＆ 例

* API の使用状況
  * [レート制限状況の把握方法](examples/How_to_handle_rate_limits.ipynb)
    * [レート制限のヒットを回避する並列処理スクリプトの例](examples/api_request_parallel_processor.py)
  * [tiktokenでトークンを数える方法](examples/How_to_count_tokens_with_tiktoken.ipynb)
  * [入力候補をストリーミングする方法](examples/How_to_stream_completions.ipynb)
* GPT-3
  * [ガイド: 大規模な言語モデルを操作する方法](how_to_work_with_large_language_models.md)
  * [ガイド:信頼性を向上させるテクニック](techniques_to_improve_reliability.md)
  * [複数ステップのプロンプトを使用して単体テストを記述する方法](examples/Unit_test_writing_using_a_multi-step_prompt.ipynb)
  * [テキストを書く例](text_writing_examples.md)
  * [テキストを説明する例](text_explanation_examples.md)
  * [テキストを編集する例](text_editing_examples.md)
  * [コードを書く例](code_writing_examples.md)
  * [コードを説明する例](code_explanation_examples.md)
  * [コードを編集の例](code_editing_examples.md)
* 埋め込み
  * [テキスト比較の例](text_comparison_examples.md)
  * [埋め込みを取得する方法](examples/Get_embeddings.ipynb)
  * [埋め込みを使用した質問応答](examples/Question_answering_using_embeddings.ipynb)
  * [埋め込みを使用したセマンティック検索](examples/Semantic_text_search_using_embeddings.ipynb)
  * [埋め込みを使用した推奨事項](examples/Recommendation_using_embeddings.ipynb)
  * [クラスタリング埋め込み](examples/Clustering.ipynb)
  * 埋め込みを[2D](examples/Visualizing_embeddings_in_2D.ipynb) または [3D](examples/Visualizing_embeddings_in_3D.ipynb)で視覚化する
  * [テキスト (長) の埋め込み](examples/Embedding_long_inputs.ipynb)
* GPT-3の微調整
  * [ガイド:テキストを分類するためにGPT-3を微調整するためのベストプラクティス](https://docs.google.com/document/d/1rqj7dkuvl7Byd5KQPUJRxc19BJt8wo0yHNwK84KfU3Q/edit)
  * [微調整された分類](examples/Fine-tuned_classification.ipynb)
* DALL-E
  * [DALL-Eで画像を生成および編集する方法](examples/dalle/Image_generations_edits_and_variations_with_DALL-E.ipynb)
* Azure OpenAI (Microsoft Azureの代替API)
  * [Azure OpenAI から入力候補を取得する方法](examples/azure/completions.ipynb)
  * [Azure OpenAI から埋め込みを取得する方法](examples/azure/embeddings.ipynb)
  * [Azure OpenAI で GPT-3 を微調整する方法](examples/azure/finetuning.ipynb)

## 関連リソース

ここにあるコード例以外にも、次のリソースから [OpenAI API] について学ぶことができます。

* [OpenAI Playground] で API を試す
* [OpenAI Documentation] で API について読む
* [OpenAI Community Forum] API について議論する
* [OpenAI Help Center] でヘルプを探す
* [OpenAI Examples] でプロンプトの例を参照してください
* [ChatGPT]のfreeな回答プレビューで遊ぶ 
* [OpenAI Blog]で最新情報を入手する

## 貢献する

あなたが見たい 例 や ガイド があれば、気兼ねなく[issues page]に提案してください。


[ChatGPT]: https://chat.openai.com/
[OpenAI API]: https://openai.com/api/
[API Signup]: https://beta.openai.com/signup
[OpenAI Playground]: https://beta.openai.com/playground
[OpenAI Documentation]: https://beta.openai.com/docs/introduction
[OpenAI Community Forum]: https://community.openai.com/top?period=monthly
[OpenAI Help Center]: https://help.openai.com/en/
[OpenAI Examples]: https://beta.openai.com/examples
[OpenAI Blog]: https://openai.com/blog/
[issues page]: https://github.com/openai/openai-cookbook/issues
