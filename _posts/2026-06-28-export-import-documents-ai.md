---
layout: post
title: "製造業の輸出入書類（英文インボイス・輸出証明）をAIで作る方法"
date: 2026-06-28
tags: [AI活用, 製造業, 輸出, 輸入, 英文インボイス, パッキングリスト, 貿易書類, ChatGPT]
description: "製造業の輸出入に必要な英文インボイス・パッキングリスト・原産地証明の下書き・英訳をChatGPTで行う方法を解説。貿易書類のAI活用プロンプトを公開します。"
---

製造業で海外への輸出や海外からの輸入が発生する場合、英文インボイス・パッキングリスト・原産地証明書などの英語書類の作成が必要です。英語が得意でなくても、AIを使えば書類の下書き・英訳・確認を効率化できます。

---

## 英文インボイス（Commercial Invoice）を作るプロンプト

輸出時に必要な英文インボイス（商業送り状）の下書きを作ります。

```
以下の情報をもとに、輸出用の英文インボイス（Commercial Invoice）を
作成してください。

【輸出者情報（Seller/Exporter）】
会社名: （例：○○ Manufacturing Co., Ltd.）
住所: （例：1-2-3 Sangyo, Nagoya-shi, Aichi, 460-0000, Japan）
電話: / FAX: / Email:

【輸入者情報（Buyer/Consignee）】
会社名: （例：ABC Auto Parts Inc.）
住所: （例：123 Industrial Blvd, Detroit, MI 48201, USA）

【貨物情報】
Invoice No.: （例：INV-2026-0123）
Invoice Date: （例：June 28, 2026）
L/C No.（信用状番号）: （例：なし / ある場合は記入）
支払条件（Terms of Payment）: （例：T/T 30 days after B/L）
取引条件（Terms of Delivery）: （例：FOB Nagoya）
船積港・仕向地: （例：Nagoya, Japan → Los Angeles, USA）

【明細】
品番 / 品名（英語） / 数量 / 単価（USD） / 金額:
（例：
A-1234 / Steel Bracket, Press Formed, Zinc Plated / 500 pcs / USD 12.50 / USD 6,250.00
B-5678 / Welded Sub-Assembly, SPCC / 200 pcs / USD 28.00 / USD 5,600.00
）

出力形式:
・実際に使える英文インボイスのフォーマット
・小計（Subtotal）/ 運賃（Freight）/ 保険料（Insurance）/ 合計（Total Amount）の計算欄
・「This invoice is true and correct」の証明文言
・Country of Origin（原産国: Japan）の記載
```

---

## パッキングリスト（英文）を作るプロンプト

輸出梱包明細書（英文パッキングリスト）を作ります。

```
以下の情報をもとに、輸出用の英文パッキングリスト（Packing List）を
作成してください。

【基本情報】
対応するインボイス番号: （例：INV-2026-0123）
荷送人（Shipper）: （例：○○ Manufacturing Co., Ltd.）
荷受人（Consignee）: （例：ABC Auto Parts Inc.）
梱包日: （例：June 28, 2026）

【梱包明細】
（ケースごとの情報）
Case No.1:
  品番・品名: （例：A-1234 Steel Bracket）
  数量: （例：250 pcs）
  寸法（L×W×H）: （例：60cm × 40cm × 30cm）
  毛重量（Gross Weight）: （例：18.5 kg）
  正味重量（Net Weight）: （例：15.2 kg）
Case No.2:
  品番・品名: （例：A-1234 Steel Bracket）
  数量: （例：250 pcs）
  （以下同様）

【合計】
総ケース数: （例：6 Cases）
合計毛重量: （例：110 kg）

出力形式:
・実際に使える英文パッキングリストのフォーマット
・各ケースの寸法・重量を表形式で
・容積重量（Volume Weight）の計算欄（L×W×H÷6000）
```

---

## 原産地証明書（Certificate of Origin）の依頼文を作るプロンプト

商工会議所への原産地証明書発給依頼文を作ります。

```
以下の情報をもとに、商工会議所への
原産地証明書（Certificate of Origin）発給依頼文を
日本語で作成してください。

【基本情報】
申請者: （例：○○製作所 代表取締役 ○○）
申請日: （例：2026年6月28日）
輸出先国: （例：アメリカ合衆国）
インボイス番号: （例：INV-2026-0123）
品名: （例：鉄鋼製ブラケット（JIS G 3141準拠））
原産地: 日本

【依頼のポイント】
・EPA（経済連携協定）の特恵関税を適用するため、
  FTA/EPAに対応した原産地証明書が必要
・または: 一般的な非特恵原産地証明書で問題なし

出力形式:
・商工会議所への申請依頼書（正式書類として使える形式）
・「原産性の根拠となる書類（インボイス写し等）を添付します」の文言
・問い合わせ先・担当者名欄
```

---

## 英文での取引先メール（輸出関連）を作るプロンプト

海外取引先へのビジネス英語メールを作ります。

```
以下の状況で、海外取引先への英文メールを作成してください。

【状況の選択（いずれかを選ぶ）】

パターン①: 出荷通知メール
状況: （例：2026年6月28日に貨物を出荷した。
  B/L番号・船名・ETA（到着予定日）を伝える）
伝えたい内容:
  ・B/L番号: OOCL-2026-1234
  ・Vessel: ONE ALTAIR V.001E
  ・ETA Los Angeles: July 15, 2026
  ・添付書類: Invoice / Packing List / B/L写し

パターン②: 輸出価格の見積りメール
状況: （例：海外取引先から部品の輸出見積りを依頼された）
条件:
  ・品番・品名: A-1234 Steel Bracket
  ・数量: 1,000 pcs/month（予定）
  ・価格: USD 12.50/pc（FOB Nagoya）
  ・納期: 6 weeks ARO（Receipt of Order後）

出力形式:
・実際に送れるビジネス英文メール（自然で丁寧な英語）
・件名（Subject）も含める
・「Please feel free to contact us if you have any questions.」の締め
```

---

### 関連記事

- [梱包仕様書・出荷明細書をAIで作る方法](/forge-labs-blog/2026/06/28/packaging-spec-shipping-doc-ai.html)（国内梱包・出荷）
- [請求書・送付状をAIで作る方法](/forge-labs-blog/2026/06/27/invoice-ai.html)（国内請求書）
- [品質成績書・検査成績書（CoC）をAIで整理する方法](/forge-labs-blog/2026/06/28/quality-certificate-ai.html)（英文CoC）
- [外国人労働者向け多言語文書をAIで作る方法](/forge-labs-blog/2026/06/27/multilingual-document-ai.html)（多言語対応）

---

[→ 中小製造業向けAI業務効率化プロンプトテンプレート集 Volume1（note ¥1,980）](https://note.com/jolly_okapi4595/n/n5ce0e322594e)
