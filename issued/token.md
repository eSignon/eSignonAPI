# 認証トークン発行

{% api-method method="post" host="https://docs.esignon.net/api/:companyId/login" path=" " %}
{% api-method-summary %}
認証トークン発行
{% endapi-method-summary %}

{% api-method-description %}
esignon APIを使用する時に必要なユーザーの認証トークン\(accesstoken\)を発行します。
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="companyId" type="string" required=true %}
会社 ID
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
使用者 email
{% endapi-method-parameter %}

{% api-method-parameter name="body.memb\_pwd" type="string" required=true %}
使用者 password
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
성공
{% endapi-method-response-example-description %}

```javascript
{
  "header": {
    "response_code": "1001A",
    "result_code": "00",
    "result_msg": "成功裏にログインされました。",
    "session_id": ""
  },
  "body": {
    "access_token": "{accesstoken}",
    "comp_id": "{会社 ID}",
    "device_id": "{Device ID}",
    "expire_date": "{満了日}",
    "memb_email": "{使用者 email}"
  }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Request Body Example

```javascript
{
  "header": {
    "request_code": "1001Q",
  },
  "body": {
    "memb_email": "{使用者 email}",
    "memb_pwd": "{使用者 password}",
  }
}
```

## Response Body Example

```javascript
{
  "header": {
    "response_code": "1001A",
    "result_code": "00",
    "result_msg": "成功裏にログインされました。",
    "session_id": ""
  },
  "body": {
    "access_token": "{accesstoken}",
    "comp_id": "{会社 ID}",
    "device_id": "{Device ID}",
    "expire_date": "{満了日}",
    "memb_email": "{使用者 email}"
  }
}
```

## Response Body  header.result\_code

| Code | **Description** | **Reference** |
| :--- | :--- | :--- |
| 00 | 成功 | 成功 |
| 10 | 失敗 | ログイン情報が正確ではありません。 |
| 12 | 失敗 | 受信メッセージのBody情報が正しくない形のため、パスできませんでした。 |
| 95 | 失敗 | APIを呼び出せない会社です。 管理者にお問い合わせください。 |
| 99 | 失敗 | Unexpected exception（誤ったフォーマット） |

