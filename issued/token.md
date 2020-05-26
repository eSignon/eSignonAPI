# 인증토큰 발급

* 인증토큰을 발급합니다.
* 이싸인온 API 사용시 필요한  회사 사용자의 인증토큰을 발급합니다. \( 유효기간 30일 \) 

## API 속성-

| Url | Type | **Code** |
| :--- | :--- | :--- |
| https://docs.esignon.net/api/{CompID}/startsimple | POST | 1001Q |

## Request

### Parameters

#### PathParameters

| **Parameter Name** | **Value** | **Description** |
| :--- | :--- | :--- |
| CompID | String                   | 회사ID |

####  Headers

| **Parameter Name**                         | **Value**                                                 | **Description** |
| :--- | :--- | :--- |
| Content-Type | String | "application/json" |
| User-Agent | String | "esignonapi" |

####   Body 

  Body - Header Parameter

| **Parameter Name**                         | **Value**                                                 | **Description** |
| :--- | :--- | :--- |
| request\_code | String | "1001Q"\(API 고유 코드\)                     |
| request\_msg | String | "인증코드 요청을 합니다 " |
| session\_id | String | "thread\_023" |

  Body - Body Parameter

| **Parameter Name** | **Value** | **Description** |
| :--- | :--- | :--- |
| comp\_id | String | 회사 ID |
| memb\_email | String | 사용자 이메일 |
| memb\_pwd | String | 사용자 비밀번호 |
| client\_id | String | esignon에서 발급받은 ID |

## 요청 Body 예시\)

```text
{
 "header" : {
   "request_code" : "1001Q",           
   "request_msg" : "인증코드 요청을 합니다.", 
   "session_id" : "thread_023"             
 },
 "body" : {
   "comp_id" : "{CompID}",
   "memb_email" : "{사용자 이메일}",  
   "memb_pwd" : "{사용자 비밀번호}",
   "client_id" : "{클라이언트 ID}"
  }
}

```

## Response

| Code | **Description** | **Reference** |
| :--- | :--- | :--- |
| 200 | 성공 | 형식이 잘못 된 경우 result\_msg 참조 |
| 400 | 실패 | 토큰  |

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
		"response_code": "1001A",
		"result_code": "00",
		"result_msg": "성공적으로 로그인되었습니다.",
		"session_id": ""
	},
	"body":{
		"access_token": "{인증토큰 코드}",
		"comp_id": "{회사 ID}",
		"device_id": "{ device_id }",
		"expire_date": "{만료일}",
		"memb_email": "{사용자 이메일}"
	}
}
```

## 

