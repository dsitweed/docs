---
title: "Cloudflare Worker"
date: 2025-10-15
authors: [dsitweed]
comments: true
---


# Cloudflare WorkerとBindingのかんたん紹介（KV & D1編）

最近、Cloudflareは安くて使いやすいサービスとして人気です。
AWSのLambda、S3、API Gatewayのかわりにも使えます。

## Cloudflare Workerとは

Cloudflare Workerはサーバーレスです。
JavaScriptなどのコードを世界中のCloudflareのネットワークで動かせます。

## Bindingとは

Workerでは、`env.URLS`のように、外のデータや変数をWorkerで使えるように“つなぐ”ことができます。
これをCloudflareでは**Binding**と言います。

> AWS LambdaにはBindingはありません。Lambdaでは環境変数やHTTP API、AWS SDK + IAMでサービスにアクセスします。

## KV StorageとのBinding

KV Storageはキーと値のデータベースです。
Workerから簡単に読み書きできます。
例：クリック数をカウントしたり、短いURLを保存したりできます。

## D1 SQL DatabaseとのBinding

D1はSQLのデータベースです。
Workerからクエリを送ってデータをさわれます。
複雑な検索や集計に便利です。

---

まとめ：Cloudflare Worker + KV/D1を使うと、サーバーを用意しなくても速くて世界中で動くアプリが作れます。
次は、KVとD1をつないで簡単なデモを作ってみましょう。

---
