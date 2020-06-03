# 비대면 계약 시작

* 비대면 계약 서식을 발송합니다.
* export\_api 값을 따로 설정하여 받아올 값의 형식을 지정할 수 있습니다.\(선택사항\)

## API 속성-

| Url | Type | **Code** |
| :--- | :--- | :--- |
| https://docs.esignon.net/api/{CompID}/startsimple | POST | 5005Q |

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
| Authorization | String | "esignon 발급받은 Token" |

####   Body 

  Body - Header Parameter

| **Parameter Name**                         | **Value**                                                 | **Description** |
| :--- | :--- | :--- |
| request\_code | String | "5005Q"\(API 고유 코드\) |
| api\_name | String | "start api" |
| session\_id | String | "S1001" |
| version | String | "1.1.59" |

  Body - Body Parameter

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Parameter Name</b>
      </th>
      <th style="text-align:left"><b>Value</b>
      </th>
      <th style="text-align:left"><b>Description</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">comp_id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xD68C;&#xC0AC; ID</td>
    </tr>
    <tr>
      <td style="text-align:left">biz_id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&quot;0&quot;</td>
    </tr>
    <tr>
      <td style="text-align:left">client_id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">esignon &#xC5D0;&#xC11C; &#xBC1C;&#xAE09;&#xBC1B;&#xC740; ID ( &#xBC1C;&#xAE09;&#xC740;
        &#xBB38;&#xC758; )</td>
    </tr>
    <tr>
      <td style="text-align:left">memb_email</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xBC1C;&#xC1A1;&#xD560; &#xC774;&#xBA54;&#xC77C;</td>
    </tr>
    <tr>
      <td style="text-align:left">workflow_name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xBC1C;&#xC1A1;&#xD560; &#xC11C;&#xC2DD; &#xC774;&#xB984;</td>
    </tr>
    <tr>
      <td style="text-align:left">doc_id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xBC1C;&#xC194;&#xD560; &#xC11C;&#xC2DD; ID</td>
    </tr>
    <tr>
      <td style="text-align:left">language</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&quot;ko-KR&quot;, &quot;en-US&quot;, &quot;ja-JP&quot;</td>
    </tr>
    <tr>
      <td style="text-align:left">player_list</td>
      <td style="text-align:left">Data</td>
      <td style="text-align:left">&#xC11C;&#xBA85;&#xD558;&#xB294; &#xACE0;&#xAC1D;&#xC758; &#xC815;&#xBCF4;&#xB97C;
        &#xC785;&#xB825;</td>
    </tr>
    <tr>
      <td style="text-align:left">player_list.field_owner</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Play &#xC21C;&#xC11C; &quot; 1 &quot; &#xBD80;&#xD130; &#xC2DC;&#xC791;</td>
    </tr>
    <tr>
      <td style="text-align:left">player_list.email</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        <p>memb_id_type &#xC5D0; &#xB530;&#xB77C;</p>
        <p>&#xC774;&#xBA54;&#xC77C; or &#xC804;&#xD654;&#xBC88;&#xD638;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">player_list.memb_id_type</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&quot;EMail&quot; or &quot;Mobile&quot;</td>
    </tr>
    <tr>
      <td style="text-align:left">player_list.name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xACC4;&#xC57D; &#xC9C4;&#xD589;&#xC790; &#xC774;&#xB984;</td>
    </tr>
    <tr>
      <td style="text-align:left">player_list.enable_mobile_cert</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xD734;&#xB300;&#xD3F0; &#xBCF8;&#xC778;&#xC778;&#xC99D; &#xAE30;&#xB2A5;
        &quot;True or false&quot;</td>
    </tr>
    <tr>
      <td style="text-align:left">player_list.mobile_number</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xBCF8;&#xC778;&#xC778;&#xC99D;&#xC5D0; &#xC0AC;&#xC6A9;&#xD560; &#xBC88;&#xD638;</td>
    </tr>
    <tr>
      <td style="text-align:left">player_list.enable_password_cert</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xBE44;&#xBC00;&#xBC88;&#xD638; &#xC778;&#xC99D; &#xAE30;&#xB2A5; &quot;True
        or false&quot;</td>
    </tr>
    <tr>
      <td style="text-align:left">player_list.password_hint</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xBE44;&#xBC00;&#xBC88;&#xD638; &#xD78C;&#xD2B8;</td>
    </tr>
    <tr>
      <td style="text-align:left">player_list.password</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xBE44;&#xBC00;&#xBC88;&#xD638;</td>
    </tr>
    <tr>
      <td style="text-align:left">field_list</td>
      <td style="text-align:left">Data</td>
      <td style="text-align:left">&#xBBF8;&#xB9AC; &#xC785;&#xB825;&#xD560; &#xAC12;&#xC774; &#xC788;&#xC744;&#xACBD;&#xC6B0;
        &#xCD94;&#xAC00;&#xD558;&#xB294; &#xAC12;</td>
    </tr>
    <tr>
      <td style="text-align:left">field_list.doc_id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xC11C;&#xC2DD; ID</td>
    </tr>
    <tr>
      <td style="text-align:left">field_list.field_name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xC11C;&#xC2DD; &#xD544;&#xB4DC; &#xC774;&#xB984;</td>
    </tr>
    <tr>
      <td style="text-align:left">field_list.field_value</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xC11C;&#xC2DD; &#xD544;&#xB4DC;</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info</td>
      <td style="text-align:left">Data</td>
      <td style="text-align:left">&#xC791;&#xC131; &#xB370;&#xC774;&#xD130;&#xB97C; &#xB0B4;&#xBCF4;&#xB0BC;&#xC2DC;&#xC5D0;
        &#xC124;&#xC815;&#xD558;&#xB294; &#xAC12;</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.api_type</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&quot;StartAndEnd&quot;(&#xC2DC;&#xC791;&#xACFC; &#xB05D;&#xB9CC;) or
        &quot;ALL&quot; (&#xC804;&#xBD80;)</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.url</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xD1B5;&#xC2E0; &#xBC1B;&#xC744; url</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.enable</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xC0AC;&#xC6A9;&#xC5EC;&#xBD80; &quot;true&quot; or &quot;false&quot;</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.request_code</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xACE0;&#xAC1D;&#xC774; &#xC815;&#xC758;&#xD558;&#xB294; &#xC784;&#xC758;&#xC758;
        &#xAC12;</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.clientid</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">esignon &#xC5D0;&#xC11C; &#xBC1C;&#xAE09;&#xBC1B;&#xC740; ID ( &#xBC1C;&#xAE09;&#xC740;
        &#xBB38;&#xC758; )</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.request_params</td>
      <td style="text-align:left">Data</td>
      <td style="text-align:left">&#xBC1B;&#xC544;&#xC62C; &#xD544;&#xB4DC;&#xC758; &#xC815;&#xBCF4;&#xB97C;
        &#xAC00;&#xC9C4; Data</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.request_params.param_id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xC784;&#xC758;&#xC9C0;&#xC815;</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.request_params.param_value</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&quot;&quot;</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.request_params.fields</td>
      <td style="text-align:left">Data</td>
      <td style="text-align:left">&#xBC1B;&#xC544;&#xC62C; &#xC11C;&#xC2DD; ID&#xC640; &#xD544;&#xB4DC;&#xBA85;&#xC744;
        &#xAC00;&#xC9C4; Data</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.request_params.fields.doc_id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xC11C;&#xC2DD; ID</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.request_params.fields.field_name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xC11C;&#xC2DD; &#xB0B4; &#xD544;&#xB4DC; &#xBA85;</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.response_params</td>
      <td style="text-align:left">Data</td>
      <td style="text-align:left">&quot;&quot;</td>
    </tr>
    <tr>
      <td style="text-align:left">customer_list</td>
      <td style="text-align:left">Data</td>
      <td style="text-align:left">&#xCC38;&#xC870;&#xC790;&#xAC00; &#xC788;&#xC744; &#xACBD;&#xC6B0; &#xCD94;&#xAC00;</td>
    </tr>
    <tr>
      <td style="text-align:left">customer_list.email</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">id_type &#xC5D0; &#xB530;&#xB77C; &#xC774;&#xBA54;&#xC77C; or &#xBC88;&#xD638;</td>
    </tr>
    <tr>
      <td style="text-align:left">customer_list.id_type</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">EMail or Mobile</td>
    </tr>
    <tr>
      <td style="text-align:left">customer_list.name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xCC38;&#xC870;&#xC790; &#xC774;&#xB984;</td>
    </tr>
    <tr>
      <td style="text-align:left">customer_list.language</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">ko-KR, en-US, ja-JP</td>
    </tr>
    <tr>
      <td style="text-align:left">comment</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&quot;&quot;</td>
    </tr>
  </tbody>
</table>

## 요청 Body 예시\)

```text
{
	"header": {
		"request_code": "5005Q",
		"api_name": "start api",
		"session_id": "S1001",
		"version": "9.9.99"
	},
	"body": {
		"comp_id": "{ 회사 ID }",
		"biz_id": "0",
		"client_id": "{ 발급요청한 client_id }",
		"memb_email": "{ 작성자 이메일 }",
		"workflow_name": "{ 작성할 문서명 }",
		"doc_id": "{서식 ID}",
		"language": "ko-KR",
		"player_list": [{
			"field_owner": "1",(순서)
			"email": "{ 받는 사람 email or 받는 사람 번호 }",( memb_id_type에 따라서)
			"memb_id_type": "{ Email or Mobile }",
          	        "name":"{ 받는 사람 이름 }",
			"language": "{ ko-KR }",
			"enable_mobile_cert": "{ true or false }",
			"mobile_number": "{ 휴대폰번호 }",
			"enable_password_cert":"{ ture or false }",
      "password_hint":"{ 비밀번호 힌트 }",
      "password":"{비밀번호}”

		},{
			"field_owner": "2",
			"email": "{}",
			"memb_id_type": "{}",
          	        "name":"{}",
			"language": "{}",
			"enable_mobile_cert": "{}",
			"mobile_number": "{}",
			"enable_password_cert":"{}",
      "password_hint":"{}",
      "password":"{}”
		}],
		"field_list": [{
				"doc_id": "{ 서식ID }",
				"field_name": "{ field_name }", ( 서식에 미리 값을 넣을 경우에만 사용 )
				"field_value": "{ field_value }"
			}
		],
		"customer_list": [{ // 참조자 리스트
			"email": "{ id_type에 따라서 참조자 이메일 or 휴대폰번호 }",
			"id_type": "{EMail or Mobile}",
          	        "name":"{ 참조자 이름 }",
			"language": "{ko-KR}"
		}],
		"export_api_info": { ( 사용시에만 값 입력 ) 
			"api_type": "{ StartAndEnd or ALL }",
			"url": "{ 통신 받을 url }",
			"enable": "{ true or false (사용여부)}",
			"request_code": "{ 고객이 정의하는 임의 값 }",
			"clientid": "{ 발급받은 UniqueID }",
                "request_params": [{
				"param_id": "{임의지정}",
				"param_value": "",
				"fields": [
                                “doc_id”:”{ 서식 ID }”,
                                “field_name”:”{ 서식 내 필드명 }” ]
          }],
		"response_params": []
		},
		"comment": ""
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
   "session_id": "S1001", 
   "response_code": "5005A",
   "result_code": "00", 
   "result_msg": "Work Flow가 시작됩니다.", 
   "version": "9.9.99" }, 
 "body":{ 
   "comp_id": "{ 회사 ID }", 
   "biz_id": "0", 
   "memb_email": "{ 생성자 이메일 }", 
   "workflow_id": "{ 서식 ID }", 
   "workflow_name": "{ 시작된 서식 이름 }", 
   "token": "{ 발급된 토큰 }", "lang": "ko-KR" }
}
```

## export\_api 응답 예시\)

```text
{
	"header": {
		"api_name": "export",
		"session_id": "S1001", //고정된 값으로 현재 사용하지 않음.
		"request_code": "{ exportAPI_info 에서 지정한 값 }"
	},
	"body": {
		"wfluid": "0", //이싸인온에서 사용하는 서식구분id
		"clientid": "{ eSignonAPI 사용을 위한 Unique ID }",
		"processid": "1", //이싸인온에서 사용하는 process 구분값
		"requestid": "{ header 의 request_code 값 }",
		"actionid": "1", //이싸인온에서 사용하는 action 구분값
		"workdatetime": "2020-01-31 04:23:28.0", //작성완료시간
		"worktype": "CF", 
//CF=승인, RT=반려 작성자가 2단계 이상의 문서에서는 승인, 반려를 선택할 수 있음.
		"wfuid": "{}", //이싸인온에서 사용하는 문서구분id
		"useremail": "{ 서명자 이메일or휴대폰번호  }", 
		"opinion": "", //comment (작성시)
		"param_id1": "value", // param_id로 지정한 값이 들어옴
		"param_id2": "value", // param_id로 지정한 값이 들어옴
		"param_id3": "value" // param_id로 지정한 값이 들어옴
	}
}
```

