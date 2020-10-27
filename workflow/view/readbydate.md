# 期間で照会

* 特定の書式に作成した文書を期間で照会します。

## API URL

| Url | Type | **Code** |
| :--- | :--- | :--- |
| https://docs.esignon.net/api/{CompID}/search | POST | 5009Q |

## Request

### Parameters

#### PathParameters

| **Parameter Name** | DataType | **Description** |
| :--- | :--- | :--- |
| CompID | String | 会社ID |

####  Headers

| **Parameter Name**                         | DataType | **Description** |
| :--- | :--- | :--- |
| Content-Type | String | "application/json" |
| Authorization | String | "esignon {accesstoken}" |

####   Body 

  Body - Header Parameter

| **Parameter Name**                         | DataType | **Description** |
| :--- | :--- | :--- |
| request\_code | String | "5009Q" |
| api\_name | String | "start api" |
| session\_id | String | "" |
| version | String | "1.1.60" |

  Body - Body Parameter

| **Parameter Name** | DataType | **Description** |
| :--- | :--- | :--- |
| comp\_id | String | 会社ID |
| doc\_uid | Stirng | 照会する文書の書式ID |
| client\_id | String |  esignonから発行されたID\(発行は[お問い合わせ](https://esignon.net/jp/customer/)\) |
| search\_date\_type | String | START or END START – 文書開始基準 END – 文書完了基準 |
| start\_date | String | 検索スタート地点 YYYY-MM-DD |
| end\_date | String | 検索終了地点 YYYY-MM-DD |
| field\_list | Data | 照会する文書情報 |
| field\_list.doc\_uid | String | 照会する文書の書式ID |
| field\_list.field\_name | String | 照会する文書書式のフィールド名 |

## Request Body 例\)

```javascript
{
 "header" : {
   "request_code" : "5009Q",
   "api_name" : "start api",
   "session_id" : "",
   "version" : "1.1.60"
 },
   "body" : {
     "comp_id": "{会社ID}",
     "doc_uid": "{照会する文書の書式ID}",
     "client_id": "{esignonから発行されたID}",
     "search_date_type":"{START or END}",
     "start_date": "{YYYY-MM-DD}",
     "end_date": "{YYYY-MM-DD}",
     "field_list": [{
  				"doc_uid": "{照会する文書の書式ID}",
  				"field_name": "{照会する文書書式のフィールド名}"
  			}]
 }
}
```

## Response

| Code | **Description** | **Reference** |
| :--- | :--- | :--- |
| 200 | success | success |
| 400 | Connection failed |  |

#### Result\_msg

| Code | **Description** | **Reference** |
| :--- | :--- | :--- |
| 00 | 成功 | 成功 |
| 10 | 失敗 | 失敗 |
| 12 | 失敗 | 受信メッセージのBody情報が正しくない形のため、パスできませんでした。 |
| 17 | 失敗 | 必須検索条件がありません。 |
| 18 | 失敗 | 検索条件がありません。 |
| 19 | 失敗 | 日付形式が間違っています。 |
| 99 | 失敗 | Unexpected exception（誤ったフォーマット） |

## Response Body 例\)

```javascript
{
	"header":{
		"response_code": "5009A",
		"result_code": "00",
		"result_msg": "Field status has been searched.",
		"session_id": "",
		"version": "1.1.60"
	},
	"body":{
		"comp_id": "{会社ID}",
		"wf_list":[
				{
					"doc_uid": "{書式ID}",
					"end_date": "{署名完了時間}",
					"total_process_count": "1", // 生息段階
					"wf_manager_name": "{ 文書作成者名 }",
					"wf_manager_email": "{ 文書作成者Eメールアドレス }",
					"wf_status": "Complete", // 文書状態 Complete–完了、Playing–進行中
					"field_value": "{照会したフィールド値}",
					"wfuid": "{文書ID}",
					"current_process_no": "1",
					"wf_title": "{Document Name}",
					"start_date": "{文書名}",
					"field_name": "{文書の開始時間}"
				}
		]
	}
}
```

