# Approval, Rejection

* Approve or Rejection the document.
* Required values must be entered on the document upon approval.

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
| comp\_id | String | Required | Company ID |
| biz\_id | String | Required | "0" |
| client\_id | String | Required | ID issued by esignon \([question](https://esignon.net/en/customer/) for issue\) |
| memb\_email | String | Required | Email of the signer |
| action\_id | String | Required | Process step of current document |
| workflow\_id | String | Required | Document ID |
| comment | String | Required | Message to deliver upon approval or rejection |
| command | String | Required | RT - Rejection / CF - Approval / For CF, it is possible to proceed only if required values are already entered in the document |

## Request Body Example\)

```javascript
{
 "header" : {
   "request_code" : "5010Q",            
   "api_name" : "start api",    
   "session_id" : "",    
   "version" : "9.9.99"
 },
 "body" : {
   "comp_id": "{Company ID}",
   "client_id":"{ID issued by esignon}",
   "biz_id":"0",
   "memb_email":"{Email of the signer}",
   "action_id":"1" // Process step of current document
   "workflow_id":"{Document ID}",
   "comment":"{Message to deliver upon approval or rejection}",
   "command":"{RT or CF}" // CF=Approval, RT=Rejection
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
| 12 | fail | Parsing failed because the body information of the received message is incorrect. |
| 99 | fail | We can't proceed because there are required items left. |
| 99 | fail | Unexpected exception \(incorrect format\) |

## Response Body Example\)

```text
{
	"header":{
		"response_code": "5010A",
		"result_code": "00",
		"result_msg": "success.",
		"version": "9.9.99"
	},
	"body":{
		"comp_id": "{Company ID}"
	}
}
```

