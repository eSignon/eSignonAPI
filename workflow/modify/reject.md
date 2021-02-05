# 승인, 반려

* 문서를 승인 또는 반려 합니다.
* 승인시 문서는 필수 값이 입력되어 있어야합니다.

## API 속성-

| Url | Type | **Code** |
| :--- | :--- | :--- |
| https://docs.esignon.net/api/:companyId/action | POST | 5010Q |

## Request

### Parameters

#### PathParameters

| **Parameter Name** | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| companyId | String | Required | 회사ID |

####  Headers

| **Parameter Name**                         | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| Content-Type | String | Required | "application/json" |
| Authorization | String | Required | "esignon ${발급받은토큰}" |

####   Body 

  Body - Header Parameter

| **Parameter Name**                         | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| request\_code | String | Required | "5010Q"\(API 고유 코드\) |
| api\_name | String | Optional | "start api" |
| session\_id | String | Optional | "" |
| version | String | Required | "9.9.99" |

  Body - Body Parameter

| **Parameter Name** | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| comp\_id | String | Required | 회사 ID |
| biz\_id | String | Required | "0" |
| client\_id | String | Required | esignon 에서 발급받은 ID \( 발급은 문의 \) |
| memb\_email | String | Required | 계약 진행자 이메일 |
| action\_id | String | Required | 계약 진행중인 단계 |
| workflow\_id | String | Required | 계약중인 문서 ID |
| comment | String | Required | 승인 or 반려 시 전달하는 메세지 |
| command | String | Required | RT - 반려 / CF - 승인 / CF 시엔 문서에 필수 값을 입력한 상태여야 진행 가능 |

## 요청 Body 예시\)

```javascript
{
 "header" : {
   "request_code" : "5010Q",            
   "api_name" : "start api",    
   "session_id" : "",    
   "version" : "9.9.99"
 },
 "body" : {
   "comp_id": "{회사 ID}",
   "client_id":"{발급받은 클라이언트 ID}",
   "biz_id":"0",
   "memb_email":"{계약 진행자 이메일}",
   "action_id":"1" // 계약 진행중인 단계,
   "workflow_id":"{계약 중인 문서 ID}",
   "comment":"{승인 or 반려시 전달하는 문자}",
   "command":"{RT or CF}" // RT – 반려, CF – 승인
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
| 10 | 실패 | 실패 |
| 12 | 실패 | 수신 메세지의 Body 정보가 잘못된 형태여서 파싱하지 못했습니다. |
| 99 | 실패 | 필수항목이 남아있어 진행할 수 없습니다. |
| 99 | 실패 | Unexpected exception \( 잘못된 포맷 \) |

## 응답 Body 예시\)

```javascript
{
	"header":{
		"response_code": "5010A",
		"result_code": "00",
		"result_msg": "성공하였습니다.",
		"version": "9.9.99"
	},
	"body":{
		"comp_id": "{회사 ID}"
	}
}
```

