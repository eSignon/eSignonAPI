# Search by period

* Search for documents created by specific template and period

## API URL

| Url | Type | **Code** |
| :--- | :--- | :--- |
| https://docs.esignon.net/api/{CompID}/search | POST | 5009Q |

## Request

### Parameters

#### PathParameters

| **Parameter Name** | DataType | **Description** |
| :--- | :--- | :--- |
| CompID | String | Company ID |

####  Headers

| **Parameter Name**                         | DataType | **Description** |
| :--- | :--- | :--- |
| Content-Type | String | "application/json" |
| Authorization | String | "esignon accesstoken" |

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
| comp\_id | String | Company ID |
| doc\_uid | Stirng | Templete ID of the document to search |
| client\_id | String |  ID issued by esignon \([question](https://esignon.net/en/customer/) for issue\) |
| search\_date\_type | String | START or END / START – based on the start of the document  / END – based on the end of the document |
| start\_date | String | Search Start Point YYYY-MM-DD |
| end\_date | String | Search End Point YYYY-MM-DD |
| field\_list | Data | Information of the document to search |
| field\_list.doc\_uid | String | Templete ID of the document to search |
| field\_list.field\_name | String | Templete field name of the document to search |

## Request Body Example\)

```javascript
{
 "header" : {
   "request_code" : "5009Q",
   "api_name" : "start api",
   "session_id" : "",
   "version" : "1.1.60"
 },
   "body" : {
     "comp_id": "{Company ID}",
     "doc_uid": "{Templete ID of the document to search}",
     "client_id": "{ID issued by esignon}",
     "search_date_type":"{START or END}",
     "start_date": "{YYYY-MM-DD}",
     "end_date": "{YYYY-MM-DD}",
     "field_list": [{
  				"doc_uid": "{Templete ID of the document to search}",
  				"field_name": "{Templete field name of the document to search}"
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
| 00 | success | success |
| 10 | fail | fail |
| 12 | fail | Parsing failed because the body information of the received message is incorrect. |
| 17 | fail | No required search conditions |
| 18 | fail | No search conditions |
| 19 | fail | Incorrect date format |
| 99 | fail | Unexpected exception \(incorrect format\) |

## Response Body Example\)

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

