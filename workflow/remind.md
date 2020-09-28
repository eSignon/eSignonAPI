# Resend

* Resend the document.
* Completed or cancelled documents cannot be resent.

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
| request\_msg | String | Required | "Request to resend." |
| session\_id | String | Required | "" |

  Body - Body Parameter

| **Parameter Name** | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| comp\_id | String | Required | Company ID |
| biz\_id | String | Required | "0" |
| workflow\_id | String | Required | Current document ID \(wfuid\) |
| memb\_email | String | Required | user email |

## Request Body Example\)

```text
{
	"header": {
		"request_code": "1429Q",
		"request_msg": "Request to resend.",
		"session_id": ""},
	"body": {
		"comp_id": "{Company ID}",
		"biz_id": "0",
		"memb_email": "{user email}",
		"workflow_id": "{Current document ID (wfuid)}"
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
| 10 | fail | fail |
| 11 | fail | This document has been signed. |
| 12 | fail | This document has been cancelled. |
| 99 | fail | Unexpected exception \(incorrect format\) |

## Response Body Example\)

```text
{
	"header":{
		"session_id": "thread_023",
		"response_code": "1429A",
		"result_code": "00",
		"result_msg": "Remind succeeded."
	},
	"body":{
		"comp_id": "{Company ID}",
		"biz_id": "0",
		"memb_email": "{user email}",
		"workflow_id": "{Current document ID (wfuid)}"
	}
}

```

