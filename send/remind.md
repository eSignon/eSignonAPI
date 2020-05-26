# 재전송

* 문서를 재전송 합니다.

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

| **Parameter Name**                         | **Value**                                                 | **Description** |
| :--- | :--- | :--- |
| Content-Type | String | "application/json" |
| Authorization | String | "esignon 발급받은 Token" |

####   Body 

  Body - Header Parameter

| **Parameter Name**                         | **Value**                                                 | **Description** |
| :--- | :--- | :--- |
| request\_code | String | "1429Q"\(API 고유 코드\) |
| request\_msg | String | "Remind 를 요청합니다." |
| session\_id | String | "thread\_023" |

  Body - Body Parameter

| **Parameter Name** | **Value** | **Description** |
| :--- | :--- | :--- |
| comp\_id | String | 회사 ID |
| biz\_id | String | "0" |
| workflow\_id | String | 진행 문서 ID |
| memb\_email | String | 사용자 이메일 |

## 요청 Body 예시\)

```text
{
"header": {
	"request_code": "1429Q",
	"request_msg": "Remind 를 요청합니다.",
	"session_id": "thread_023"},
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
| 99 | 실패 | Unexpected exception \( 잘못된 포맷 \) |
| 12 | 실패 | 수신 메세지의 Body 정보가 잘못된 형태여서 파싱하지 못했습니다. |

## 응답 Body 예시\)

```text
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

