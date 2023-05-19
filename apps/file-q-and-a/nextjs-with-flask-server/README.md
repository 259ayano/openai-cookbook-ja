# Next.jsとFlaskによるファイルQ&A

ファイルQ&Aは、ファイルの中から答えを見つけることができるウェブアプリです。ファイルをアップロードして、その内容に関連する質問をすると、アプリは埋め込みとGPTを使って、最も関連性の高いファイルから回答を生成します。

## 要件

アプリを実行するために必要なのは

- OpenAI APIキー。新しいAPIキーは、[こちら](https://beta.openai.com/account/api-keys)で作成できます。
- Pinecone APIキーとインデックス名。新しいアカウントとインデックスを作成することができます [こちら](https://www.pinecone.io/).
- Python3.7以上とFlaskサーバー用のpipenv。
- Next.jsクライアントには、Node.jsとnpmが必要です。

## セットアップと開発

### サーバー

config.yaml ファイルに Pinecone API キー、インデックス名、環境を記入します。

Flaskサーバを実行します。

```
cd server
bash script/start "<your OPENAI_API_KEY>"
```

### クライアント

クライアントディレクトリに移動し、Nodeの依存関係をインストールします。

```
cd client
npm install
```

Next.jsクライアントを実行します。

```
cd client
npm run dev
```

ブラウザで[http://localhost:3000](http://localhost:3000)を開くと、アプリが表示されます。

## 制限事項

こちらのアプリは、ファイルにない答えを生成したり、アップロードされていないファイルの存在を幻視することが時々あります。
