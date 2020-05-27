# 서식 목록조회

* 서식 목록을 조회합니다.

## API 속성-

| Url | Type | **Code** |
| :--- | :--- | :--- |
| https://docs.esignon.net/JEDOC/Common.do?lang={value} | POST | 1123Q |

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
| request\_code | String | "1123Q"\(API 고유 코드\) |
| request\_msg | String | "" |
| session\_id | Stri | "" |
| version | String | "9.9.99" |

  Body - Body Parameter

| **Parameter Name** | **Value** | **Description** |
| :--- | :--- | :--- |
| comp\_id | String | 회사 ID |
| memb\_email | Stirng | 사용자 이메일 |
| biz\_id | String | "0" |
| search\_dir\_id | String | 서식을 찾을 폴더 ID / "all"\(공유폴더\),"my"\(내 폴더\) |
| display\_order\_mode | String | 정렬기준값 Response file\_list 필드값 순서대로 1~11 |

## 요청 Body 예시\)

```text
{
        "header": {
                "request_code": "1123Q",
                "request_msg": "",
                "session_id": "session_id",
                "version": "9.9.99"
        },
        "body": {
                 "comp_id": "{회사 ID}",
                 "biz_id": "0",
                 "memb_email" : "{사용자 이메일}",
                 "search_dir_id": "all", // all ( 공유폴더 ) , my ( 내 폴더 )
                 "display_order_mode": "1" // 정렬 기준값 1 ~ 11
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
	"body":{
		"comp_id": "{회사 ID}",
		"biz_id": "0",
		"memb_email": "{사용자 이메일}",
		"search_dir_id": "all",
		"file_list":[{서식 정보 // Example} file_lsit 참조}] 서식 전체 조회이기 때문에 모든 서식 데이터
	},
	"header":{
		"session_id": "session_id",
		"response_code": "1123A",
		"result_code": "00",
		"result_msg": "파일 리스트입니다.",
		"version": "9.9.99"
	}
}

```

#### Example\) file\_list

```text
{
	"file_id": "{서식ID}",
	"file_type": "templete",
	"file_name": "{서식 이름}",
	"dir_type": "{서식이 위치한 폴더}",
	"create_memb_email": "{서식 작성자 이메일}",
	"create_date": "{서식 생성일}",
	"create_memb_name": "{서식 작성자 이름}",
	"file_workflow_count": "1", // 서식의 단계 수
	"file_workflow_type": "WEBTYPE", // 대면,비대면 WEBTYPE 대량 BULK
	"file_workflow_library_id": "{서식의 lib ID}", // 대량 발송에 사용
	"last_modify_date": "{마지막 수정일}"
}
```

