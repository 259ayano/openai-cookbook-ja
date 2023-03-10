# ファイルQ&A

ファイルQ&Aは、OpenAI APIを使ってファイルの中から答えを探すことができる[Next.js](https://nextjs.org/)アプリです。ファイルをアップロードして、その内容に関連した質問をすると、アプリは埋め込みとGPTを使って、最も関連性の高いファイルから答えを生成します。

## 要件

アプリを実行するには、OpenAI APIキーが必要です。新しいAPIキーは[こちら](https://beta.openai.com/account/api-keys)で作成することができます。

## セットアップ

Node.jsとnpmをまだ持っていない場合は、[https://nodejs.org/en/download/](https://nodejs.org/en/download/)からインストールします。

ターミナルで、このサンプルアプリの `nextjs` ディレクトリに移動し、依存関係をインストールします。

```
npm install
```

.env.local.example ファイルを .env.local ファイルにコピーし、OpenAI API キー欄を記入します。

## 開発

開発用サーバーを起動します。

```
npm run dev
```

ブラウザで[http://localhost:3000](http://localhost:3000)を開くとアプリが表示されます。

## デプロイメント

Next.jsのクリエイターによるプラットフォームである[Vercel](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme)上にアプリをデプロイすることができます。詳しくは、[Next.js デプロイメントドキュメント](https://nextjs.org/docs/deployment) をご覧ください。

## 制限事項

アップロードされたファイルや生成された埋め込みは、ブラウザのリフレッシュ時に永続化されません。より多くの埋め込みデータを保存したい場合は、ベクターデータベース（Pinecone, Weaviate, Milvus, Qdrant, Redis, FAISSなど）の利用をお勧めします。このデモの `nextjs-with-flask-server` バージョンでは、Pinecone ベクターデータベースを使用しています。

こちらのアプリは、ファイルにない答えを生成したり、アップロードされていないファイルの存在を幻視することが時々あります。
