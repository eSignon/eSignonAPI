# 再送信

* 文書を再送信します。
* 完了、キャンセルされた文書は、再送信できません。

## API URL

| Url | Type | **Code** |
| :--- | :--- | :--- |
| https://docs.esignon.net/JEDOC/Common.do?lang={} | POST | 1429Q |

## Request

### Parameters

#### PathParameters

| **Parameter Name** | DataType | **Description** |
| :--- | :--- | :--- |
| lang | String | ko,en,jp |

####  Headers

| **Parameter Name**                         | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| Content-Type | String | Required | "application/json" |
| Authorization | String | Required | "esignon AccessToken" |

####   Body 

  Body - Header Parameter

| **Parameter Name**                         | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| request\_code | String | Required | "1429Q" |
| request\_msg | String | Required | "再送信要請" |
| session\_id | String | Required | "" |

  Body - Body Parameter

| **Parameter Name** | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| comp\_id | String | Required | 会社ID |
| biz\_id | String | Required | "0" |
| workflow\_id | String | Required | 進行文書ID \(wfuid\) |
| memb\_email | String | Required | 使用者 email |

## Request Body 例\)

```javascript
{
	"header": {
		"request_code": "1429Q",
		"request_msg": "再送信要請",
		"session_id": ""},
	"body": {
		"comp_id": "{会社ID}",
		"biz_id": "0",
		"memb_email": "{使用者 email}",
		"workflow_id": "{進行文書ID (wfuid)}"
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
| 11 | 失敗 | 署名が完了した文書です。 |
| 12 | 失敗 | キャンセル処理された文書です。 |
| 99 | 失敗 | Unexpected exception（誤ったフォーマット） |

## Response Body 例\)

```javascript
{
	"header":{
		"session_id": "thread_023",
		"response_code": "1429A",
		"result_code": "00",
		"result_msg": "Remind succeeded."
	},
	"body":{
		"comp_id": "{会社ID}",
		"biz_id": "0",
		"memb_email": "{使用者 email}",
		"workflow_id": "{進行文書ID (wfuid)}"
	}
}

```

