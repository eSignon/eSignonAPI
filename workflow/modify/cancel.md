# Cancel, disposal

* Cancel or disposal the document
* Cancel - to cancel the document in playing.
* disposal- disposal completed documents.

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
| comp\_id | String | Required | Company ID |
| biz\_id | String | Required | "0" |
| memb\_email | String | Required | user email |
| workflow\_id | String | Required | Document ID |
| command | String | Required | "cancel" or  "disposal"  |
| description | String | Optional | Required value for "disposal" - "Reasons for disposal" |
| timezone\_offset | String | Optional | Required value for "disposal" - "Enter UTC time value"/"+00:00" |

## Request Body Example\)

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
			"comp_id": "{Company ID}",
      "biz_id":"0",
      "memb_email":"{user email}",
      "workflow_id":"{Document ID}",
      "command":"{ CANCEL or DISPOSAL }",
      "description":"{Enter a reason for disposal}", // 
      "timezone_offset":"+00:00" // +04:00 for Washington DC
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
| 00 | success | success |
| 94 | fail | The authentication key is incorrect. |
| 11 | fail | Required values do not exist or status values are incorrect. |
| -1 | fail | Parsing failed because the body information of the received message is incorrect. |

## Response Body Example\)

```text
{
	"header":{
		"session_id": "session_id",
		"response_code": "1510A",
		"result_code": "00",
		"result_msg": "success",
		"version": "9.9.99"
	},
	"body":{
		"comp_id": "{Company ID}",
		"biz_id": "0",
		"memb_email": "{user email}",
		"workflow_id": "{Document ID}",
		"command": "{executed command}"
	}
}
```



