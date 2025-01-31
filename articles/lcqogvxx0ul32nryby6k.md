---
title: "ファイルシステムの暗号化について"
emoji: ""
type: "25-砂場"
topics: ['25-砂場']
published: False
---

# ファイルシステムの暗号化について

ファイルシステムの暗号化について

ファイルシステムの暗号化は、個人情報や機密データの保護に重要な役割を果たします。その中でも、<a href="https://github.com/google/fscrypt">fscrypt</a>は効果的な解決策として注目されています。fscryptは、カーネルで実装されているため軽量であり、特定のPCでのみ復号できるように設定することができます。また、PAMとの連携も容易であり、ユーザーのパスワード変更時に自動的に同期するという特徴もあります。

fscryptのメリットは以下の通りです：
- カーネル側で実装されているため軽量
- 特定のPCでのみ復号できるように設定可能
- PAMとの連携が容易
- ユーザーのパスワードと連携できる
- Google製で信頼性が高い

一方、fscryptのデメリットは以下のようになります：
- ブロックデバイスレベルでの暗号化はできないため、情報漏洩の可能性がある
- EXT4 / F2FSのみ対応で、他のファイルシステムには非対応
- 細かな設定ができない場合もある

fscryptは素晴らしい暗号化ツールですが、誤った操作や設定ミスによってデータを消失する可能性もあるため、注意が必要です。
