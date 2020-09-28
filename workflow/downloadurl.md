# ダウンロードURL作成

会社 ID と文書の ID を通じて文書をダウンロードできる URL を取得します。

Authorizationに入力されたToken値を持つユーザーが閲覧できる文書のみアクセス可能です。（ログインしたユーザー）

作成されたURLは5分間維持されます。

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
完了した文書のID
{% endapi-method-parameter %}

{% api-method-parameter name="client\_id" type="string" required=true %}
esignonから発行されたID
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
		"cert_url": "{履歴認証書URL}",
		"doc_url": "{完了した文書URL}",
		"workflow_name": "{完了した文書名}"
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
  "client_id":"{esignonから発行されたID}",
	"workflow_id": "{完了した文書のID}"
}
```

Example\) Response Body / Error

```text
{
    "header":{
        "response_code": "",
        "result_code": "{応答コード}",
        "result_msg": "{コードに沿ったメッセージ}",
        "session_id": ""
    },
    "body":{}
}
```

