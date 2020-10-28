# 特定フィールド値で照会

* 特定のフィールド値で照会します。
* 例\) A書式中、Nameフィールド値が"誰か"の文書のみ照会

## API URL

| Url | Type | **Code** |
| :--- | :--- | :--- |
| https://docs.esignon.net/api/{CompID}/search | POST | 5008Q |

## Request

### Parameters

#### PathParameters

| **Parameter Name** | DataType | **Description** |
| :--- | :--- | :--- |
| CompID | String | 会社ID |

####  Headers

| **Parameter Name**                         | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| Content-Type | String | Required | application/json |
| Authorization | String | Required | esignon {token} |

####   Body 

  Body - Header Parameter

| **Parameter Name**                         | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| request\_code | String | Required | 5008Q |
| api\_name | String | Required | start api |
| session\_id | String | Required | "" |
| version | String | Required | 1.1.60 |

  Body - Body Parameter

| **Parameter Name** | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| comp\_id | String | Required | 会社ID |
| client\_id | String | Required |  esignonから発行されたID\(発行は[お問い合わせ](https://esignon.net/jp/customer/)\) |
| field\_list | Data | Required | 照会する文書情報 |
| field\_list.doc\_uid | String | Required | 照会する文書の書式ID |
| field\_list.field\_name | String | Optional | 照会する文書書式のフィールド名 |
| field\_list.field\_value | String | Optional | 照会する文書書式のフィールド値 |

## Request Body 例

```javascript
{
	 "header" : {
	   "request_code" : "5008Q",            
	   "api_name" : "start api",    
	   "session_id" : "",    
	   "version" : "1.1.60"
	 },
	 "body" : {
	   "comp_id": "{ 会社ID }",
	   "client_id":"{ esignonから発行されたID }",
	   "field_list": [ 
			    {
						"doc_uid": "{照会する文書の書式ID}",
						"field_name": "{照会する文書書式のフィールド名}",
						"field_value": "{照会する文書書式のフィールド値}"
			    }
	   ]
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
| 17 | 失敗 | 必須検索条件がありません。 |
| 18 | 失敗 | 検索条件がありません。 |
| 19 | 失敗 | 日付形式が間違っています。 |
| 99 | 失敗 | Unexpected exception（誤ったフォーマット） |

## Response Body 例

```javascript
{
	"header":{
		"response_code": "5008A",
		"result_code": "00",
		"result_msg": "フィールドステータスが検索されました。",
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
				"wf_status": "Complete", // 文書性態 Complete–完了、Playing–進行中
				"field_value": "{照会したフィールド値}",
				"wfuid": "{文書ID}",
				"current_process_no": "1",
				"wf_title": "{文書名}",
				"start_date": "{文書の開始時間}",
				"field_name": "{照会したフィールド名}"
			}
		]
	}
}

```

