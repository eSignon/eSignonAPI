# 정보 조회

{% api-method method="get" host="https://docs.esignon.net" path="/api/v2/company" %}
{% api-method-summary %}
회사 정보 조회 
{% endapi-method-summary %}

{% api-method-description %}
회사의 상세 정보를 조회합니다.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
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
        "response_code": "/api/v2/company",
        "result_code": "00",
        "result_msg": "Success",
        "session_id": ""
    },
    "body":{
        "name": "{회사명}",
        "contract_company_name": "{계약 진행용 회사명}",
        "create_email": "{생성자}",
        "country_code": "{국가 코드}",
        "workflow_capacity": "{충전 건수}",
        "workflow_usage": "{사용 건수}",
        "allow_list":[
            "{ip 주소}"
        ],
        "expiry_date": "{만료일}",
        "workflow_charge_list":[
            "grade_code": "{요금제 코드}",
            "email": "{결제자}",
            "payment_date_time": "{결제일}",
            "doc_capacity": "{충전 건수}",
            "payment_system": "{결제 시스템}",
            "payment_amount": "{결제 횟수}",
        ],
        "sign_up_type": "{구분}",
        "grade_code": "{요금제 코드}",
        "create_date": "{생성일}",
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
| 10 | 실패 | 회사 정보 조회가 실패했습니다. |

**body.grade\_code**

| Value | Description |
| :--- | :--- |
| BB | Beginner |
| BR | Rookie |
| BE | Expert |
| BP | Premier |
| PS | Personal |
| ST | Standard |
| BV | Business VIP |
| PP | PostPaid |
| R1 | MONTH 10 |
| R2 | MONTH 30 |
| R3 | MONTH 50 |
| R4 | MONTH 100 |
| R5 | MONTH 250 |
| R6 | MONTH 500 |
| R0 | MONTH 0 |
| RT | Rookie Test |

**body.sign\_up\_type**

| Value | Description |
| :--- | :--- |
| my | 개인 고객 |
| company | 기업 고객 |

