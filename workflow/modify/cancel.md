# 取り消し、廃棄

* 文書を削除または廃棄します。
* キャンセル - 進行中の文書をキャンセル処理します。
* 廃棄 - 完了した文書を廃棄処理します。

## API URL

| Url | Type | **Code** |
| :--- | :--- | :--- |
| https://docs.esignon.net/JEDOC/Common.do | POST | 1510Q |

## Request

### Parameters

####  Headers

| **Parameter Name**                         | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| Content-Type | String | Required | "application/json" |
| Authorization | String | Required | "esignon accesstoken" |

####   Body 

  Body - Header Parameter

| **Parameter Name**                         | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| request\_code | String | Required | "1510Q" |
| request\_msg | String | Required | "" |
| request\_lang | String | Optional | "ko","en","ja" |
| session\_id | String | Required | "thread\_023" |
| version | String | Required | "9.9.99" |

  Body - Body Parameter

| **Parameter Name** | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| comp\_id | String | Required | 会社ID |
| biz\_id | String | Required | "0" |
| memb\_email | String | Required | 使用者 email |
| workflow\_id | String | Required | 文書ID |
| command | String | Required | 「cancel」 - キャンセル 「disposal」 - 廃棄。 |
| description | String | Optional | 「disposal」時には必須値 - 「廃棄事由」 |
| timezone\_offset | String | Optional | 「disposal」時には必須値 - 「UTC時間値入力」「+00:00」 |

## Request Body 例\)

```javascript
{
	"header": {
			"request_code": "1510Q",
			"request_msg": "",
	    "request_lang":"{ko or ja or en}",
			"session_id": "session_id",
			"version": "9.9.99"
	},
	"body": {
			"comp_id": "{会社ID}",
      "biz_id":"0",
      "memb_email":"{使用者 email}",
      "workflow_id":"{文書ID}",
      "command":"{ CANCEL or DISPOSAL }",
      "description":"{廃棄事由の入力}", // 
      "timezone_offset":"+00:00" // 日本の場合+09:00
	}
}
```

## Response

| Code | **Description** | **Reference** |
| :--- | :--- | :--- |
| 200 | 成功 | 成功 |
| 400 | Connection 失敗 |  |

#### Result\_msg

| Code | **Description** | **Reference** |
| :--- | :--- | :--- |
| 00 | 成功 | 成功 |
| -1 | 失敗 | 受信メッセージのBody情報が正しくない形のため、パスできませんでした。 |
| 11 | 失敗 | 必須値がないか、ステータス値が正しくありません。 |
| 94 | 失敗 | 認証キーが正しくありません。 |

## Response Body 例\)

```javascript
{
	"header":{
		"session_id": "session_id",
		"response_code": "1510A",
		"result_code": "00",
		"result_msg": "success",
		"version": "9.9.99"
	},
	"body":{
		"comp_id": "{会社ID}",
		"biz_id": "0",
		"memb_email": "{使用者 email}",
		"workflow_id": "{文書ID}",
		"command": "{実行されたコマンド}"
	}
}
```



