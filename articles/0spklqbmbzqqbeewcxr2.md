---
title: "Golang でも Domain layer 作って書きましょーね"
emoji: ""
type: "25-dev-general"
topics: ['25-dev-general']
published: False
---

# Golang でも Domain layer 作って書きましょーね

Golang でも Domain layer 作って書きましょーね

最近、Golangでのプログラミングについて考えていました。特に、Domain層の作成方法についてです。Domain層は、アプリケーションの中核となる部分であり、ビジネスルールやエンティティを管理する役割を果たします。

最初は、「<https://medium.com/i35-267/infrastructure-api-ddd-x-oop-x-go-d43fc3cf7811>」という記事を参考にしようと思いました。この記事では、GolangでのインフラストラクチャAPIの設計について詳しく説明されています。しかし、実際に試してみると、GolangとDomain層の相性があまり良くないことに気付きました。

別の記事「<https://zenn.dev/msksgm/articles/20220617-go-is-incompatible-to-ddd>」では、GolangとDDDの相性の悪さについて取り上げられています。この記事を読んで、最初の記事が少し古い情報だったことに気付きました。結局、GolangでのDomain層の作成方法については明確な答えが見つからず、私はGolangがあまり好きではないという結論に至りました。

私は、大きなファイルに工夫を凝らすよりも、コードを構造化することを重視する方が良いと考えています。そのために、GitHub上で公開されている「<https://github.com/slack-go/slack>」というプロジェクトを参考にしました。このプロジェクトでは、コードの中にドメイン構造を明示的に定義しています。

GolangでDomain層を作成する際には、ファイルの構造化よりもコードの中での工夫に重点を置くことが重要です。このようなアプローチを取ることで、よりクリーンでメンテナブルなコードを実現することができます。

以上が、私のGolangでのDomain層作成に関する考えです。皆さんも是非参考にしてみてください。

(参考リンク：<https://medium.com/i35-267/infrastructure-api-ddd-x-oop-x-go-d43fc3cf7811>, <https://zenn.dev/msksgm/articles/20220617-go-is-incompatible-to-ddd>, <https://github.com/slack-go/slack>)
