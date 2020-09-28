# 承認、返戻

* 文書を承認または却下します。
* 承認時に文書は必須値が入力されている必要があります。

## API URL

| Url | Type | **Code** |
| :--- | :--- | :--- |
| https://docs.esignon.net/api/{CompID}/action | POST | 5010Q |

## Request

### Parameters

#### PathParameters

| **Parameter Name** | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| CompID | String | Required | Company ID |

####  Headers

| **Parameter Name**                         | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| Content-Type | String | Required | "application/json" |
| Authorization | String | Required | "esignon AccessToken" |

####   Body 

  Body - Header Parameter

| **Parameter Name**                         | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| request\_code | String | Required | "5010Q" |
| api\_name | String | Optional | "start api" |
| session\_id | String | Optional | "" |
| version | String | Required | "9.9.99" |

  Body - Body Parameter

| **Parameter Name** | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| comp\_id | String | Required | 会社ID |
| biz\_id | String | Required | "0" |
| client\_id | String | Required | esignonから発行されたID\(発行は[お問い合わせ](https://esignon.net/jp/customer/)\) |
| memb\_email | String | Required | 契約進行者Eメール |
| action\_id | String | Required | 契約進行中の段階 |
| workflow\_id | String | Required | 契約中の文書ID |
| comment | String | Required | 承認 or 返戻時に伝えるメッセージ |
| command | String | Required | RT - 返戻 CF - 承認 CF の際は、文書に必須値を入力した状態 必須項目が残っているため進行できません。 |

## Request Body 例\)

```text
{
 "header" : {
   "request_code" : "5010Q",            
   "api_name" : "start api",    
   "session_id" : "",    
   "version" : "9.9.99"
 },
 "body" : {
   "comp_id": "{会社ID}",
   "client_id":"{esignonから発行されたID}",
   "biz_id":"0",
   "memb_email":"{契約進行者Eメール}",
   "action_id":"1" // 契約進行中の段階
   "workflow_id":"{契約中の文書ID}",
   "comment":"{承認 or 返戻時に伝えるメッセージ}",
   "command":"{RT or CF}" // RT - 返戻 CF - 承認
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
| 10 | 失敗 | 失敗 |
| 12 | 失敗 | 受信メッセージのBody情報が正しくない形のため、パスできませんでした。 |
| 99 | 失敗 | 必須項目が残っているため進行できません。 |
| 99 | 失敗 | Unexpected exception（誤ったフォーマット） |

## Response Body 例\)

```text
{
	"header":{
		"response_code": "5010A",
		"result_code": "00",
		"result_msg": "success.",
		"version": "9.9.99"
	},
	"body":{
		"comp_id": "{会社ID}"
	}
}
```

