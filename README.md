# しずかなインターネット API Docs


> **Warning**
> APIは現在ベータ版であり、仕様が変更される可能性があります。

エンドポイントの一覧と仕様は[しずかなインターネット APIリファレンス](https://catnose99.github.io/quiet-internet-api-docs)をご確認ください。

## はじめる前に

- このAPIは自分の記事データを取得するために利用します。他のユーザーのデータを取得することはできません。
- APIは[プロジェクトのスポンサー](https://sizu.me/sponsors/purchase)のみが利用できます。

### 想定される利用方法
1. 自分の記事のデータを外部サービスへ定期的にバックアップする
2. 記事のデータを自分のサイトに表示する

## リクエスト

エンドポイントのURLは`https://sizu.me/api/`から始まります。

> **Warning**
> URLは**http**ではなく**https**で始まる必要があります。

## 認証

APIを利用するには、APIキーが必要です。プロジェクトのスポンサーになると、[スポンサー設定](https://sizu.me/dashboard/settings?tab=sponsor)からAPIキーを取得できます。

リクエスト時には、以下のように`Authorization`ヘッダーにAPIキーを指定します。

```
Authorization: Bearer sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## レスポンス

レスポンスはJSON形式で返されます。ステータスコードには以下のいずれかが指定されます。

- 200: リクエストが成功した場合
- 400: リクエストが不正な場合（e.g. パラメータの指定が不適切）
- 401: 認証に失敗した場合
- 404: リソースが存在しない場合
- 429: レート制限を超えた場合
- 500: サーバー内部でエラーが発生した場合

日時のフォーマットはISO 8601形式です。

## レート制限

APIのリクエスト数は、5分間につき300回までとなっています。レート制限を超えた場合は、`429 Too Many Requests`が返されます。レスポンスヘッダから、現在のレート制限に関する情報を確認できます。

```
x-ratelimit-limit: 300
x-ratelimit-remaining: 299
x-ratelimit-reset: 1691806076122
```

## エンドポイント

エンドポイントの一覧と仕様は[しずかなインターネット APIリファレンス](https://catnose99.github.io/quiet-internet-api-docs)をご確認ください。
