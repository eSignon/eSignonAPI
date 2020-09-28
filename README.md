# API説明

* esignon の API は Header-Body 形式であり
* Bodyデータ形式もプロトコルコードとversion管理のためにHeader - Body形式で提供します。
* 形式ex\) Header - Body \(Header - Body\)
* 一部のAPIの場合はBodyの形式が異なる場合があります。 各APIの説明を参考にしてください。
* esignon APIを使用する際には企業固有のクライアントIDが必要です。
*  クライアントIDの発行は、[カスタマーサポート](https://esignon.net/jp/customer/)をご利用ください。
* 使用順序）クライアントID発行\(会社問い合わせ\) -認証トークン発行 -認証トークンを利用してAPIを使用
* ※Headerトークン値の入力形式を必ずお守りください。※

## 例\) Header

![](.gitbook/assets/head.png)

Headerの場合、最大2つの入力値が与えられ、トークン発行APIを除くすべてのAPIは、Authorizationにトークン値を入力して要請しなければなりません。 esignon とトークン値の間はスペースを必ず開けて入力することが必要です。

## 例\) Body

```jsx
{
    "header": {
        Key : "value"
    },
    "body": {
        key : "value"
    }
}
```

Bodyの場合、request時に上記のようにbodyの中にヘッダー値とbodyのkey,valueをそれぞれ作成して要請することが必要です。 中に入るkey,valueの例は各APIに明示されています。

