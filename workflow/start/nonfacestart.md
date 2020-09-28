# 비대면 계약 시작

* 비대면 계약 서식을 시작합니다.
* export\_api 값을 따로 설정하여 받아올 값의 형식을 지정할 수 있습니다.\(선택사항\)
* export\_api 란 고객님이 진행중 승인, 반려를 할 경우 설정된 값을 설정된 URL로 esignon에서 request 해주는 기능입니다.
* ※ Array 타입의 파라미터가 optional 인 경우 사용 시 Array 내부 파라미터 값 중 필수 값은 반드시 입력하셔야합니다. 사용을 하지 않으실 경우엔 입력하지 않으셔도 상관없습니다.
* ※ language 파리미터의 경우 기본값 "ko-KR" \( 설정 안했을경우 \)

## API 주소 정보 

| Url | Type | **Code** |
| :--- | :--- | :--- |
| https://docs.esignon.net/api/{CompID}/startsimple | POST | 5005Q |

## Request

### Parameters

#### PathParameters

| **Parameter Name** | DataType | **Description** |
| :--- | :--- | :--- |
| CompID | String | 회사아이디 |

####  Headers

| **Parameter Name**                         | DataType                                       **** | Required | **Description** |
| :--- | :--- | :--- | :--- |
| Content-Type | String | Required | "application/json" |
| Authorization | String | Required | "esignon {token}" |

####   Body 

  Body - Header Parameter

| **Parameter Name**                         | DataType                                              **** | Required | **Description** |
| :--- | :--- | :--- | :--- |
| request\_code | String | Required | "5005Q"\(API 고유 코드\) |
| version | String | Required | "9.9.99" |

  Body - Body Parameter

| **Parameter Name** | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| biz\_id | String | Required | "0" |
| workflow\_name | String | Required | 시작할 문서 이름 |
| doc\_id | String | Required | 시작할 서식 ID |
| memb\_email | String | Required | 계약 시작자 이메일 |
| language | String | Optional | "ko-KR", "en-US", "ja-JP" |
| comment | String | Optional | 전달메시지 |
| player\_list | Array | Required | 서명하는 고객의 정보를 입력  서식의 단계에 맞춰서 작성 필수  |
| player\_list.field\_owner | String | Required | 작성 순서 " 1 " 부터 시작 |
| player\_list.email | String | Required | 이메일 or 전화번호 |
| player\_list.name | String | Required | 계약 진행자 이름 |
| player\_list.mobile\_number | String | Optional | 본인인증에 사용할 번호 |
| player\_list.password\_hint | String | Optional | 계약 진행시 사용할  비밀번호 힌트 |
| player\_list.password | String | Optional | 계약 진행시 사용할 비밀번호 |
| field\_list | Array | Optional | 미리 입력할 값이 있을 경우 추가하는 값 RadioBox,CheckBox,LabelBox ,TextBox 만 미리 값 입력가능 |
| field\_list.field\_name | String | Optional | 서식 필드 이름 |
| field\_list.field\_value | String | Optional | 서식 필드 값 Radio,Check Box 의 경우 값을 \(“N” or ”Y”\) 로 수신 Label,Text Box 의 경우 텍스트 값을 그대로 수신 |
| export\_api\_info | Array | Optional | 작성 데이터를 내보낼시에 설정하는 값 |
| export\_api\_info.api\_type | String | Required | "StartAndEnd"\(시작과 끝만\) or "ALL" \(전부\)  |
| export\_api\_info.url | String | Required | 통신 받을 url |
| export\_api\_info.enable | String | Optional | 사용여부 "true" or "false" |
| export\_api\_info.request\_code | String | Optional | 고객이 정의하는 임의의 값 or "embed"\( ExportAPI 설명 참조\) |
| export\_api\_info.clientid | String | Optional | esignon 에서 발급받은 ID \( 발급은 문의 \) |
| export\_api\_info.authorization | String | Optional | 데이터를 수신받을때 헤더 authorization 로 설정하고 싶은 값 |
| export\_api\_info.request\_params | Array | Optional | 문서내부에 특정 값을 받아 오고싶을때 사용 |
| export\_api\_info.request\_params.param\_id | String | Required | 받아올 파라미터 이름\(사용자 지정\) |
| export\_api\_info.request\_params.param\_value | String | Required | Params.fields에서 받아올 값이 문서에 없는경우 받아올 기본  |
| export\_api\_info.request\_params.fields | Array | Required | 서식 내부에 있는 필드명을 조회하여 필드이름에 해당하는 값이 문서에 존재할 경우 param\_value 대신에 들어가는 값 |
| export\_api\_info.request\_params.fields.doc\_id | String | Required | 서식 ID |
| export\_api\_info.request\_params.fields.field\_name | String | Required | 값을 가져올 서식 내 필드 명 |
| customer\_list | Array | Optional | 참조자가 있을 경우 추가 |
| customer\_list.email | String | Required | 이메일 or 휴대폰번호 |
| customer\_list.name | String | Required | 참조자 이름 |
| customer\_list.language | String | Optional | ko-KR, en-US, ja-JP |

## Request Body Example

