---
title: "weserv/images — オープンソースの画像プロキシ＆キャッシュサービス"
date: 2025-10-12
authors: [dsitweed]
categories:
  - テクノロジー
  - バックエンド
  - インフラ
tags:
  - weserv
  - 画像処理
  - プロキシ
  - キャッシュ
  - Docker
  - AWS
comments: true
---

## 🚀 weserv/images — オープンソースの画像プロキシ＆キャッシュサービス

**weserv/images** は、サービス **wsrv.nl** (旧 *images.weserv.nl*) のソースコードで、自分のサーバーで **画像処理サービス (image proxy / image server)** を実行できます。([weserv/images GitHub repo][1])

### 🔍 内容＆主な機能

* 画像処理操作のサポート: resize, crop, format conversion, 画像最適化。
* **libvips** などの強力なライブラリを使用して、高性能な画像処理を実現。
* **nginx** をウェブサーバー、リバースプロキシ、HTTPキャッシュとして組み合わせ、パフォーマンスを最適化。
* Docker 構成のサポートで、自分のサーバー環境へのデプロイが簡単。
* ソースコードは **BSD-3-Clause License** でライセンスされており、使用、修正、プロジェクトへの統合が可能。

### 🛠 アプリケーション＆利点

* ウェブまたはモバイルアプリケーションの **image proxy server** として使用: すべての画像リクエストがこのサービスを経由して resize / 最適化 / キャッシュされ、メインデータベースの負荷を軽減。
* 画像品質、セキュリティ、独自ルール (例: watermark, モバイル最適化) を制御したい場合、このリポジトリは独自画像ソリューションを構築する優れた基盤。
* 高性能 (libvips + キャッシュ) で、大規模画像処理が可能で、パフォーマンスへの影響が少ない。
* 大規模プロジェクトに画像サービスを統合したいが、サードパーティに依存したくない場合に適している。

---

## 🔧 具体的な動作

URL を以下のように送信すると:

```
https://images.weserv.nl/?url=https://example.com/image.jpg&w=400&h=300&fit=cover
```

システムは:

1. 🛰 **Proxy request** – `https://example.com/image.jpg` からオリジナル画像をダウンロード
2. 🧠 **画像処理** – **libvips** を使用して resize, crop, フォーマット変換、圧縮など
3. 📦 **結果のキャッシュ** – 処理済み画像を (通常 nginx + ローカルキャッシュまたは CDN で) 保存
4. ⚡ **最適化画像を返却** – エンドユーザーに最適化画像を提供

---

## 💡 利点

* **オリジナルサーバーの負荷軽減** (画像は一度処理され、次回はキャッシュから提供)
* **画像表示速度の向上** (軽量でデバイスに適したサイズ)
* **画像ソースのセキュリティ** (ユーザーは本当の URL を知る必要なし)
* **拡張性** – Docker でセルフホスト可能

---

## 📦 キャッシュの仕組み

### 🟢 1️⃣ 公開サービス使用時: [https://images.weserv.nl](https://images.weserv.nl)

* API 呼び出し例:

  ```
  https://images.weserv.nl/?url=https://example.com/image.jpg&w=400
  ```

  → weserv.nl のサーバーが:

  1. `example.com` からオリジナル画像をダウンロード
  2. 処理 (resize, crop, 圧縮など)
  3. 内部キャッシュ (disk または CDN) に一時保存

* **画像の保存期間?**

  * リポジトリは正確なキャッシュ時間を公開していないが、GitHub の issue と discussion によると:

    * **画像は一定期間 (通常数日～数週間) キャッシュ**、サーバーと CDN による。
    * キャッシュは自動的に期限切れまたは容量満了で削除。
    * オリジナル画像が変更されても、キャッシュがリフレッシュされるまで古い画像が提供される可能性。

* 🚫 つまり:

  * weserv.nl を **永久ストレージ** と見なさない。
  * これは **一時的な proxy + CDN キャッシュ** のみ。
  * オリジナル画像は自分のサーバー (`example.com`) に存在する必要あり — オリジナルが削除されると、キャッシュ期限後に再作成不可。

