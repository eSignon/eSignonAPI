# Search Template Info

* Search list of template.

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
| comp\_id | String | Company ID |
| memb\_email | Stirng | user email |
| biz\_id | String | "0" |
| search\_dir\_id | String | ID of the folder from which templates to be found / "all" \(shared folder\), "my" \(my folder\) |
| display\_order\_mode | String | 1 through 11 in the order of Response file\_list field values of the sorting criteria value |

## Request Body Example\)

```text
{
        "header": {
                "request_code": "1123Q",
                "request_msg": "",
                "session_id": "",
                "version": "9.9.99"
        },
        "body": {
                 "comp_id": "{Company ID}",
                 "biz_id": "0",
                 "memb_email" : "{user email}",
                 "search_dir_id": "all", // all (shared folder) , my (my folder)
                 "display_order_mode": "1" // 1 ~ 11
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
| 99 | fail | Unexpected exception \(incorrect format\) |
| 12 | fail | Parsing failed because the body information of the received message is incorrect. |

## Response Body Example\)

```text
{
	"body":{
		"comp_id": "{Company ID}",
		"biz_id": "0",
		"memb_email": "{user email}",
		"search_dir_id": "all",
		"file_list":[{ Displays all template data as it is a full search of the templates}]
	},
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

```text
{
	"file_id": "{Template ID}",
	"file_type": "templete",
	"file_name": "{Template name}",
	"dir_type": "{Folder in which template are located}",
	"create_memb_email": "{Email of the creator of the template}",
	"create_date": "{Template creation date}",
	"create_memb_name": "{Name of the creator of the template}",
	"file_workflow_count": "1", // Number of steps in the template
	"file_workflow_type": "WEBTYPE", // Face-to-face and email sending (WEBTYPE) bulk sending (BULK)
	"file_workflow_library_id": "{lib ID of the Template}", //(used for bulk sending)
	"last_modify_date": "{Last modified date}"
}
```



