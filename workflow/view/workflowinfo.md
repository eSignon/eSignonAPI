# 정보 조회

{% api-method method="get" host="https://docs.esignon.net" path="/api/v2/workflows/:workflowId" %}
{% api-method-summary %}
문서 정보 조회
{% endapi-method-summary %}

{% api-method-description %}
 문서 id를 통해 문서의 작성 이력, 필드 목록, 작성자 목록, 참조자 목록을 포함한 상세 정보를 조회합니다.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="workflowId" type="string" required=true %}
조회할 문서의 ID 
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
        "response_code": "/api/v2/workflows/:workflowId",
        "result_code": "00",
        "result_msg": "Success",
        "session_id": ""
    },
    "body":{
        "workflow_id": "{문서 id}",
        "workflow_name": "{문서명}",
        "workflow_status": "{문서 상태}",    
        "last_modify_date": "{마지막 작성일}",
        "expiry_date": "{문서 작성 기한}",
        "create_date": "{생성일}",
        "creator_email": "{생성자}",
        "creator_name": "{생성자 이메일}",
        "biz_id": "{부서 id}",
        "biz_name": "{부서명}",
        "action_history_list":[    // 작성 이력
            {
                "step_code": "{상태 코드}",
                "action_id": "{단계 id}",
                "confirm_date": "{작성일}",
                "name": "{작성자 이름}",
                "confirm_email": "{작성자 이메일}",
                "comment": "{메세지}",
            }
        ],
        "current_action_id": "{현재 작성 단계}",
        "total_action_count": "{문서 작성자 수}",
        "certificate_url": "{인증서 다운로드 url}",
        "download_url": "{문서 다운로드 url}",
        "view_url": "{문서 보기 url}",
        "referer_list":[    // 참조자 목록
            {
                "name": "{이름}",
                "type": "{참조 타입}",
                "email": "{이메일}",
            }
        ],
        "field_list":[    // 필드 목록
            {
                "action_id": "{단계 id}",
                "field_owner": "{필드명}",
                "field_value": "{입력값}",
                "email": "{이메일}",
            }
        ],
        "owner_list":[    // 생성자 목록
            {
                "action_id": "{단계 id}",
                "turn_yn": "{작성 차례 여부}",
                "name": "{이름}",
                "email": "{이메일}",
                "phone_number": "{핸드폰 번호}",
                "cert_mobile_yn": "{핸드폰 인증 여부}",
                "cert_password_yn": "{비밀번호 인증 여부}",
                "password_hint": "{비밀번호 힌트}",
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
| 10 | 실패 | 문서 정보 조회가 실패했습니다. id를 확인하세요. |

**body.workflow\_type**

| Value | Description |
| :--- | :--- |
| WEBTYPE | 비대면 |
| BULKTYPE | 대량발송 |
| FACEWEB | 대면 |

**body.workflow\_status**

| Value | Description |
| :--- | :--- |
| Complete | 완료 |
| Canceled | 취소 |
| Playing | 진행 중 |
| Truncate | 완전 삭제 |
| Disposal | 폐기 |

**body.action\_history\_list.step\_code**

| Value | Description |
| :--- | :--- |
| CERT\_DOWN | 이력 인증서 다운로드 |
| DELETED | 원본 PDF 삭제 |
| DISPOSAL | 폐기 |
| DOC\_DOWN | 문서 다운로드 |
| EXCEL\_EXPORT | 엑셀 다운로드 |
| MOBILE\_CERT | 휴대폰 인증 완료 |
| PASSWORD\_CERT | 비밀번호 인증 완료 |
| PUBLIC\_CERT | 공인인증 서명 완료 |
| RESEND | 문서 재전송 |
| SIGN\_COMPLETE | 서명 완료 |
| SIGN\_REQ | 서명 요청 |
| SIGN\_RETURN | 서명 반려 |
| SIGN\_START | 서명 시작 |
| TRUNCATE | 문서 삭제 |
| VIEW | 문서 보기 |
| WORKFLOW\_CANCEL | 문서 취소 |
| WORKFLOW\_COMPLETE | 문서 완료 |
| WORKFLOW\_REJECT | 문서 반려 |
| WORKFLOW\_START | 문서 시작 |

**body.referer\_list.type**

| Value | Description |
| :--- | :--- |
| starter | 생성자 |
| referer | 참조자 |