### 🔵 2️⃣ セルフホスト時: weserv/images

* **キャッシュポリシーを自分で定義可能**:

  * **Redis**, **disk**, または **CDN** (Cloudflare, Fastly など) でキャッシュ
  * TTL (time-to-live) を任意に設定: 1日、1週間、1ヶ月、無期限。
* オープンソースなので:

  * キャッシュパスのカスタマイズ
  * 処理済み画像をローカルストレージまたは S3 に保存
  * オリジナル画像変更時にキャッシュをアクティブに無効化

---

## ⚡ 簡単まとめ

| ケース                          | 画像保存場所         | 保存期間                       | 備考                          |
| ------------------------------- | -------------------- | ------------------------------ | ----------------------------- |
| `images.weserv.nl` (公開) 使用 | weserv のキャッシュサーバー | 不定 (数日～数週間)            | 永久保存なし、proxy のみ      |
| weserv/images セルフホスト     | 自分のサーバーまたは CDN | 自分で設定                     | 必要に応じて長期保存可能      |

---

## 🔄 画像変更時の対応

`images.weserv.nl` は **image proxy cache** として動作するため:

* オリジナル URL (例: `https://images.weserv.nl/?url=example.com/image.jpg`) を送信すると:

  1. `example.com` からオリジナル画像を取得。
  2. システムにキャッシュ。
  3. 以後のリクエストにキャッシュ画像を返却。

⚠️ しかし:

* Weserv は **オリジナル画像の変更を自動チェックしない**。
* キャッシュされた画像は **期限切れまたは削除されるまで古いまま提供**。

✅ **解決策:**

* オリジナル画像が変更され、新しい画像が必要なら、query string を少し変更 (例: `?t=timestamp`（例えば：updated_at timestamp） または `?v=2`)、以下のように:

  ```
  https://images.weserv.nl/?url=example.com/image.jpg&t=1760281316
  ```

  => URL が異なるため、weserv は新しいオリジナル画像を再ダウンロード。

---

## 🏗 セルフホストのアイデア

完全に実現可能 💡
[weserv/images](https://github.com/weserv/images) は **オープンソース** なので:

* 独自インフラ (Docker, Kubernetes など) にサービスをデプロイ
* `images.weserv.nl` と同様に **resize, crop, optimize, cache** に使用。

👉 セルフホストの利点:

* キャッシュ / invalidation の完全制御。
* Rate limit なし。
* サードパーティ依存の削減。
* 認証やプライベート CDN の追加統合可能。

---

## ⚖️ AWS サービスとの比較

| シナリオ                                                                 | Weserv を使用すべきか?          | 説明                                                                                                  |
| ------------------------------------------------------------------------ | ------------------------------- | ----------------------------------------------------------------------------------------------------- |
| **静的画像のストレージ + キャッシュ** のみ必要                         | ❌ 不要                          | S3 + CloudFront で十分: キャッシュ、グローバル CDN、バージョン管理あり。                              |
| **動的画像変換** (例: thumbnail, webp, サイズ削減) が必要               | ✅ Weserv または独自構築         | Weserv/images に画像処理パイプラインあり。AWS では Lambda@Edge または Image Handler を構築する必要。 |
| AWS Lambda / CloudFront Functions より低コストで制御したい             | ✅ 可能                          | Weserv は C/C++ (libvips) で動作し、大規模画像処理で Lambda より軽量・効率的。                        |

---

👉 **まとめ:**

* `weserv/images` は **dynamic image transformation** (resize, crop, convert など) が必要な場合に有用。
* 静的画像の CDN キャッシュのみなら、**S3 + CloudFront** で十分、速く信頼性が高い。

---

[1]: https://github.com/weserv/images "GitHub - weserv/images: Source code of wsrv.nl (formerly images.weserv.nl), to be used on your own server(s)."
