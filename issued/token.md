# 인증토큰 발급

{% api-method method="post" host="https://docs.esignon.net/api/:companyId/login" path=" " %}
{% api-method-summary %}
인증토큰 발급
{% endapi-method-summary %}

{% api-method-description %}
이싸인온 API 사용시 필요한 사용자의 인증토큰을 발급합니다.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="companyId" type="string" required=true %}
회사아이디
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="header" type="object" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="header.request\_code" type="string" required=true %}
1001Q
{% endapi-method-parameter %}

{% api-method-parameter name="body" type="object" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="body.memb\_email" type="string" required=true %}
사용자이메일
{% endapi-method-parameter %}

{% api-method-parameter name="body.memb\_pwd" type="string" required=true %}
사용자비밀번호
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
성공
{% endapi-method-response-example-description %}

```
{
  "header": {
    "response_code": "1001A",
    "result_code": "00",
    "result_msg": "성공적으로 로그인되었습니다.",
    "session_id": ""
  },
  "body": {
    "access_token": "{인증토큰}",
    "comp_id": "{회사아이디}",
    "device_id": "{디바이스아이디}",
    "expire_date": "{만료일}",
    "memb_email": "{사용자 이메일}"
  }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Request Body Example

```text
{
  "header": {
    "request_code": "1001Q",
  },
  "body": {
    "memb_email": "{사용자 이메일}",
    "memb_pwd": "{사용자 비밀번호}",
  }
}
```

## Response Body Example

```text
{
  "header": {
    "response_code": "1001A",
    "result_code": "00",
    "result_msg": "성공적으로 로그인되었습니다.",
    "session_id": ""
  },
  "body": {
    "access_token": "{인증토큰}",
    "comp_id": "{회사아이디}",
    "device_id": "{디바이스아이디}",
    "expire_date": "{만료일}",
    "memb_email": "{사용자 이메일}"
  }
}
```

## Response Body  header.result\_code

| Code | **Description** | **Reference** |
| :--- | :--- | :--- |
| 00 | 성공 | 성공 |
| 10 | 실패 | 로그인 정보가 정확하지 않습니다. |
| 12 | 실패 | 수신 메세지의 Body 정보가 잘못된 형태여서 파싱하지 못했습니다. |
| 95 | 실패 | API를 호출할 수 없는 회사입니다. 관리자에게 문의해주세요. |
| 99 | 실패 | Unexpected exception \( 잘못된 포맷 \) |

