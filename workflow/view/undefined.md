# 모든필드 값 조회

* 문서 ID를 받아 해당 문서 내 모든 필드값을 조회합니다.

{% api-method method="post" host="https://docs.esignon.net" path="/exportfield" %}
{% api-method-summary %}
Export field
{% endapi-method-summary %}

{% api-method-description %}
문서 내 모든 필드값을 조회합니다.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
esignon {token} / 값 입력시 띄어쓰기는 필수입니다.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="workflow\_id" type="string" %}
문서 ID
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Response Body 예시\)
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
        "field_data":{
            "{필드명}": "{필드값}",
            "{필드명}": "{필드값}"......
        },
        "sender_email": "{문서 생성자 Email}",
        "start_date": "{문서 생성 시간}",
        "status": "{현재 문서의 상태}",
        "workflow_id": "{문서 ID}",
        "workflow_name": "{문서 제목}"
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

