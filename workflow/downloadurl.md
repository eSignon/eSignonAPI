# 다운로드 URL 생성

회사 ID 와 문서의 ID 를 통하여 문서를 다운로드 할 수 있는 URL 을 가져옵니다.

Authorization에 입력된 Token 값을 가진 유저가 볼 수 있는 문서만 접근 가능합니다.\(로그인한 유저\)

생성된 URL은 5분간 유지됩니다.

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
esignon ${발급받은토큰}  
 **/ 값 입력시 띄어쓰기는 필수입니다.**
{% endapi-method-parameter %}

{% api-method-parameter name="Content-Type" type="string" required=true %}
application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="workflow\_id" type="string" required=true %}
완료 된 문서의 ID 값 / wfuid
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
	"header":{
		"response_code": "",
		"result_code": "00",
		"result_msg": "Success",
		"session_id": ""
	},
	"body":{
		"cert_url": "{이력인증서 URL}",
		"doc_url": "{완료된 문서 URL}",
		"workflow_name": "{완료된 문서 이름}"
	}
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example\) Request Body

```javascript
{
	"workflow_id": "{완료 된 문서의 ID 값}"
}
```

Example\) Response Body / Error

```javascript
{
    "header":{
        "response_code": "",
        "result_code": "{결과코드}",
        "result_msg": "{'코드에 따른 메세지'}",
        "session_id": ""
    },
    "body":{}
}
```

