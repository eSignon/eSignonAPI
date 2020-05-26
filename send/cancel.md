# 문서 취소, 폐기

* 문서를 취소 또는 폐기합니다.

## API 속성-

| Url | Type | **Code** |
| :--- | :--- | :--- |
| https://docs.esignon.net/JEDOC/Common.do | POST | 1510Q |

## Request

### Parameters

####  Headers

| **Parameter Name**                         | **Value**                                                 | Required | **Description** |
| :--- | :--- | :--- | :--- |
| Content-Type | String | Y | "application/json" |
| Authorization | String | Y | "esignon 발급받은 Token" |

####   Body 

  Body - Header Parameter

| **Parameter Name**                         | **Value**                                                 | Required | **Description** |
| :--- | :--- | :--- | :--- |
| request\_code | String | Y | "1510Q"\(API 고유 코드\) |
| request\_msg | String | Y | "" |
| request\_lang | String | N | "ko","en","ja" |
| session\_id | String | Y | "thread\_023" |
| version | String | Y | "9.9.99" |

  Body - Body Parameter

| **Parameter Name** | **Value** | Required | **Description** |
| :--- | :--- | :--- | :--- |
| comp\_id | String | Y | 회사 ID |
| biz\_id | String | Y | "0" |
| memb\_email | String | Y | 사용자 이메일 |
| workflow\_id | String | Y | 문서 ID |
| command | String | Y | "cancel" - 취소 / "disposal" - 폐기 |
| description | String | N | "disposal" 시엔 필수 값 - "폐기 사유" |
| timezone\_offset | String | N | "disposal" 시엔 필수 값 - "UTC 시간값 입력"/"+00:00" |

## 요청 Body 예시\)

```text
{
	"header": {
		"request_code": "1510Q",
		"request_msg": "",
      	        "request_lang":"{ko or ja or en}",
		"session_id": "session_id",
		"version": "9.9.99"
	},
	"body": {
	"comp_id": "{회사 ID}",
      	"biz_id":"0",
      	"memb_email":"{사용자 이메일}",
      	"workflow_id":"{문서 ID}",
      	"command":"{ CANCEL or DISPOSAL }",
      	"description":"{폐기 사유 입력}", // 
      	"timezone_offset":"+09:00" // UTC 00:00 기준 한국의 경우 +09:00으로
	}
}
```

## Response

| Code | **Description** | **Reference** |
| :--- | :--- | :--- |
| 200 | 성공 | 형식이 잘못 된 경우 result\_msg 참조 |
| 400 | 연결 실패  |  |

#### Result\_msg

| Code | **Description** | **Reference** |
| :--- | :--- | :--- |
| 00 | 성공 | 성공 |
| 94 | 실패 | 인증키가 올바르지 않습니다. |
| 11 | 실패 | 필수 값이 없거나 상태 값이 올바르지 않습니다. |
| -1 | 실패 | 수신 메세지의 Body 정보가 잘못된 형태여서 파싱하지 못했습니다. |

## 응답 Body 예시\)

```text
{
	"header":{
		"session_id": "session_id",
		"response_code": "1510A",
		"result_code": "00",
		"result_msg": "폐기/취소를 성공했습니다.",
		"version": "9.9.99"
	},
	"body":{
		"comp_id": "{회사 ID}",
		"biz_id": "0",
		"memb_email": "{사용자 이메일}",
		"workflow_id": "{문서 ID}",
		"command": "{실행된 커맨드}"
	}
}
```

 See the Pen [API TEST](https://codepen.io/wodyd7654/pen/NWGmzmw) by wodyd7654 \([@wodyd7654](https://codepen.io/wodyd7654)\) on [CodePen](https://codepen.io).

