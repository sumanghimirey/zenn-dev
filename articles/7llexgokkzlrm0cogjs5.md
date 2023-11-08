---
title: "# RESTful API の設計ツールとしてのSwagger Viewer"
emoji: ""
type: "25-dev-general"
topics: ['25-dev-general']
published: False
---

# # RESTful API の設計ツールとしてのSwagger Viewer

RESTful API の設計書を楽に作成する方法

最近、RESTful API の設計書を書いても捨てるだけで時間の浪費になってしまうと感じていませんか？そんな方におすすめなのが、「Swagger Viewer」です。

Swagger Viewer を使用すれば、VSCode 上で Swagger editor のようにメンテナンスすることができます。具体的には以下の手順で利用することができます。

1. コマンドパレットから「Preview Swagger」を選択します。
2. shift + option + p のショートカットキーを押します。※ ユーザーさん、申し訳ありませんが注意してください。

これで、VSCode 上で Swagger editor のように RESTful API の設計書を作成・メンテナンスすることができるようになります。

さらに、以下の機能も利用することができます。

- 静的解析ツール: パスやコンポーネントが表示されるツールです。
- コード補完機能: コードの入力時に自動的に補完候補が表示されます。

これらの機能を導入すれば、openapi.yml ファイルからコントローラーまでのコードを自動生成することができます。また、openapi.yml のメンテナンスが面倒だと感じる場合は、コントローラーにコメントを書いて、code first の開発モデルにすることで、API ドキュメントを不要にすることも可能です。

このように、Swagger Viewer を活用することで、RESTful API の設計書作成の効率化とメンテナンスの簡素化を実現できます。是非お試しください。
