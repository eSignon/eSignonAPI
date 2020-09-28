# Create Download URL

Create URL for downloading the document using the company ID and document ID.

 Can only access documents where users who retain the token values entered under Authorization can view. \(logged-in users\)

The created URL is valid for 5 minutes.

{% api-method method="post" host="https://docs.esignon.net" path="/workflow/download" %}
{% api-method-summary %}
workflow\_download
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
**esignon {token}**
{% endapi-method-parameter %}

{% api-method-parameter name="Content-Type" type="string" required=true %}
application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="workflow\_id" type="string" required=true %}
ID of completed document
{% endapi-method-parameter %}

{% api-method-parameter name="client\_id" type="string" required=true %}
ID issued by esignon
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
	"header":{
		"response_code": "",
		"result_code": "00",
		"result_msg": "Success",
		"session_id": ""
	},
	"body":{
		"cert_url": "{History Certificate Download URL}",
		"doc_url": "{Document Download URL}",
		"workflow_name": "{Completed Document Name}"
	}
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example\) Request Body

```text
{
  "client_id":"{ID issued by esignon}",
	"workflow_id": "{ID of completed document}"
}
```

Example\) Response Body / Error

```text
{
    "header":{
        "response_code": "",
        "result_code": "{Result code}",
        "result_msg": "{'Message by code'}",
        "session_id": ""
    },
    "body":{}
}
```

