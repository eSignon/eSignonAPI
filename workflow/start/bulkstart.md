# 大量契約の開始

* 大量契約転送を開始します

* 大量契約時の署名順序は、書式を作成する際に設定した段階によって、顧客、担当者が文書を受け取る順序が決まります。 \(1段階のみ設定時に顧客にのみ伝達\)担当者は生成者として固定され、顧客情報はunset\_player\_listに入った値に決定されます。 unset\_player\_listに入っているすべての顧客に契約が送信されます。

## API URL

| Url | Type | **Code** |
| :--- | :--- | :--- |
| https://docs.esignon.net/JEDOC/Common.do | POST | 1410Q |

## Request

### Parameters

####  Headers

| **Parameter Name**                         | DataType | **Description** |
| :--- | :--- | :--- |
| Content-Type | String | application/json |
| Authorization | String | esignon {token} |

####   Body 

  Body - Header Parameter

| **Parameter Name**                         | DataType | **Description** |
| :--- | :--- | :--- |
| request\_code | String | "1410Q" |
| request\_msg | String | "Start Work Flow Bulk Sending" |
| session\_id | String | "thread\_023" |
| version | String | "9.9.99" |

  Body - Body Parameter

| **Parameter Name** | DataType | **Description** |
| :--- | :--- | :--- |
| comp\_id | String | 会社ID |
| biz\_id | String | "0" |
| memb\_email | String | 文書生成者Email |
| workflow\_name | String | "" |
| workflow\_lib\_id | String | 書式を作成すると生成されるlid\_id リスト照会で確認可能 |
| unset\_player\_list | Data | 署名するお客様の情報を入力 |
| unset\_player\_list.memb\_id\_type | String | "EMail" |
| unset\_player\_list.email | String | Email address |
| unset\_player\_list.name | String | 契約進行者名 |
| unset\_player\_list.language | String | "ko-KR","en-US","ja-JP" |
| unset\_player\_list.workflow\_name | String | 開始するドキュメント名 |
| unset\_player\_list.enable\_mobile\_cert | String |  "false" \( モバイルは韓国でのみサービスされます。\) |
| unset\_player\_list.mobile\_number | String | "" \( モバイルは韓国でのみサービスされます。\) |
| unset\_player\_list.enable\_password\_cert | String | パスワード認証機能「True or false」 |
| unset\_player\_list.password\_hint | String | パスワードヒント |
| unset\_player\_list.password | String | パスワード |
| field\_list | Data | 契約開始時にフィールドに値を入力して転送する場合に使用するフィールド |
| field\_list.doc\_id | String | 書式ID |
| field\_list.field\_name | String | 書式フィールド名 |
| field\_list.field\_value | String | 該当フィールドに入力したい値 |
| comment | String | "" |
| enable\_legal\_agreement | String | "false" |

## Request Body Example

```javascript
{
  "header": {
    "request_code": "1410Q",
    "api_name": "Start Work Flow Bulk Sending",
    "session_id": "",
    "version" : "9.9.99"
  },
  "body": {
    "comp_id": "{文書ID}",
    "biz_id": "0",
    "memb_email": "{ 文書生成者Email }",
    "workflow_lib_id": "{ templete lib_id }",
    "workflow_name": "",
    "unset_player_list": [
      {
        "memb_id_type" : "{ EMail }",
        "email": "{ email adress }",
        "name" : "{ 契約進行者名 }",
        "language": "ja-JP",//ko-KR, ja-JP, en-US
        "workflow_name" : "{ 開始するドキュメント名 }",
        "enable_mobile_cert" : "flase",//( モバイルは韓国でのみサービスされます。)
        "mobile_number" : "",//( モバイルは韓国でのみサービスされます。)
        "enable_password_cert":"{true or false}",
	      "password_hint":"{パスワードヒント}",  		
	      "password":"{パスワード}",
        "field_list": [{ // 契約開始時にフィールドに値を入力して転送する場合に使用するフィールド
      				"doc_id": "{ 書式ID }",
      				"field_name": "{ 書式フィールド名 }",
      				"field_value": "{ 該当フィールドに入力したい値 }"
			}]
      }
      ],// 設定したプレイヤーすべてに発送されます。
    "comment": "",
    "enable_legal_agreement":"false"
  }
}
```

## Response

| Code | **Description** | **Reference** |
| :--- | :--- | :--- |
| 200 | 成功 | 成功 |
| 400 | Connection failed |  |

#### Result\_msg

| Code | **Description** | **Reference** |
| :--- | :--- | :--- |
| 00 | 成功 | 成功 |
| -1 | 失敗 | 受信メッセージのBody情報が正しくない形のため、パスできませんでした。 |
| 10 | 失敗 | 当該WorkFlow Libraryが存在しません。 |
| 11 | 失敗 | 失敗しました。 |
| 12 | 失敗 | 許容された保存容量を超過しました。 |
| 13 | 失敗 | 可能な文書数を超過します。 |
| 14 | 失敗 | 利用期間が満了しました。 |
| 15 | 失敗 | 作成者の設定が正しくありません。 |

## Response Body Example

```javascript
}
	"body":{
		"workflow_list":[
			{
			"workflow_id": "{文書ID}",
			"unset_player_email": "{署名者 email}",
			"unset_player_name": "{署名者 name}",
			"result": "OK",
			"description": "",
			"workflow_name": "{文書名}",
			"token": "{accesstoken}",
			"lang": "ja-JP",
			"reg_date": "{会社決済更新日}"},
			"comp_id": "{会社ID}",
			"biz_id": "0",
			"memb_email": "{生成者Eメール}",
			"workflow_lib_id": "{書式を生成すると生成されるlid_idwfUIDとは異なる値}"
			},
	"header":{
		"session_id": "thread_023",
		"response_code": "1410A",
		"result_code": "00",
		"result_msg": "Start Work Flow bulk Sending.",
		"version": "9.9.99"
	}
}
```

