---
title: "ヘッドレスCMSとは？"
emoji: ""
type: "25-dev-general"
topics: ['25-dev-general']
published: False
---

# ヘッドレスCMSとは？

ヘッドレスCMSとは？

最近、Headless CMSという言葉を耳にすることが増えてきました。これは、Strapiなどのツールが提供しているもので、単なるテスト用のモックAPIサーバーであり、本格的な機能はありません。そのため、GraphQLと組み合わせて使用することが推奨されています。この組み合わせがあれば、より幸せな開発体験を得ることができるそうです。

以前は、自作のテスト用サーバーを作成する必要がありましたが、最近ではPostmanを使用して簡単にモックサーバーを立ち上げることができるため、非常に便利な時代になりました。

Strapiについて詳しく知りたい方は、[こちらの記事](https://wk-partners.co.jp/homepage/blog/hpseisaku/htmlcss/strapi/)をご覧ください。

# Headless CMSの選択肢

さて、Headless CMSにはいくつかの選択肢がありますが、特に有名なのは[***](https://microcms.io/)です。しかし、これはSaaS版であり、料金がかなり高いと言われています。私自身も運用をやめた経験があります。

一方で、[WebConsole](https://webconsole.co.jp/)が付属しているため、非常に使い勝手が良いと評判です。ただし、Headless CMSは元々、画面を持たないものであり、ユーザーが直接編集するのが難しいという声もあります。そのような場合には、Firebaseを使用して全体を構築する方が早いかもしれません。簡単なサービスであれば、Firebaseで作り、将来的にアクセスが増えてきた場合には、少しずつCloudの機能を導入するというロードマップが理想的だと思います。

このような選択肢がある中で、どのCMSを選ぶかはプロジェクトの特性や目的に応じて考えるべきです。それぞれの特徴を比較し、最適な選択を行いましょう。

この記事は「Web開発」シリーズの一環としてお届けしました。

本記事に関するご意見やご質問がありましたら、お気軽にコメントしてください。
