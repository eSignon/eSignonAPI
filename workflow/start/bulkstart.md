# 대량전송 계약 시작

* 계약 대량 전송을 시작합니다.

* 대량 계약시 서명 순서는 서식을 작성 할 때 설정한 단계에 따라 고객, 담당자가 문서를 받을 순서가 결정됩니다. \(1단계만 설정 시 고객에게만 전달\) 담장자는 생성자로 고정되며 고객정보는 unset\_player\_list 에 들어간 값으로 결정됩니다. unset\_player\_list에 들어있는 모든 고객에게 계약이 발전송니다.

## API 주소 정보 

| Url | Type | **Code** |
| :--- | :--- | :--- |
| https://docs.esignon.net/JEDOC/Common.do | POST | 1410Q |

## Request

### Parameters

####  Headers

| **Parameter Name**                         | DataType | **Description** |
| :--- | :--- | :--- |
| Content-Type | String | application/json |
| Authorization | String | esignon ${발급받은토큰} |

####   Body 

  Body - Header Parameter

| **Parameter Name**                         | DataType | **Description** |
| :--- | :--- | :--- |
| request\_code | String | "1410Q"\(API 고유 코드\) |
| request\_msg | String | "Work Flow Bulk Sending를 시작합니다." |
| session\_id | String | "thread\_023" |
| version | String | "9.9.99" |

  Body - Body Parameter

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Parameter Name</b>
      </th>
      <th style="text-align:left">DataType</th>
      <th style="text-align:left"><b>Description</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">comp_id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xD68C;&#xC0AC; ID / companyId</td>
    </tr>
    <tr>
      <td style="text-align:left">biz_id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&quot;0&quot;</td>
    </tr>
    <tr>
      <td style="text-align:left">memb_email</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xC0DD;&#xC131;&#xC790; &#xC774;&#xBA54;&#xC77C;</td>
    </tr>
    <tr>
      <td style="text-align:left">workflow_name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&quot;&quot;</td>
    </tr>
    <tr>
      <td style="text-align:left">workflow_lib_id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        <p>&#xC11C;&#xC2DD;&#xC744; &#xC0DD;&#xC131;&#xD558;&#xBA74; &#xC0DD;&#xC131;&#xB418;&#xB294;
          lid_id
          <br />&#xC11C;&#xC2DD;ID&#xC640;&#xB294; &#xB2E4;&#xB978;&#xAC12;&#xC785;&#xB2C8;&#xB2E4;.</p>
        <p>(&#xC11C;&#xC2DD;&#xBAA9;&#xB85D;&#xC870;&#xD68C;&#xC5D0;&#xC11C; &#xD655;&#xC778;&#xAC00;&#xB2A5;&#xD569;&#xB2C8;&#xB2E4;.)</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">unset_player_list</td>
      <td style="text-align:left">Data</td>
      <td style="text-align:left">&#xC11C;&#xBA85;&#xD558;&#xB294; &#xACE0;&#xAC1D;&#xC758; &#xC815;&#xBCF4;&#xB97C;
        &#xC785;&#xB825;</td>
    </tr>
    <tr>
      <td style="text-align:left">unset_player_list.memb_id_type</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&quot;EMail&quot; or &quot;Mobile&quot;</td>
    </tr>
    <tr>
      <td style="text-align:left">unset_player_list.email</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        <p>memb_id_type &#xC5D0; &#xB530;&#xB77C;</p>
        <p>&#xC774;&#xBA54;&#xC77C; or &#xC804;&#xD654;&#xBC88;&#xD638;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">unset_player_list.name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xACC4;&#xC57D; &#xC9C4;&#xD589;&#xC790; &#xC774;&#xB984;</td>
    </tr>
    <tr>
      <td style="text-align:left">unset_player_list.language</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&quot;ko-KR&quot;,&quot;en-US&quot;,&quot;ja-JP&quot;</td>
    </tr>
    <tr>
      <td style="text-align:left">unset_player_list.workflow_name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xC2DC;&#xC791;&#xD558;&#xB294; &#xC11C;&#xC2DD; &#xC774;&#xB984;</td>
    </tr>
    <tr>
      <td style="text-align:left">unset_player_list.enable_mobile_cert</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xD734;&#xB300;&#xD3F0; &#xC778;&#xC99D; &#xAE30;&#xB2A5; &quot;true
        or false&quot;</td>
    </tr>
    <tr>
      <td style="text-align:left">unset_player_list.mobile_number</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xBCF8;&#xC778;&#xC778;&#xC99D;&#xC5D0; &#xC0AC;&#xC6A9;&#xD560; &#xBC88;&#xD638;
        / - &#xC5C6;&#xC774;</td>
    </tr>
    <tr>
      <td style="text-align:left">unset_player_list.enable_password_cert</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xBE44;&#xBC00;&#xBC88;&#xD638; &#xC778;&#xC99D; &#xAE30;&#xB2A5; &quot;true
        or false&quot;</td>
    </tr>
    <tr>
      <td style="text-align:left">unset_player_list.password_hint</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xBE44;&#xBC00;&#xBC88;&#xD638; &#xD78C;&#xD2B8;</td>
    </tr>
    <tr>
      <td style="text-align:left">unset_player_list.password</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xBE44;&#xBC00;&#xBC88;&#xD638;</td>
    </tr>
    <tr>
      <td style="text-align:left">unset_player_list.field_list</td>
      <td style="text-align:left">Data</td>
      <td style="text-align:left">
        <p>&#xBBF8;&#xB9AC; &#xC785;&#xB825;&#xD560; &#xAC12;&#xC774; &#xC788;&#xC744;&#xACBD;&#xC6B0;
          &#xCD94;&#xAC00;&#xD558;&#xB294; &#xAC12;</p>
        <p>&#xC5EC;&#xB7EC;&#xAC1C; &#xCD94;&#xAC00;&#xAC00;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">unset_player_list.field_list.doc_id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xC11C;&#xC2DD; ID</td>
    </tr>
    <tr>
      <td style="text-align:left">unset_player_list.field_list.field_name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xC11C;&#xC2DD; &#xD544;&#xB4DC; &#xC774;&#xB984;</td>
    </tr>
    <tr>
      <td style="text-align:left">unset_player_list.field_list.field_value</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xC11C;&#xC2DD; &#xD544;&#xB4DC;</td>
    </tr>
    <tr>
      <td style="text-align:left">comment</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&quot;&quot;</td>
    </tr>
    <tr>
      <td style="text-align:left">enable_legal_agreement</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&quot;false&quot;</td>
    </tr>
  </tbody>
</table>

## 요청 Body 예시\)

```javascript
{
  "header": {
    "request_code": "1410Q",
    "api_name": "Work Flow Bulk Sending를 시작합니다.",
    "session_id": "",
    "version" : "9.9.99"
  },
  "body": {
    "comp_id": "{회사 ID}",
    "biz_id": "0",
    "memb_email": "{ 사용자 이메일 }",
    "workflow_lib_id": "{ 서식의 lib_id }",
    "workflow_name": "",
    "unset_player_list": [{
        "memb_id_type" : "{ EMail or Mobile }",
        "email": "{ memb_id_type 에 따라 번호나 이메일 }",
        "name" : "{ 받는 사람 이름 }",
        "language": "{ko-KR or ja-JP or en-US}",
        "workflow_name" : "{서식 이름}",
        "enable_mobile_cert" : "{ 휴대폰 본인인증 여부 true or false }",
        "mobile_number" : "{ 본인 인증에 사용할 전화번호 }",
        "enable_password_cert":"{true or false}",
	      "password_hint":"{계약자가 볼 비밀번호 힌트}",  		
	      "password":"{설정할 문서 비밀번호}",
        "field_list": [{
      				"doc_id": "{ 서식 ID }",
      				"field_name": "{ 서식 필드명 }",
      				"field_value": "{ 서식 필드 값 }"
			  }]
      }],
    "comment": "",
    "enable_legal_agreement":"false"
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
| -1 | 실패 | 수신 메세지의 Body 정보가 잘못된 형태여서 파싱하지 못했습니다. |
| 10 | 실패 | 해당 Work Flow Library가 존재하지 않습니다. |
| 11 | 실패 | 실패하였습니다. |
| 12 | 실패 | 허용된 저장 용량이 초과되었습니다 |
| 13 | 실패 | 가능한 문서 수를 초과합니다. |
| 14 | 실패 | 이용기간이 만료되었습니다. |
| 15 | 실패 | 작성자 설정이 올바르지 않습니다. |

## 응답 Body 예시\)

```javascript
}
	"body":{
		"workflow_list":[{
			"workflow_id": "{문서ID}",
			"unset_player_email": "{서명자 이메일 or 전화번호}",
			"unset_player_name": "{서명자 이름}",
			"result": "OK",
			"description": "",
			"workflow_name": "{서식 이름}",
			"token": "{인증 토큰 코드}",
			"lang": "ko-KR",
			"reg_date": "{회사 결제 갱신일}"}],
			"comp_id": "{회사 ID}",
			"biz_id": "0",
			"memb_email": "{생성자 이메일}",
			"workflow_lib_id": "{서식 lib_id}"
			},
	"header":{
		"session_id": "thread_023",
		"response_code": "1410A",
		"result_code": "00",
		"result_msg": "Work Flow bulk Sending이 시작됩니다.",
		"version": "9.9.99"
	}
}
```

