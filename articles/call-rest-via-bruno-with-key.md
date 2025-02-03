---
title: "Bruno に乗り換えることになったので使ってみる"
emoji: "🐕"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["REST", "Bruno"]
published: true
---

# はじめに
環境の都合により、某 REST API 呼び出しツールから Bruno に乗り換えたので、その使い始めの記録です。
もう何番煎じかわかりません。

# この記事の要約
Bruno を使ってみた！
https://www.usebruno.com/

# 環境
以下の環境、バージョンで取り組んでいます。
- Windows 11 Enterprise (24H2)
- Bruno 1.38.1

# とりあえず使ってみる
まずは一通り動くところまでやってみましょう。手順書ではないので、あとから見直したときにあったほうがいいなと思ったポイントだけ書いていきます。

## インストール 
以下の Docs に従って、Winget でインストールしました。
```powershell
winget install Bruno.Bruno
```
https://docs.usebruno.com/get-started/bruno-basics/download

インストールが完了すると、Bruno が自動起動したので、そのまま続けていきます。

## 最初の REST API コール
自分で REST API を作ったりするのはめんどくさいので、MSN.com でも呼んでみることにします。
1. Collection 作成
1. Request 作成
1. 呼び出し

![MSNの呼び出し](/images/call-rest-via-bruno-with-key/image1.png)
*MSNを呼び出し*

# Azure 上の API を呼んでみる
所与の API キーを使用して、Azure OpenAI Service を呼び出してみます。以下の流れになりました。
1. Environment 作成
1. Collection 作成
1. Folder 作成
1. Request 作成
1. 呼び出し

![MSNの呼び出し](/images/call-rest-via-bruno-with-key/image2.png)
*AOAI を呼び出し*

## Environment の意味
Collection ごとに設定できる環境変数です。以下のようなものを私は定義します。
- エンドポイント
- URL に埋め込む可変部分
- API バージョン

今回は API キーも隠蔽したいので Environment に定義しました。

Environment を作成することから逆算すると、Collection は環境変数が共有できる範囲のリクエストだけを含めるほうが使いやすそうかなと思います。
例えば、複数のエンドポイントを書くこともできますが、おそらくかなり散らかります。(個人の感想です)

## Request を作るにあたって考えること
まずは、対象の API の定義や利用方法を確認するのが最初です。
例えば、以下は Azure OpenAI Service のチャット入力候補 API の使用方法です。
https://learn.microsoft.com/ja-jp/azure/ai-Service/openai/reference#chat-completions

ドキュメントからは、
- URI パラメーターで指定すべきものは何か？
- リクエスト ヘッダーに指定すべきものは何か？
- リクエスト本文に指定すべきものは何か？

を読み取ります。API キーについては Header として定義することもできますし、Auth タブ内で設定することもできますが、結局は Header に含めるので好みかなと思います。

# おわりに
某ツールと使い勝手があまり変わらないので、迷子にならずに済みました。