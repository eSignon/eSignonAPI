# 非対面契約開始

* 非対面契約書式を始めます。
* エクスポート\_api値を別途に設定して、受信する値の形式を指定できます。（オプション）
* エクスポート\_apiとは、お客様が進行中に承認·差し戻しをする場合、設定された値を設定されたURLに、esignonでrequestする機能です。
* ※ Arrayタイプのパラメータがoptionalの場合は、使用の際にArray内部パラメータ値のうち必須値は必ず入力してください。 お使いにならない場合は、ご入力いただかなくても構いません。
* ※ language パリメータの場合、デフォルト値"ko-KR" \(設定しなかった場合\)

## API URL Info

| Url | Type | **Code** |
| :--- | :--- | :--- |
| https://docs.esignon.net/api/{CompID}/startsimple | POST | 5005Q |

## Request

### Parameters

#### PathParameters

| **Parameter Name** | DataType | **Description** |
| :--- | :--- | :--- |
| CompID | String | 会社 ID |

####  Headers

| **Parameter Name**                         | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| Content-Type | String | Required | "application/json" |
| Authorization | String | Required | "esignon {accesstoken}" |

####   Body 

  Body - Header Parameter

| **Parameter Name**                         | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| request\_code | String | Required | "5005Q" |
| version | String | Required | "9.9.99" |

  Body - Body Parameter

| **Parameter Name** | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| biz\_id | String | Required | "0" |
| workflow\_name | String | Required | 開始する文書の名前 |
| doc\_id | String | Required | 開始する書式ID |
| memb\_email | String | Required | 契約開始者Email |
| language | String | Optional | "ko-KR", "en-US", "ja-JP" |
| comment | String | Optional | 配信メッセージ |
| player\_list | Array | Required | 署名者の情報は、テンプレート段階に従って作成されなければならない。 |
| player\_list.field\_owner | String | Required | 作成順序"1"からスタート |
| player\_list.email | String | Required | Email |
| player\_list.name | String | Required | 契約進行者名 |
| player\_list.password\_hint | String | Optional | 文書パスワードヒント |
| player\_list.password | String | Optional | 文書パスワード設定 |
| field\_list | Array | Optional | あらかじめ入力する値がある場合、追加する値RadioBox、CheckBox、LabelBox、TextBox のみあらかじめ値を入力可能 |
| field\_list.field\_name | String | Optional | 書式フィールド名 |
| field\_list.field\_value | String | Optional | 書式フィールド値Radio、Check Boxの場合の値を\("N" or "Y"\)で受信Label、Text Boxの場合はテキスト値をそのまま受信 |
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
| customer\_list | Array | Optional | 参照者がいる場合、追加 |
| customer\_list.email | String | Required | Email |
| customer\_list.name | String | Required | 参照者名 |
| customer\_list.language | String | Optional | ko-KR, en-US, ja-JP |

## Request Body Example

```javascript
{
	"header": {
		"request_code": "5005Q",
		"version": "9.9.99"
	},
	"body": {
		"biz_id": "0",
		"workflow_name": "{ 開始する文書の名前 }",
		"memb_email":"{ 契約開始者Email }",
		"doc_id": "{ 開始する書式ID }",
		"language": "ja-JP",
		"comment": "",
		"player_list": [{
			"field_owner": "1",//(step)
			"email": "{ 署名者 Email }",
      "name":"{ 署名者 name }",
			"language": "{ ja-JP }",
      "password_hint":"{ 文書パスワードヒント }",
      "password":"{ 文書パスワード設定 }"
		},{
			"field_owner": "2",
			"email": "{}",
      "name":"{}",
			"language": "{}",
      "password_hint":"{}",
      "password":"{}"
		}],
		"field_list": [{
				"field_name": "{ field_name }",
				"field_value": "{ field_value }"
			}
		],
		"customer_list": [{ // 参照者 list
				"email": "{ 参照者 Email }",
	      "name":"{ 参照者 Name }",
				"language": "{ja-JP}"
		}],
		"export_api_info": {
				"api_type": "{ StartAndEnd or ALL }",
				"url": "{ 通信を受けるurl }",
				"request_code": "{ 顧客が定義する任意のvalue or "embed" (Export APIの説明参照) }",
				"clientid": "{ esignonから発行されたID }",
				"authorization":"{ データの受信時にヘッダーauthorizationに設定したいvalue }",
	      "request_params": [{
								"param_id": "{受信パラメータ名(ユーザー指定)}",
								"param_value": "{Params.fieldsで受信する値が文書にない場合に受信する基本value}",
								"fields": [{ // 書式内部にあるフィールド名を照会し、フィールド名に該当する値が文書に存在する場合、param_valueの代わりに入るvalue
														 //	  filed_name not exist - param_id:param_value return  
														 //	  filed_name exist - param_id:field_value return
                            "doc_id":"{ 文書 ID }",
                            "field_name":"{ 文書 field name }" 
          			}]
				}]
	   }
	}
}
```

