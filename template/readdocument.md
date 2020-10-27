# 書式リスト照会

* 書式リストを照会します。

## API URL

| Url | Type | **Code** |
| :--- | :--- | :--- |
| https://docs.esignon.net/JEDOC/Common.do?lang={value} | POST | 1123Q |

## Request

### Parameters

#### PathParameters

| **Parameter Name** | DataType | **Description** |
| :--- | :--- | :--- |
| lang | String | ko,en,jp |

####  Headers

| **Parameter Name**                         | DataType | **Description** |
| :--- | :--- | :--- |
| Content-Type | String | "application/json" |
| Authorization | String | "esignon AccessToken" |

####   Body 

  Body - Header Parameter

| **Parameter Name**                         | DataType | **Description** |
| :--- | :--- | :--- |
| request\_code | String | "1123Q" |
| request\_msg | String | "" |
| session\_id | String | "" |
| version | String | "9.9.99" |

  Body - Body Parameter

| **Parameter Name** | DataType | **Description** |
| :--- | :--- | :--- |
| comp\_id | String | 会社ID |
| memb\_email | Stirng | 使用者 email |
| biz\_id | String | "0" |
| search\_dir\_id | String | 書式を探すフォルダID "all"\(共有フォルダ\)、"my"\(自分のフォルダ\) |
| display\_order\_mode | String | ソート基準値Response file\_list フィールド値順に1~11 |

## Request Body 例\)

```javascript
{
        "header": {
                "request_code": "1123Q",
                "request_msg": "",
                "session_id": "",
                "version": "9.9.99"
        },
        "body": {
                 "comp_id": "{会社ID}",
                 "biz_id": "0",
                 "memb_email" : "{使用者 email}",
                 "search_dir_id": "all", // 書式を探すフォルダID "all"(共有フォルダ)、"my"(自分のフォルダ)
                 "display_order_mode": "1" // 1 ~ 11
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
| 99 | 失敗 | Unexpected exception（誤ったフォーマット） |

## Response Body 例\)

```javascript
{
	"body":{
		"comp_id": "{会社ID}",
		"biz_id": "0",
		"memb_email": "{使用者 email}",
		"search_dir_id": "all",
		"file_list":[{ 書式全体照会のため、すべての書式データを出力}]
	}
	"header":{
		"session_id": "session_id",
		"response_code": "1123A",
		"result_code": "00",
		"result_msg": "file list",
		"version": "9.9.99"
	}
}

```

#### Example\) file\_list

```javascript
{
	"file_id": "{書式ID}",
	"file_type": "書式",
	"file_name": "{書式名}",
	"dir_type": "{書式が位置するフォルダー}",
	"create_memb_email": "{書式作成者のEメールアドレス}",
	"create_date": "{書式生成日}",
	"create_memb_name": "{書式作成者名}",
	"file_workflow_count": "1", // 書式の段数
	"file_workflow_type": "WEBTYPE", // 対面、肥大なら(WEB TYPE)/大量(BULK)
	"file_workflow_library_id": "{書式のlibID}", //(大量発送に使用)
	"last_modify_date": "{最終修正日}"
}
```



