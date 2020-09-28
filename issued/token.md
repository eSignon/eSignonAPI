# issue authentication token

{% api-method method="post" host="https://docs.esignon.net/api/:companyId/login" path=" " %}
{% api-method-summary %}
issue authentication token
{% endapi-method-summary %}

{% api-method-description %}
When using eSignon API, an authentication token is absolutely required. This API issues the required user's authentication token.\( accesstoken \)
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="companyId" type="string" required=true %}
Company ID
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
User email
{% endapi-method-parameter %}

{% api-method-parameter name="body.memb\_pwd" type="string" required=true %}
User password
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
    "result_msg": "You have successfully logged in.",
    "session_id": ""
  },
  "body": {
    "access_token": "{accesstoken}",
    "comp_id": "{Company ID}",
    "device_id": "{Device ID}",
    "expire_date": "{Expired}",
    "memb_email": "{User email}"
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
    "memb_email": "{User email}",
    "memb_pwd": "{User password}",
  }
}
```

## Response Body Example

```text
{
  "header": {
    "response_code": "1001A",
    "result_code": "00",
    "result_msg": "You have successfully logged in.",
    "session_id": ""
  },
  "body": {
    "access_token": "{accesstoken}",
    "comp_id": "{Company ID}",
    "device_id": "{Device ID}",
    "expire_date": "{Expired}",
    "memb_email": "{User email}"
  }
}
```

## Response Body  header.result\_code

| Code | **Description** | **Reference** |
| :--- | :--- | :--- |
| 00 | success | success |
| 10 | Fail | Your login information is incorrect. |
| 12 | Fail | Parsing failed because the body information of the received message is incorrect. |
| 95 | Fail | The company is unable to call the API. Please contact the customer center. |
| 99 | Fail | Unexpected exception \(incorrect format\) |

