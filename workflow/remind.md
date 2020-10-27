# 재전송

* 문서를 재전송 합니다.
* 완료, 취소된 문서는 재전송 할 수 없습니다.

## API 속성-

| Url | Type | **Code** |
| :--- | :--- | :--- |
| https://docs.esignon.net/JEDOC/Common.do?lang={} | POST | 1429Q |

## Request

### Parameters

#### PathParameters

| **Parameter Name** | **Value** | **Description** |
| :--- | :--- | :--- |
| lang | String | ko,en,jp |

####  Headers

| **Parameter Name**                         | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| Content-Type | String | Required | "application/json" |
| Authorization | String | Required | "esignon 발급받은 Token" |

####   Body 

  Body - Header Parameter

| **Parameter Name**                         | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| request\_code | String | Required | "1429Q"\(API 고유 코드\) |
| request\_msg | String | Required | "Remind 를 요청합니다." |
| session\_id | String | Required | "" |

  Body - Body Parameter

| **Parameter Name** | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| comp\_id | String | Required | 회사 ID |
| biz\_id | String | Required | "0" |
| workflow\_id | String | Required | 진행 문서 ID |
| memb\_email | String | Required | 사용자 이메일 |

## 요청 Body 예시\)

```javascript
{
	"header": {
		"request_code": "1429Q",
		"request_msg": "Remind 를 요청합니다.",
		"session_id": ""},
	"body": {
		"comp_id": "{회사 ID}",
		"biz_id": "0",
		"memb_email": "{사용자 이메일}",
		"workflow_id": "{진행 문서 ID}"
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
| 11 | 실패 | 서명이 완료된 문서입니다. |
| 12 | 실패 | 취소 처리 된 문서입니다. |
| 99 | 실패 | Unexpected exception \( 잘못된 포맷 \) |

## 응답 Body 예시\)

```javascript
{
	"header":{
		"session_id": "thread_023",
		"response_code": "1429A",
		"result_code": "00",
		"result_msg": "Remind를 성공 하었습니다."
	},
	"body":{
		"comp_id": "{회사 ID}",
		"biz_id": "0",
		"memb_email": "{사용자 이메일}",
		"workflow_id": "{진행 문서 ID}"
	}
}

```

