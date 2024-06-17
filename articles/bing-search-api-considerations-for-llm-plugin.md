---
title: "Bing Search API を LLM プラグインに利用する際の考慮事項あれこれ"
emoji: "🧐"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["BingWebSearchAPI", "LLMPlugin"]
published: false
---

# はじめに
大規模言語モデルをベースとした生成 AI は、組織専用の生成 AI チャットとして多くの組織に導入されつつあります。本記事では、専用生成 AI チャットが Web 上で公開された情報を加味した回答を生成できるようにするための Web 検索エンジン、Bing Search API の導入に際しての考慮事項を整理します。

本記事に関しては、法的に正確な解釈が求められるトピックも含むため、以下の免責事項を踏まえて参照してください。

## 免責事項
- 本記事は、Bing Search API の利用に際しての一般的な情報提供のみを目的としており、特定の状況に対する助言を提供するものではありません。記事の内容は、投稿日時点での情報に基づいています。
- この記事の情報を利用して行動を起こす前に、専門家に相談することを強く推奨します。この記事の情報に基づいて行動を取った結果について、ブログの所有者、管理者、作成者、貢献者は一切の責任を負いません。
- この記事に掲載されている情報は、可能な限り正確であるように努力していますが、その正確性や完全性を保証するものではありません。また、筆者は情報が時代遅れになったり、その他の理由で不正確になった場合でも、情報を更新する義務を負いません。

# 要約
- Web 検索 API は与えられたキーワードに対する検索結果を返すものと認識する
- キーワードに対する情報漏洩は、プラグインの処理内で考慮するものと認識する

# Bing Search API について
Microsoft の検索エンジン Bing が API として提供されているものです。過去には、Azure の AI 系 API 群の総称であった、Cognitive Seavices (現在の Azure AI Services) に含まれる API の一つとして位置づけられていた時期もありました。

https://learn.microsoft.com/en-us/bing/search-apis/bing-web-search/overview

# MSから提示されている要求事項、ガイダンス
## Use and Display requirements of Bing Search APIs, with your LLM 
Bing Search API のドキュメントの一部として提示されています。認められない利用方法や、考慮した方がいい要求事項が纏まっていますので、生成 AI と組み合わせて利用する場合には一番最初に読んでおく必要があります。

https://learn.microsoft.com/en-us/bing/search-apis/bing-web-search/use-display-requirements-llm

## Term of Use
使用条件、利用条件と訳される文書です。利用において遵守する条件が記載されています。

https://www.microsoft.com/en-us/bing/apis/legal

# おわりに