## Request Body Example - only Required

```javascript
{
	"header": {
		"request_code": "5005Q",
		"version": "9.9.99"
	},
	"body": {
		"biz_id": "0",
		"workflow_name": "{ 開始された文書名 }",
		"memb_email":"{ 契約開始者Email }",
		"doc_id": "{文書 ID}",
		"language": "ja-JP",
		"player_list": [{
			"field_owner": "1",
			"email": "{ 署名者 Email }",
			"name": "{ 署名者 name }"
		}, {
			"field_owner": "2",
			"email": "{}",
			"name": "{}"
		}]
	}
}
```

## Request Body Example - For TEST Account

```javascript
{
	"header": {
		"request_code": "5005Q",
		"version": "9.9.99"
	},
	"body": {
		"comp_id": "testapi",
		"biz_id": "0",
		"memb_email": "guide@esignon.net",
		"language": "ja-JP",
		"comment": "",
		"workflow_name": "TEST-NAME",
		"doc_id": "1",
		"player_list": [{
				"field_owner": "1",
				"email": "guide@esignon.net",
				"name": "TEST",
				"language": "ja-JP"
			},
			{
				"field_owner": "2",
				"email": "guide@esignon.net",
				"name": "TEST",
				"language": "ja-JP"
			}
		],
		"field_list": [{
			"doc_id": "1",
			"field_name": "name",
			"field_value": "name-value"
		}],
		"customer_list": [{
			"email": "guide@esignon.net",
			"name": "TEST",
			"language": "ja-JP"
		}]
	}
}
```

## Response

| Code | **Description** | **Reference** |
| :--- | :--- | :--- |
| 200 | 成功 | 成功 |
| 400 | 失敗 |  |

#### Result\_msg

| Code | **Description** | **Reference** |
| :--- | :--- | :--- |
| 00 | 成功 | 成功 |
| 10 | 失敗 | 失敗 |
| 12 | 失敗 | 受信メッセージのBody情報が正しくない形のため、パスできませんでした。 |
| 99 | 失敗 | Unexpected exception（誤ったフォーマット） |

## Response Body Example

```javascript
{ 
 "header":{
   "session_id": "S1001", 
   "response_code": "5005A",
   "result_code": "00", 
   "result_msg": "Work Flow Start", 
   "version": "9.9.99" }, 
 "body":{ 
   "comp_id": "{ 会社 ID }", 
   "biz_id": "0", 
   "memb_email": "{ 契約開始者Eメール }", 
   "workflow_id": "{ 文書ID }", 
   "workflow_name": "{ 開始された文書名 }", 
   "token": "{ 文書を始めた人が契約の最初の作成者である場合、作成ページにアクセスするときに使用するトークンvalue }", 
   // https://docs.esignon.net/mail/sign?token=
   // Enter the token value issued to the above address to access the signature page
   "lang": "ja-JP" }
}
```

## Response export\_api Example

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

