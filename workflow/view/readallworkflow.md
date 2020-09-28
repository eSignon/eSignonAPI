# Search all documents

* Search all your company's documents list.
* Enter only token values issued to HEADERS using GET-based APIs.

{% api-method method="get" host="https://docs.esignon.net/" path="worklists/new?page={value}&rows={value}" %}
{% api-method-summary %}
Search all documents
{% endapi-method-summary %}

{% api-method-description %}
You can check the status, type, level, etc. of the progress document.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="rows" type="string" required=true %}
How many to search per page / Default 50
{% endapi-method-parameter %}

{% api-method-parameter name="page" type="string" required=true %}
The list on which page to be searched / Default 1
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
esignon {accesstoken} 
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
	"header":{
		"response_code": "/worklists/new",
		"result_code": "00",
		"result_msg": "",
		"session_id": ""
	},
	"body":{
		"comp_id": "{Company ID}",
		"isManager": true,
		"memb_email": "{Logged-in email}",
		"page": "{Number of the page to be displayed}",
		"rows": "{Number of lists to be shown per page}",
		"total": "{Total Documents}",
		"workflow_list":[{
			"wfuid": {Documents ID},
			"wfname": "{Documents Title}",
			"wftype": "{Documents Type}",
			"status": "{Documents Status}",
			"step": "{Documents Step}",
			"nickname": "{Document starter's name}",
			"currentactionid": {Process step number of document},
			"email": "{Document starter's email}",
			"startdate": "{Document Start Time}",
			"totalprocesscount": {Total number of steps in the document},
			"currentprocesscount": {Completion Process Step Number},
			"confirmdate": "{Document finished time}",
			"preactionid": {},
			"preactionemail":{Referer Email}
			}]
	}
}

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Parameter Info

| **Name**                         | **Value**                                                 | **Description** |
| :--- | :--- | :--- |
| Workflow\_list.status | Playing | Playing |
|  | Canceled | Canceled |
|  | Complete | Complete |
|  | Truncate | Truncate |
| Workflow\_list.wftype | NORMAL | Email sending document |
|  | BULKWEB | Bulk sending document |
| Workflow\_list.step | Myturn | Myturn |
|  | Progress | in Progress |
|  | Complete | Complete |

