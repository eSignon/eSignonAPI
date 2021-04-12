# 모든필드 값 조회

## 해당 API는 구버전입니다. 신규 API 인[ 문서 정보 조회 API](https://api.esignon.net/workflow/view/workflowinfo) 에 병합 됨

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
{% api-method-parameter name="Content-Type" type="string" required=true %}
application/json
{% endapi-method-parameter %}

{% api-method-parameter name="Authorization" type="string" required=true %}
esignon {token} / 값 입력시 띄어쓰기는 필수입니다.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="workflow\_id" type="string" required=true %}
문서 ID
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Response Body 예시\)
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
        "field_data":{
            "{필드명}": "{필드값}",
            "{필드명}": "{필드값}"......
        },
        "sender_email": "{문서 생성자 Email}",
        "start_date": "{문서 생성 시간}",
        "status": "{현재 문서의 상태}",
        "workflow_id": "{문서 ID}",
        "workflow_name": "{문서 제목}",
        "doc_uid": "{서식 ID}"
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
| status | Playing | 진행중 |
|  | Canceled | 취소 |
|  | Complete | 완료 |
|  | Disposal | 폐기 |
|  | Truncate | \(취소 상태 후 삭제한 경우\) |

