# Search with the specific field value.

* Search with the specific field value.
* Ex\) Among template A, search only the documents with the Name field value "Somebody”

## API URL

| Url | Type | **Code** |
| :--- | :--- | :--- |
| https://docs.esignon.net/api/{CompID}/search | POST | 5008Q |

## Request

### Parameters

#### PathParameters

| **Parameter Name** | DataType | **Description** |
| :--- | :--- | :--- |
| CompID | String | Company ID |

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
| comp\_id | String | Required | Company ID |
| client\_id | String | Required |  ID issued by esignon \([question](https://esignon.net/en/customer/) for issue\) |
| field\_list | Data | Required | Information of the document to search |
| field\_list.doc\_uid | String | Required | Templete ID of the document to search |
| field\_list.field\_name | String | Optional | Templete field name of the document to search |
| field\_list.field\_value | String | Optional | Templete field value  of the document to search |

## Request Body Example

```javascript
{
	 "header" : {
	   "request_code" : "5008Q",            
	   "api_name" : "start api",    
	   "session_id" : "",    
	   "version" : "1.1.60"
	 },
	 "body" : {
	   "comp_id": "{ Company ID }",
	   "client_id":"{ ID issued by esignon }",
	   "field_list": [ 
			    {
						"doc_uid": "{Templete ID  of the document to search}",
						"field_name": "{Templete field name of the document to search}",
						"field_value": "{Templete field value  of the document to search}"
			    }
	   ]
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
| 17 | fail | No required search conditions |
| 18 | fail | No search conditions |
| 19 | fail | Incorrect date format |
| 99 | fail | Unexpected exception \(incorrect format\) |

## Response Body Example

```javascript
{
	"header":{
		"response_code": "5008A",
		"result_code": "00",
		"result_msg": "Field status has been searched.",
		"session_id": "",
		"version": "1.1.60"
	},
	"body":{
		"comp_id": "{Company ID}",
		"wf_list":[
			{
				"doc_uid": "{Templete ID}",
				"end_date": "{Signature Completion Time}",
				"total_process_count": "1", // Total steps of template
				"wf_manager_name": "{ Document starter Name }",
				"wf_manager_email": "{ Document starter Email }",
				"wf_status": "Complete", // Document status Complete – Done, Playing – In progress
				"field_value": "{Searched field value}",
				"wfuid": "{Document ID}",
				"current_process_no": "1",
				"wf_title": "{Document Name}",
				"start_date": "{Document Start Time}",
				"field_name": "{Searched field name}"
			}
		]
	}
}

```

