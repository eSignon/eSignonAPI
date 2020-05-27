# 진행 문서 목록조회

* 해당 회사의 진행문서 목록을 전부 조회합니다. 
* GET 방식의 API로 HEADERS에 발급받은 토큰 값만 입력하여 조회합니다.

{% api-method method="get" host="https://docs.esignon.net/" path="worklists/new?page={value}&rows={value}" %}
{% api-method-summary %}
진행 문서 조회
{% endapi-method-summary %}

{% api-method-description %}
진행 문서의 상태,종류,단계등을 확인 할 수 있습니다.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="rows" type="string" required=false %}
1페이지에 몇개나 조회할 것인지 / 기본값 50
{% endapi-method-parameter %}

{% api-method-parameter name="page" type="string" required=false %}
몇페이지에 있는 목록을 조회할 것인지 / 기본값 1
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=false %}
esignon {발급받은토큰값} 
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
		"comp_id": "{회사 ID}",
		"isManager": true,
		"memb_email": "{해당 토큰을 가진 이메일}",
		"page": "{출력할 페이지의 번호}",
		"rows": "{페이지 당 보여줄 목록의 갯수}",
		"total": "{전체 문서 수}",
		"workflow_list":[{
			"wfuid": {문서 ID},
			"wfname": "{문서 제목}",
			"wftype": "{문서 타입}",
			"status": "{문서 상태}",
			"step": "{문서 단계}",
			"nickname": "{문서 작성자}",
			"currentactionid": {계약 중인 단계 번호},
			"email": "{문서 작성자 이메일}",
			"startdate": "{문서 시작일}",
			"totalprocesscount": {문서의 총 단계 갯수},//3단계 문서일 경우 3
			"currentprocesscount": {완료 된 계약 단계 번호},
			"confirmdate": "{문서 완료일}",
			"preactionid": {},//esignon 코드처리를 위한 변수
			"preactionemail":{참조하는 이메일}
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
| Workflow\_list.status | Playing | 진행중 |
|  | Canceled | 취소 |
|  | Complete | 완료 |
|  | Truncate | 폐기 |
| Workflow\_list.wftype | NORMAL | 일반 발송 문서 |
|  | BULKWEB | 대량 발송 문서 |
| Workflow\_list.step | Myturn | 내 차례 |
|  | Progress | 계약자가 진행중 |
|  | Complete | 완료 |

