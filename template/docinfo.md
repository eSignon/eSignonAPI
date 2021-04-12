# 정보 조회

{% api-method method="get" host="https://docs.esignon.net" path="/api/v2/docs/:documentId" %}
{% api-method-summary %}
서식 정보 조회 
{% endapi-method-summary %}

{% api-method-description %}
서식 id를 통해 서식의 상세 정보를 조회합니다. 
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="documentId" type="string" required=true %}
조회할 서식의 id 
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authentication" type="string" required=true %}
esignon ${인증토큰}
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="offset" type="string" %}
UTC offset  
±hh:mm 형식으로 입력 \(기본값 +09:00\)
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
조회 성공
{% endapi-method-response-example-description %}

```
{
    "header":{
        "response_code": "/api/v2/docs/:documentId",
        "result_code": "00",
        "result_msg": "Success",
        "session_id": ""
    },
    "body":{
        "doc_id": "{서식 id}",
        "doc_name": "{서식명}",
        "doc_type": "{서식 종류}",
        "creator": "{생성자}",
        "workflow_library_id": "{라이브러리 id}",
        "dir_type": "{폴더 종류}",
        "dir_path": "{폴더 위치}",
        "last_modifier": "{마지막 수정자}",
        "file_workflow_count": "{문서 작성자 수}",
        "last_modify_date": "{마지막 수정일}",
        "create_date": "{생성일}",
        "field_list":[    // 필드 목록
            {
                "action_id": "{단계 id}",
                "field_owner": "{필드명}",
                "email": "{이메일}",
            }
        ]
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Response

### **Status code**

| Code | Description | Reference |
| :--- | :--- | :--- |
| 200 | 성공 | 형식이 잘못된 경우 header.result\_msg 참조 |
| 400 | 연결 실패 |  |

### Body

**header.result\_code**

| Code | Description | Reference |
| :--- | :--- | :--- |
| 00 | 성공 | 성공 |
| 10 | 실패 | 완성되지 않은 서식입니다. |
| 11 | 실패 | 문서 정보 조회가 실패했습니다. id를 확인하세요. |

**body.doc\_type**

| Value | Description |
| :--- | :--- |
| WEBTYPE | 비대면 |
| BULKTYPE | 대량발송 |
| FACEWEB | 대면 |

**body.dir\_type**

| Value | Description |
| :--- | :--- |
| shared | 공유된 폴더 |
| biz | 부서폴더 |
| my | 내폴더 |