```text
{
	"header": {
		"request_code": "5005Q",
		"version": "9.9.99"
	},
	"body": {
		"biz_id": "0",
		"workflow_name": "{ 작성할 문서명 }",
		"memb_email":"{ 계약 시작자 이메일 }",
		"doc_id": "{서식 ID}",
		"language": "ko-KR",
		"comment": "",
		"player_list": [{
			"field_owner": "1",(순서)
			"email": "{ 받는 사람 email or 받는 사람 휴대폰 번호 }",
      "name":"{ 받는 사람 이름 }",
			"language": "{ ko-KR }",
			"mobile_number": "{ 휴대폰 본인인증시 사용할 휴대폰번호 }",
      "password_hint":"{ 비밀번호 힌트 }",
      "password":"{비밀번호}"
		},{
			"field_owner": "2",
			"email": "{}",
      "name":"{}",
			"language": "{}",
			"mobile_number": "{}",
      "password_hint":"{}",
      "password":"{}"
		}],
		"field_list": [{
				"field_name": "{ field_name }", ( 서식에 미리 값을 넣을 경우에만 사용 )
				"field_value": "{ field_value }"
			}
		],
		"customer_list": [{ // 참조자 리스트
				"email": "{ id_type에 따라서 참조자 이메일 or 휴대폰번호 }",
	      "name":"{ 참조자 이름 }",
				"language": "{ko-KR}"
		}],
		"export_api_info": {
				"api_type": "{ StartAndEnd or ALL }",
				"url": "{ 통신 받을 url }",
				"enable": "{ true or false (사용여부)}",
				"request_code": "{ 고객이 정의하는 임의 값 }",
				"clientid": "{ 발급받은 UniqueID }",
				"authorization": "{설정 URL로 request 시에 Header - authorization 으로 받아올 값 }",
	      "request_params": [{
								"param_id": "{받아올 파라미터 이름(사용자 지정)}",
								"param_value": "{fields에서 설정한 값이 없을 경우 받아올 기본 값}",
								"fields": [{ // 서식에 field_name으로 등록한 필드 박스의 값이 없을경우 param_id:param_value return / 
																값이 있을경우엔 param_id:field_value를 return
                            "doc_id":"{ 서식 ID }",
                            "field_name":"{ 값을 가져올 서식 내 필드명 }" 
          			}]
				}]
	   }
	}
}
```

## Request Body Example - only Required

```text
{
	"header": {
		"request_code": "5005Q",
		"version": "9.9.99"
	},
	"body": {
		"biz_id": "0",
		"workflow_name": "{ 작성할 문서명 }",
		"memb_email":"{ 계약 시작자 이메일 }",
		"doc_id": "{서식 ID}",
		"language": "ko-KR",
		"player_list": [{
			"field_owner": "1",
			"email": "{ 받는 사람 email or 받는 사람 번호 }",
			"name": "{ 받는 사람 이름 }"
		}, {
			"field_owner": "2",
			"email": "{}",
			"name": "{}"
		}]
	}
}
```

## Request Body Example - For TEST Account

```text
{
	"header": {
		"request_code": "5005Q",
		"version": "9.9.99"
	},
	"body": {
		"comp_id": "testapi",
		"biz_id": "0",
		"memb_email": "guide@esignon.net",
		"language": "ko-KR",
		"comment": "",
		"workflow_name": "TEST-NAME",
		"doc_id": "1",
		"player_list": [{
				"field_owner": "1",
				"email": "guide@esignon.net",
				"name": "TEST",
				"language": "ko-KR"
			},
			{
				"field_owner": "2",
				"email": "guide@esignon.net",
				"name": "TEST",
				"language": "ko-KR"
			}
		],
		"field_list": [{
			"field_name": "name",
			"field_value": "name-value"
		}],
		"customer_list": [{
			"email": "guide@esignon.net",
			"name": "TEST",
			"language": "ko-KR"
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

## Response Body Example

```text
{ 
 "header":{
   "session_id": "S1001", 
   "response_code": "5005A",
   "result_code": "00", 
   "result_msg": "Work Flow가 시작됩니다.", 
   "version": "9.9.99" }, 
 "body":{ 
   "comp_id": "{ 회사 ID }", 
   "biz_id": "0", 
   "memb_email": "{ 계약 시작자 이메일 }", 
   "workflow_id": "{ 문서아이디 }", 
   "workflow_name": "{ 시작된 서식 이름 }", 
   "token": "{ 문서를 시작한 사람이 계약의 첫번째 작성자일 경우 작성페이지에 접근할때 사용하는 토큰값 }", 
   // https://docs.esignon.net/mail/sign?token=
   // 위의 주소에 발급된 토큰 값을 입력하면 서명페이지에 접근
   "lang": "ko-KR" }
}
```

## Response export\_api Example

```text
{
	"header": {
		"api_name": "export",
		"session_id": "S1001",
		"request_code": "{ exportAPI_info 에서 지정한 request_code 값 }",
		"authorization":"{ 비대면 계약 API 사용시 설정했던 authorization 값 }"
	},
	"body": {
		"clientid": "{ eSignonAPI 사용을 위한 Unique ID }",
		"processid": "1", //문서의 진행 단계 구분값
		"requestid": "{ header 의 request_code 값 }",
		"actionid": "1", //문서의 진행 단계 구분값
		"workdatetime": "2020-01-31 04:23:28.0", //작성완료시간
		"worktype": "CF", //CF=승인, RT=반려 ( 처음 계약자가 반려시 문서는 취소 처리됩니다.)
		"wfuid": "{}", //문서의 고유ID
		"useremail": "{ 서명자 이메일or휴대폰번호 }", 
		"opinion": "", //승인, 반려시 고객들이 반려 메세지,전송 메세지를 사용한 경우 출력
		"param_id": "param_value", // fields 값을 설정한 경우 fields_value를 return
	}
}
```

