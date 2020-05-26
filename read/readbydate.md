# 기간으로 조회

* 문서의 완료 or 시작 기간으로 조회합니다.

## API 속성-

| Url | Type | **Code** |
| :--- | :--- | :--- |
| https://docs.esignon.net/api/{CompID}/search | POST | 5009Q |

## Request

### Parameters

#### PathParameters

| **Parameter Name** | **Value** | **Description** |
| :--- | :--- | :--- |
| CompID | String | 회사ID |

####  Headers

| **Parameter Name**                         | **Value**                                                 | **Description** |
| :--- | :--- | :--- |
| Content-Type | String | "application/json" |
| User-Agent | String | "esignonapi" |
| Authorization | String | "esignon 발급받은 Token" |

####   Body 

  Body - Header Parameter

| **Parameter Name**                         | **Value**                                                 | **Description** |
| :--- | :--- | :--- |
| request\_code | String | "5009Q"\(API 고유 코드\) |
| api\_name | String | "start api" |
| session\_id | Stri | "" |
| version | String | "1.1.60" |

  Body - Body Parameter

| **Parameter Name** | **Value** | **Description** |
| :--- | :--- | :--- |
| comp\_id | String | 회사 ID |
| doc\_uid | Stirng | 조회할 문서의 서식 ID |
| client\_id | String | esignon 에서 발급받은 ID \( 발급은 문의 \) |
| search\_date\_type | String | START or END / START – 문서 시작 기준 / END – 문서 완료 기준 |
| start\_date | String | 검색 시작 지점 YYYY-MM-DD |
| end\_date | String | 검색 종료 지점 YYYY-MM-DD |
| field\_list | Data | 조회할 문서 정 |
| field\_list.doc\_uid | String | 조회할 문서의 서식 ID |
| field\_list.field\_name | String | 조회할 문서 서식의 필드 이름 |

## 요청 Body 예시\)

```text
{
 "header" : {
   "request_code" : "5009Q",
   "api_name" : "start api",
   "session_id" : "",
   "version" : "1.1.60"
 },
   "body" : {
   "comp_id": "{회사 ID}",
   "doc_uid": "{서식 ID}",
   "client_id": "{발급받은 클라이언트 ID}",
   "search_date_type":"{START or END}",
   "start_date": "{검색 시작 지점}",
   "end_date": "{검색 종료 지점}",
   "field_list": [{
				"doc_uid": "{회사 ID}",
				"field_name": "{서식 내부에 있는 필드명}"
			}]
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
| 17 | 실패 | 필수 검색 조건이 없습니다. |
| 18 | 실패 | 검색 조건이 없습니다. |
| 19 | 실패 | 날짜 형식이 잘못되었습니다. |

## 응답 Body 예시\)

```text
{
	"header":{
	"response_code": "5009A",
	"result_code": "00",
	"result_msg": "필드 상태가 검색되었습니다.",
	"session_id": "",
	"version": "1.1.60"
	},
	"body":{
	"comp_id": "{회사 ID}",
	"wf_list":[
		{
		"doc_uid": "{서식ID}",
		"end_date": "{서명 완료 시간}",
		"total_process_count": "1", // 서식 단계
		"wf_manager_name": "{ 문서 생성자 이름 }",
		"wf_manager_email": "{ 문서 생성자 이메일 }",
		"wf_status": "Complete", // 문서 상태 Complete – 완료, Playing – 진행중
		"field_value": "{조회한 필드 값}",
		"wfuid": "{문서 ID}",
		"current_process_no": "1",
		"wf_title": "{문서 이름}",
		"start_date": "{문서 시작 시간}",
		"field_name": "{조회한 필드 이름}"
		}
	]
	}
}
```

