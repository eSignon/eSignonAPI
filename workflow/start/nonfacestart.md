# Start email sending

* Begin the email sending template
* The export\_api value can be set separately to designate the format of the value to be received. \(optional\)
* export\_api is the feature that requests for a set value in esignon by a set URL when a customer approves or rejects in the process.
* ※ If the array-type parameter is optional, required values among the parameter values in the array must be entered during use. They do not need to be entered when it is not used.
* ※ The default value of the language parameter is "ko-KR" \(Default settings\)

## API URL Info

| Url | Type | **Code** |
| :--- | :--- | :--- |
| https://docs.esignon.net/api/{CompID}/startsimple | POST | 5005Q |

## Request

### Parameters

#### PathParameters

| **Parameter Name** | DataType | **Description** |
| :--- | :--- | :--- |
| CompID | String | Company ID |

####  Headers

| **Parameter Name**                         | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| Content-Type | String | Required | "application/json" |
| Authorization | String | Required | "esignon {token}" |

####   Body 

  Body - Header Parameter

| **Parameter Name**                         | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| request\_code | String | Required | "5005Q" |
| version | String | Required | "9.9.99" |

  Body - Body Parameter

| **Parameter Name** | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| biz\_id | String | Required | "0" |
| workflow\_name | String | Required | Title of the document to start |
| doc\_id | String | Required | templateID to start |
| memb\_email | String | Required | Email of document starter |
| language | String | Optional | "ko-KR", "en-US", "ja-JP" |
| comment | String | Optional | Delivered message |
| player\_list | Array | Required | The information of the signer be filled out according to the steps of the template step |
| player\_list.field\_owner | String | Required | Start from "1" in the order of signing |
| player\_list.email | String | Required | Email |
| player\_list.name | String | Required | Name of the signer |
| player\_list.password\_hint | String | Optional | Password hint |
| player\_list.password | String | Optional | Password |
| field\_list | Array | Optional | If there are values to be entered in advance, only the values of RadioBox, CheckBox, LabelBox and TextBox may be entered in advance |
| field\_list.field\_name | String | Optional | Templete Field Name |
| field\_list.field\_value | String | Optional | For the form field values of Radio and Check Box, the values are received as \(“N” or ”Y”\); for Label and Text Box, the text values are received as they are |
| export\_api\_info | Array | Optional | The value set when exporting the written data |
| export\_api\_info.api\_type | String | Required | "StartAndEnd" \(only start and end\) or "ALL" \(all\) |
| export\_api\_info.url | String | Required | URL to receive data from |
| export\_api\_info.request\_code | String | Required | The arbitrary value defined by the customer |
| export\_api\_info.clientid | String | Optional | ID issued by esignon \([question ](https://esignon.net/en/customer/)for issue\) |
| export\_api\_info.authorization | String | Optional | The value you want to set to header authorization when receiving data |
| export\_api\_info.request\_params | Array | Optional | Use when you want to get a specific value inside a document. |
| export\_api\_info.request\_params.param\_id | String | Required | Name of the parameter to be received \(user-specified\) |
| export\_api\_info.request\_params.param\_value | String | Required | Default value to be received in case the value to be received from Params.fields does not exist in the document |
| export\_api\_info.request\_params.fields | Array | Required | The value entered instead of param\_value if the value corresponding to the field name exists in the document by querying the field name inside the template. |
| export\_api\_info.request\_params.fields.doc\_id | String | Required | templateID |
| export\_api\_info.request\_params.fields.field\_name | String | Required | template field name  |
| customer\_list | Array | Optional | Add if there are additional referers |
| customer\_list.email | String | Required | Email address |
| customer\_list.name | String | Required | Referer Name |
| customer\_list.language | String | Optional | ko-KR, en-US, ja-JP |

## Request Body Example

```javascript
{
	"header": {
		"request_code": "5005Q",
		"version": "9.9.99"
	},
	"body": {
		"biz_id": "0",
		"workflow_name": "{ Title of the document to start }",
		"memb_email":"{ Email of document starter }",
		"doc_id": "{Templete ID}",
		"language": "ko-KR",
		"comment": "",
		"player_list": [{
			"field_owner": "1",//(step)
			"email": "{ Email }",
      "name":"{ Signer name }",
			"language": "{ ko-KR }",
      "password_hint":"{ Password to use when proceeding with the contract hint }",
      "password":"{Password to use when proceeding with the contract}"
		},{
			"field_owner": "2",
			"email": "{}",
      "name":"{}",
			"language": "{}",
      "password_hint":"{}",
      "password":"{}"
		}],
		"field_list": [{
				"field_name": "{ field_name }",
				"field_value": "{ field_value }"
			}
		],
		"customer_list": [{ // Referer list
				"email": "{ Email }",
	      "name":"{ Referer Name }",
				"language": "{ko-KR}"
		}],
		"export_api_info": {
				"api_type": "{ StartAndEnd or ALL }",
				"url": "{ URL to receive data from }",
				"request_code": "{ Return The Value You Want to Receive or "embed"( See ExportAPI Description) }",
				"clientid": "{ Issued UniqueID }",
				"authorization":"{The value you want to set to header authorization when receiving data }",
	      "request_params": [{
								"param_id": "{Name of parameter to receive (custom)}",
								"param_value": "{Default value to be obtained if the value to be obtained from Params.fields is not in the document}",
								"fields": [{ // The value entered instead of param_value if the value corresponding to the field name exists in the document by querying the field name inside the format.
														 //	  filed_name not exist - param_id:param_value return  
														 //	  filed_name exist - param_id:field_value return
                            "doc_id":"{ templateID }",
                            "field_name":"{ template field name }" 
          			}]
				}]
	   }
	}
}
```

## Request Body Example - only Required

```javascript
{
	"header": {
		"request_code": "5005Q",
		"version": "9.9.99"
	},
	"body": {
		"biz_id": "0",
		"workflow_name": "{ Title of the document to start }",
		"memb_email":"{ Email of document starter }",
		"doc_id": "{Templete ID}",
		"language": "ko-KR",
		"player_list": [{
			"field_owner": "1",
			"email": "{ Email }",
			"name": "{ Signer name }"
		}, {
			"field_owner": "2",
			"email": "{}",
			"name": "{}"
		}]
	}
}
```

## Request Body Example - For TEST Account

```javascript
{
	"header": {
		"request_code": "5005Q",
		"version": "9.9.99"
	},
	"body": {
		"comp_id": "testapi",
		"biz_id": "0",
		"memb_email": "guide@esignon.net",
		"language": "ko-KR",
		"comment": "",
		"workflow_name": "TEST-NAME",
		"doc_id": "1",
		"player_list": [{
				"field_owner": "1",
				"email": "guide@esignon.net",
				"name": "TEST",
				"language": "ko-KR"
			},
			{
				"field_owner": "2",
				"email": "guide@esignon.net",
				"name": "TEST",
				"language": "ko-KR"
			}
		],
		"field_list": [{
			"doc_id": "1",
			"field_name": "name",
			"field_value": "name-value"
		}],
		"customer_list": [{
			"email": "guide@esignon.net",
			"name": "TEST",
			"language": "ko-KR"
		}]
	}
}
```

## Response

| Code | **Description** | **Reference** |
| :--- | :--- | :--- |
| 200 | success |  |
| 400 | Connection failed |  |

#### Result\_msg

| Code | **Description** | **Reference** |
| :--- | :--- | :--- |
| 00 | success | success |
| 10 | fail | fail |
| 99 | fail | Unexpected exception \(incorrect format\) |
| 12 | fail | Parsing failed because the body information of the received message is incorrect. |

## Response Body Example

```javascript
{ 
 "header":{
   "session_id": "S1001", 
   "response_code": "5005A",
   "result_code": "00", 
   "result_msg": "Work Flow Start", 
   "version": "9.9.99" }, 
 "body":{ 
   "comp_id": "{ Company ID }", 
   "biz_id": "0", 
   "memb_email": "{ Document starter name }", 
   "workflow_id": "{ Document ID }", 
   "workflow_name": "{ Title of the document that started }", 
   "token": "{ Token value used to access the creation page if the person who initiated the document is the first author of the contract }", 
   // https://docs.esignon.net/mail/sign?token=
   // Enter the token value issued to the above address to access the signature page
   "lang": "ko-KR" }
}
```

## Response export\_api Example

```javascript
{
	"header": {
		"api_name": "export",
		"session_id": "S1001",
		"request_code": "{ Value set at request }",
		"authorization":"{ Value set at request }"
	},
	"body": {
		"clientid": "{ Unique ID for using eSignonAPI }",
		"processid": "1", //Separated value for the progress stage of the document
		"requestid": "{ Value of request_code of the header }",
		"actionid": "1", //Separated value for the progress stage of the document
		"workdatetime": "2020-01-31 04:23:28.0", //Document finished time
		"worktype": "CF", //CF=Approval, RT=Rejection (The document is cancelled when the contract initiator rejects.)
		"wfuid": "{}", //
		"useremail": "{ Signer email }", 
		"opinion": "", //Display when the signers use messages of rejection or transmission upon approval or rejection
		"param_id": "param_value", // fields_value is returned when the fields value is set
	}
}
```

