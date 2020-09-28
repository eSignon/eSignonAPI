# 進行文書リスト照会

* 該当会社の進行文書リストをすべて照会します。
* GET方式のAPIでHEADERSに発行されたトークン値だけを入力して照会します。

{% api-method method="get" host="https://docs.esignon.net/" path="worklists/new?page={value}&rows={value}" %}
{% api-method-summary %}
進行文書リスト照会
{% endapi-method-summary %}

{% api-method-description %}
進行文書の状態、種類、段階などを確認することができます。
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="rows" type="string" required=true %}
1ページあたり照会する文書数 / Default 50
{% endapi-method-parameter %}

{% api-method-parameter name="page" type="string" required=true %}
照会するページの番号 / Default 1
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
esignon {accesstoken} 
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
	"header":{
		"response_code": "/worklists/new",
		"result_code": "00",
		"result_msg": "",
		"session_id": ""
	},
	"body":{
		"comp_id": "{会社ID}",
		"isManager": true,
		"memb_email": "{ログインしたEメール}",
		"page": "{出力するページの番号}",
		"rows": "{ページあたりの表示リストの数}",
		"total": "{全文書数}",
		"workflow_list":[{
			"wfuid": {文書ID},
			"wfname": "{文書のタイトル}",
			"wftype": "{文書タイプ}",
			"status": "{文書状態}",
			"step": "{文書段階}",
			"nickname": "{文書作成者}",
			"currentactionid": {契約中の段階番号},
			"email": "{文書作成者Eメール}",
			"startdate": "{文書開始日}",
			"totalprocesscount": {文書の総工数},
			"currentprocesscount": {完了した契約段階番号},
			"confirmdate": "{文書完了日}",
			"preactionid": {},
			"preactionemail":{参照のEメール}
			}]
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
| Workflow\_list.status | Playing | 進行中 |
|  | Canceled | キャンセル |
|  | Complete | 完了 |
|  | Truncate | 廃棄 |
| Workflow\_list.wftype | NORMAL | 一般発送の文書 |
|  | BULKWEB | 大量発送文書 |
| Workflow\_list.step | Myturn | 私の番 |
|  | Progress | 契約者が進行中 |
|  | Complete | 完了 |

