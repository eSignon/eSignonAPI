# 非対面契約開始 - ExportAPI 説明

エクスポートAPIとは、非対面契約の開始時にエクスポート\_api\_info Parameterの値を通じて設定した情報に基づいて、契約者が契約書を承認し、却下時に設定値を基に作成されたJSON形式のbodyを設定したURLにエクスポートして、該当会社側から受け取ることができるようにする機能です。

request\_codeにユーザー定義の代わりに「embed」を入力すると、契約書進行のURLがエキスポートされ、カカオトークとメール通知は契約者に送信されません。 エクスポートを受信したURLに基づき、お客様側で別途に発送を行うことができます。

embed Code を使用する場合は、最初の非対面契約の呼び出し時にresponse に契約開始 URL を提供し、契約の進行時に署名者が契約書を承認、却下するたびにエクスポートで進行 URL と入力した契約者の番号、または電子メールを提供します。\(電子メール、番号で呼び出した場合は番号\) 契約完了時に文書のダウンロード、履歴認証書のダウンロード URL を提供します。

## Parameter 

| **Parameter Name**                         | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| export\_api\_info | Array | Optional | 作成データをエクスポートする時に設定する値 |
| export\_api\_info.api\_type | String | Required | "StartAndEnd"\(始まりと終わりだけ\) or "ALL"\(全て\) |
| export\_api\_info.url | String | Required | 通信を受けるurl |
| export\_api\_info.request\_code | String | Optional | 顧客が定義する任意のvalue or "embed" \(Export APIの説明参照\) |
| export\_api\_info.clientid | String | Optional | esignonから発行されたID\(発行は[お問い合わせ](https://esignon.net/jp/customer/)\) |
| export\_api\_info.authorization | String | Optional | データの受信時にヘッダーauthorizationに設定したいvalue |
| export\_api\_info.request\_params | Array | Optional | 文書の内部に特定の値を受け取りたいときに使用 |
| export\_api\_info.request\_params.param\_id | String | Required | 受信パラメータ名\(ユーザー指定\) |
| export\_api\_info.request\_params.param\_value | String | Required | Params.fieldsで受信する値が文書にない場合に受信する基本value |
| export\_api\_info.request\_params.fields | Array | Required | 書式内部にあるフィールド名を照会し、フィールド名に該当する値が文書に存在する場合、param\_valueの代わりに入るvalue |
| export\_api\_info.request\_params.fields.doc\_id | String | Required | 書式ID |
| export\_api\_info.request\_params.fields.field\_name | String | Required | 値を取得する書式内のフィールド名 |

## export\_api Response\) 

```javascript
{
	"header": {
		"api_name": "export",
		"session_id": "S1001",
		"request_code": "{ exportAPI_info で指定したrequest_code value }",
		"authorization":"{ 非対面契約API使用時に設定したauthorization value }"
	},
	"body": {
		"clientid": "{ eSignonAPI使用のためのUnique ID }",
		"processid": "1", //文書の進行段階の区分値
		"requestid": "{ ヘッダーのrequest_code value }",
		"actionid": "1", //文書の進行段階の区分値
		"workdatetime": "2020-01-31 04:23:28.0", //作成完了時間
		"worktype": "CF", //CF=承認、RT=返却（最初の契約者が返戻した場合、文書はキャンセルされます。）
		"wfuid": "{}", //
		"useremail": "{ 署名者 email }", 
		"opinion": "", //承認、差し戻し時に顧客が差し戻しメッセージ、転送メッセージを使用した場合に出力
		"param_id": "param_value", // fields値を設定した場合、fields_valueをreturn
	}
}
```

## Export\_api Response 例\) code-embed 状態のとき \(進行中\)

```javascript
{
	"header": {
		"api_name": "export",
		"session_id": "S1001",
		"request_code": "{embed}"
	},
	"body": {
		"wfluid": "0",
		"clientid": "{ eSignonAPI使用のためのUnique ID }",
		"processid": "1", //文書の進行段階の区分値
		"requestid": "{ embed }",
		"actionid": "1", //文書の進行段階の区分値
		"workdatetime": "2020-01-31 04:23:28.0", //作成完了時間
		"worktype": "CF",//CF=承認、RT=返却（最初の契約者が返戻した場合、文書はキャンセルされます。）
		"wfuid": "{}",
		"useremail": "{ 署名者 email }", 
		"opinion": "", //承認、差し戻し時に顧客が差し戻しメッセージ、転送メッセージを使用した場合に出力
		"param_id": "param_value",
		"next_play_user":"{次の順番にサインするEメール}",
		"play_url":"{次の順番にサインインするお客様にお渡しするURL}",
		"status":"{Playing}", // 進行状態 - Playing(進行中) Complete(完了)
		"next_user_name":"{次の署名者の名前}",
		"user_name":"{現在の署名者名}"
	}
}
```

## Export\_api Response 例）code-embed 状態のとき（完了）

```javascript
{
	"header": {
		"api_name": "export",
		"session_id": "S1001",
		"request_code": "{embed}"
	},
	"body": {
		"wfluid": "0",
		"clientid": "{ eSignonAPI使用のためのUnique ID }",
		"processid": "1", //文書の進行段階の区分値
		"requestid": "{ embed }",
		"actionid": "1", //文書の進行段階の区分値
		"workdatetime": "2020-01-31 04:23:28.0", //作成完了時間
		"worktype": "CF",//CF=承認、RT=返却（最初の契約者が返戻した場合、文書はキャンセルされます。）
		"wfuid": "{}",
		"useremail": "{ 署名者 email }", 
		"opinion": "", //承認、差し戻し時に顧客が差し戻しメッセージ、転送メッセージを使用した場合に出力
		"param_id": "param_value",
		"cert_url":"{履歴証明書ダウンロードURL}",
		"download_url":"{文書ダウンロードURL}",
		"status":"{Playing}", // 進行状態 - Playing(進行中) Complete(完了)
		"user_name":"{現在の署名者名}"
	}
}
```

