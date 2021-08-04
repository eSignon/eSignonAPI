# 비대면 계약 시작

* 비대면 계약 서식을 시작합니다.
* export\_api 값을 따로 설정하여 받아올 값의 형식을 지정할 수 있습니다.\(선택사항\)
* export\_api 란 고객님이 진행중 승인, 반려를 할 경우 설정된 값을 설정된 URL로 esignon에서 request 해주는 기능입니다.
* ※ Body 파라미터 중 **Required 값은 필수 값이므로 입력하지 않으시면 요청에 실패합니다.** 또한, Optional 이지만 Array 타입의 파라미터를 사용하실 경우 Array 내부 파라미터 값 중 Required 값을 꼭 입력해주셔야 합니다. 사용을 하지 않으실 경우에 내부 파라미터를 입력하실 필요가 없습니다.
* ※ language 파리미터의 경우 기본값 "ko-KR" \( 설정 안했을경우 \)

## API 주소 정보 

| Url | Type | **Code** |
| :--- | :--- | :--- |
| https://docs.esignon.net/api/:companyId/startsimple | POST | 5005Q |

## Request

### Parameters

#### PathParameters

| **Parameter Name** | DataType | **Description** |
| :--- | :--- | :--- |
| :companyId | String | 회사아이디 |

####  Headers

| **Parameter Name**                         | DataType                                       **** | Required | **Description** |
| :--- | :--- | :--- | :--- |
| Content-Type | String | **Required** | "application/json" |
| Authorization | String | **Required** | "esignon ${발급받은토큰}"    |

####   Body 

  Body - Header Parameter

| **Parameter Name**                         | DataType                                              **** | Required | **Description** |
| :--- | :--- | :--- | :--- |
| request\_code | String | **Required** | "5005Q"\(API 고유 코드\) |
| version | String | **Required** | "9.9.99" |

  Body - Body Parameter

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Parameter Name</b>
      </th>
      <th style="text-align:left">DataType</th>
      <th style="text-align:left">Required</th>
      <th style="text-align:left"><b>Description</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">workflow_name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"><b>Required</b>
      </td>
      <td style="text-align:left">&#xBB38;&#xC11C;&#xBA85; ( &#xACC4;&#xC57D;&#xC11C; &#xC774;&#xB984; )</td>
    </tr>
    <tr>
      <td style="text-align:left">doc_id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"><b>Required</b>
      </td>
      <td style="text-align:left">&#xC2DC;&#xC791;&#xD560; &#xC11C;&#xC2DD; ID</td>
    </tr>
    <tr>
      <td style="text-align:left">memb_email</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"><b>Required</b>
      </td>
      <td style="text-align:left">&#xACC4;&#xC57D; &#xC2DC;&#xC791;&#xC790; &#xC774;&#xBA54;&#xC77C;</td>
    </tr>
    <tr>
      <td style="text-align:left">language</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">
        <p>&quot;ko-KR&quot;, &quot;en-US&quot;, &quot;ja-JP&quot;</p>
        <p>&#xC804;&#xB2EC;&#xD558;&#xB294; &#xBA54;&#xC77C; &#xBC0F; &#xD50C;&#xB808;&#xC774;&#xD654;&#xC758;
          &#xD45C;&#xAE30;&#xC5B8;&#xC5B4;</p>
        <p>&#xCE74;&#xD1A1;&#xC758; &#xACBD;&#xC6B0; &#xD55C;&#xAE00;&#xB9CC; &#xC81C;&#xACF5;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">comment</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">&#xC804;&#xB2EC;&#xBA54;&#xC2DC;&#xC9C0;</td>
    </tr>
    <tr>
      <td style="text-align:left">expireddate</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">
        <p>YYYY-MM-DD&#xD615;&#xC2DD;&#xC73C;&#xB85C; &#xC785;&#xB825;</p>
        <p>&#xBB38;&#xC11C;&#xC758; &#xC791;&#xC131;&#xAE30;&#xD55C; &#xC124;&#xC815;</p>
        <p>&#xB144; - &#xC6D4; - &#xC77C;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">preview</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">
        <p>&quot;preview&quot; - &#xC785;&#xB825;&#xAC12; &#xACE0;&#xC815;</p>
        <p>&#xC635;&#xC158; &#xC124;&#xC815;&#xC2DC; &#xBE44;&#xB300;&#xBA74; &#xACC4;&#xC57D;</p>
        <p>&#xC2DC;&#xC791;&#xC774; &#xC544;&#xB2CC; &#xBBF8;&#xB9AC;&#xBCF4;&#xAE30;URL</p>
        <p>&#xC774; &#xC81C;&#xACF5;&#xB429;&#xB2C8;&#xB2E4;.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">player_list</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left"><b>Required</b>
      </td>
      <td style="text-align:left">&#xC11C;&#xBA85;&#xD558;&#xB294; &#xACE0;&#xAC1D;&#xC758; &#xC815;&#xBCF4;&#xB97C;
        &#xC785;&#xB825; &#xC11C;&#xC2DD;&#xC758; &#xB2E8;&#xACC4;&#xC5D0; &#xB9DE;&#xCDB0;&#xC11C;
        &#xC791;&#xC131; &#xD544;&#xC218;</td>
    </tr>
    <tr>
      <td style="text-align:left">player_list.email</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"><b>Required</b>
      </td>
      <td style="text-align:left">&#xC774;&#xBA54;&#xC77C; or &#xC804;&#xD654;&#xBC88;&#xD638;</td>
    </tr>
    <tr>
      <td style="text-align:left">player_list.name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"><b>Required</b>
      </td>
      <td style="text-align:left">&#xACC4;&#xC57D; &#xC9C4;&#xD589;&#xC790; &#xC774;&#xB984;</td>
    </tr>
    <tr>
      <td style="text-align:left">player_list.mobile_number</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">&#xBCF8;&#xC778;&#xC778;&#xC99D;&#xC5D0; &#xC0AC;&#xC6A9;&#xD560; &#xBC88;&#xD638;</td>
    </tr>
    <tr>
      <td style="text-align:left">player_list.password_hint</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">&#xACC4;&#xC57D; &#xC9C4;&#xD589;&#xC2DC; &#xC0AC;&#xC6A9;&#xD560; &#xBE44;&#xBC00;&#xBC88;&#xD638;
        &#xD78C;&#xD2B8;</td>
    </tr>
    <tr>
      <td style="text-align:left">player_list.password</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">&#xACC4;&#xC57D; &#xC9C4;&#xD589;&#xC2DC; &#xC0AC;&#xC6A9;&#xD560; &#xBE44;&#xBC00;&#xBC88;&#xD638;</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">field_list</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">&#xBBF8;&#xB9AC; &#xC785;&#xB825;&#xD560; &#xAC12;&#xC774; &#xC788;&#xC744;
        &#xACBD;&#xC6B0; &#xCD94;&#xAC00;&#xD558;&#xB294; &#xAC12; RadioBox,CheckBox,LabelBox
        ,TextBox,DatePickerBox &#xB9CC; &#xBBF8;&#xB9AC; &#xAC12; &#xC785;&#xB825;&#xAC00;&#xB2A5;</td>
    </tr>
    <tr>
      <td style="text-align:left">field_list.field_name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">&#xC11C;&#xC2DD; &#xD544;&#xB4DC; &#xC774;&#xB984;</td>
    </tr>
    <tr>
      <td style="text-align:left">field_list.field_value</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">
        <p>&#xC11C;&#xC2DD; &#xD544;&#xB4DC; &#xAC12; Radio,Check Box &#xC758; &#xACBD;&#xC6B0;
          &#xAC12;&#xC744; (&#x201C;N&#x201D; or &#x201D;Y&#x201D;) &#xB85C; &#xC218;&#xC2E0;
          Label,Text Box &#xC758; &#xACBD;&#xC6B0; &#xD14D;&#xC2A4;&#xD2B8; &#xAC12;&#xC744;
          &#xADF8;&#xB300;&#xB85C; &#xC218;&#xC2E0;</p>
        <p>DatePickerBox ( &#xB0A0;&#xC9DC;&#xBC15;&#xC2A4; )</p>
        <p>&#xC758; &#xACBD;&#xC6B0; YYYY-MM-DD &#xD615;&#xD0DC;&#xB85C;&#xC785;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">&#xC791;&#xC131; &#xB370;&#xC774;&#xD130;&#xB97C; &#xB0B4;&#xBCF4;&#xB0BC;&#xC2DC;&#xC5D0;
        &#xC124;&#xC815;&#xD558;&#xB294; &#xAC12;</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.api_type</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"><em><b>Required</b></em>
      </td>
      <td style="text-align:left">&quot;StartAndEnd&quot;(&#xC2DC;&#xC791;&#xACFC; &#xB05D;&#xB9CC;) or
        &quot;ALL&quot; (&#xC804;&#xBD80;)</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.url</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"><em><b>Required</b></em>
      </td>
      <td style="text-align:left">&#xD1B5;&#xC2E0; &#xBC1B;&#xC744; url</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.link_type</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">embed &#xC804;&#xC6A9;&#xC635;&#xC158;
        <br />&#xBB38;&#xC11C; &#xC644;&#xB8CC; &#xC2DC; &#xC774;&#xB825;&#xC778;&#xC99D;&#xC11C;,
        <br
        />PDF &#xBB38;&#xC11C; URL&#xC758; type&#xC744; &#xBCC0;&#xACBD;
        <br />default - viewer URL
        <br />&quot;download&quot; - download URL</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.request_code</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">&#xACE0;&#xAC1D;&#xC774; &#xC815;&#xC758;&#xD558;&#xB294; &#xC784;&#xC758;&#xC758;
        &#xAC12; or &quot;embed&quot;( ExportAPI &#xC124;&#xBA85; &#xCC38;&#xC870;)</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.authorization</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">
        <p>&#xB370;&#xC774;&#xD130;&#xB97C; &#xC218;&#xC2E0;&#xBC1B;&#xC744;&#xB54C;
          &#xD5E4;&#xB354; authorization &#xB85C; &#xC124;&#xC815;&#xD558;&#xACE0;
          &#xC2F6;&#xC740; &#xAC12;</p>
        <p>(&#xC218;&#xC2E0;&#xCE21;&#xC5D0;&#xC11C; &#xC554;&#xD638;&#xD1A0;&#xD070;&#xC744;
          &#xBC1B;&#xC544;&#xC11C; &#xBCF4;&#xC548;&#xC0C1; &#xD65C;&#xC6A9;&#xD558;&#xACE0;
          &#xC2F6;&#xC73C;&#xC2E0;&#xACBD;&#xC6B0;)</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.request_params</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">&#xBB38;&#xC11C;&#xB0B4;&#xBD80;&#xC5D0; &#xD2B9;&#xC815; &#xAC12;&#xC744;
        &#xBC1B;&#xC544; &#xC624;&#xACE0;&#xC2F6;&#xC744;&#xB54C; &#xC0AC;&#xC6A9;</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.request_params.param_id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"><em><b>Required</b></em>
      </td>
      <td style="text-align:left">&#xBC1B;&#xC544;&#xC62C; &#xD30C;&#xB77C;&#xBBF8;&#xD130; &#xC774;&#xB984;(&#xC0AC;&#xC6A9;&#xC790;
        &#xC9C0;&#xC815;)</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.request_params.param_value</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"><em><b>Required</b></em>
      </td>
      <td style="text-align:left">request_params.fields&#xC5D0;&#xC11C; &#xBC1B;&#xC544;&#xC62C; &#xAC12;&#xC774;
        &#xBB38;&#xC11C;&#xC5D0; &#xC5C6;&#xB294;&#xACBD;&#xC6B0; &#xBC1B;&#xC544;&#xC62C;
        &#xAE30;&#xBCF8; &#xAC12;</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.request_params.fields</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left"><em><b>Required</b></em>
      </td>
      <td style="text-align:left">&#xC11C;&#xC2DD; &#xB0B4;&#xBD80;&#xC5D0; &#xC788;&#xB294; &#xD544;&#xB4DC;&#xBA85;&#xC744;
        &#xC870;&#xD68C;&#xD558;&#xC5EC; &#xD544;&#xB4DC;&#xC774;&#xB984;&#xC5D0;
        &#xD574;&#xB2F9;&#xD558;&#xB294; &#xAC12;&#xC774; &#xBB38;&#xC11C;&#xC5D0;
        &#xC874;&#xC7AC;&#xD560; &#xACBD;&#xC6B0; request_params.param_value &#xB300;&#xC2E0;&#xC5D0;
        &#xB4E4;&#xC5B4;&#xAC00;&#xB294; &#xAC12;</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.request_params.fields.doc_id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"><em><b>Required</b></em>
      </td>
      <td style="text-align:left">&#xC11C;&#xC2DD; ID</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.request_params.fields.field_name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"><em><b>Required</b></em>
      </td>
      <td style="text-align:left">&#xAC12;&#xC744; &#xAC00;&#xC838;&#xC62C; &#xC11C;&#xC2DD; &#xB0B4; &#xD544;&#xB4DC;
        &#xBA85;</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">customer_list</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">&#xCC38;&#xC870;&#xC790;&#xAC00; &#xC788;&#xC744; &#xACBD;&#xC6B0; &#xCD94;&#xAC00;</td>
    </tr>
    <tr>
      <td style="text-align:left">customer_list.email</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"><em><b>Required</b></em>
      </td>
      <td style="text-align:left">&#xC774;&#xBA54;&#xC77C; or &#xD734;&#xB300;&#xD3F0;&#xBC88;&#xD638;</td>
    </tr>
    <tr>
      <td style="text-align:left">customer_list.name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"><em><b>Required</b></em>
      </td>
      <td style="text-align:left">&#xCC38;&#xC870;&#xC790; &#xC774;&#xB984;</td>
    </tr>
    <tr>
      <td style="text-align:left">customer_list.language</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">&quot;ko-KR&quot;, &quot;en-US&quot;, &quot;ja-JP&quot;</td>
    </tr>
  </tbody>
</table>

## Request Body Example

```javascript
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
		"expireddate": "YYYY-MM-DD",
		"player_list": [{
			"field_owner": "1",
			"email": "{ 받는 사람 email or 받는 사람 휴대폰 번호 }",
      "name":"{ 받는 사람 이름 }",
			"mobile_number": "{ 휴대폰 본인인증시 사용할 휴대폰번호 }",
      "password_hint":"{ 비밀번호 힌트 }",
      "password":"{비밀번호}"
		},{
			"field_owner": "2",
			"email": "{}",
      "name":"{}",
			"mobile_number": "{}",
      "password_hint":"{}",
      "password":"{}"
		}],
		"field_list": [{
				"field_name": "{ field_name }", 
				"field_value": "{ field_value }"
			}
		],
		"customer_list": [{
				"email": "{ id_type에 따라서 참조자 이메일 or 휴대폰번호 }",
	      "name":"{ 참조자 이름 }"
		}],
		"export_api_info": {
				"api_type": "{ StartAndEnd or ALL }",
				"url": "{ 통신 받을 url }",
				"link_type": "{download or null}",
				"request_code": "{ 고객이 정의하는 임의 값 }",
				"authorization": "{설정 URL로 request 시에 Header - authorization 으로 받아올 값 }",
	      "request_params": [{
								"param_id": "{받아올 파라미터 이름(사용자 지정)}",
								"param_value": "{fields에서 설정한 값이 없을 경우 받아올 기본 값}",
								"fields": [{ 
                            "doc_id":"{ 서식 ID }",
                            "field_name":"{ 값을 가져올 서식 내 필드명 }" 
          			}]
				}]
	   }
	}
}
```

**request\_params**   
서식에 field\_name으로 등록한 필드 박스의 값이 없을경우 param\_id:param\_value return   
값이 있을경우엔 param\_id:field\_value를 return

## Request Body Example - only Required

```javascript
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

```javascript
{
	"header": {
		"request_code": "5005Q",
		"version": "9.9.99"
	},
	"body": {
		"biz_id": "0",
		"memb_email": "guide@esignon.net",
		"language": "ko-KR",
		"comment": "",
		"workflow_name": "TEST-NAME",
		"doc_id": "1",
		"player_list": [{
				"field_owner": "1",
				"email": "guide@esignon.net",
				"name": "TEST"
			},
			{
				"field_owner": "2",
				"email": "guide@esignon.net",
				"name": "TEST"
			}
		],
		"field_list": [{
			"field_name": "name",
			"field_value": "name-value"
		}],
		"customer_list": [{
			"email": "guide@esignon.net",
			"name": "TEST"
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

<table>
  <thead>
    <tr>
      <th style="text-align:left">Code</th>
      <th style="text-align:left"><b>Description</b>
      </th>
      <th style="text-align:left"><b>Reference</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">00</td>
      <td style="text-align:left">&#xC131;&#xACF5;</td>
      <td style="text-align:left">&#xC131;&#xACF5;</td>
    </tr>
    <tr>
      <td style="text-align:left">-1</td>
      <td style="text-align:left">&#xC2E4;&#xD328;</td>
      <td style="text-align:left">
        <p>&#xBB38;&#xC11C;&#xBA85;&#xC740; 1~128&#xC790;&#xB85C; &#xC785;&#xB825;&#xD574;&#xC8FC;&#xC138;&#xC694;.
          <br
          />timezone_offset&#xC758; &#xD615;&#xC2DD;&#xC774; &#xC798;&#xBABB;&#xB418;&#xC5C8;&#xC2B5;&#xB2C8;&#xB2E4;.
          // ( +XX:XX or -XX:XX ) &#xD615;&#xC2DD;
          <br />&#xBB38;&#xC11C;&#xC774;&#xB984;&#xC5D0; &#xD2B9;&#xC218;&#xBB38;&#xC790;&#xB97C;
          &#xD3EC;&#xD568;&#xD560; &#xC218; &#xC5C6;&#xC2B5;&#xB2C8;&#xB2E4;.(\&apos;,
          \&quot;, \\, /, :, |, &lt;, &gt;, <em>. ?) <br />&#xC774;&#xB984;&#xC5D0; &#xD2B9;&#xC218;&#xBB38;&#xC790;&#xB97C; &#xD3EC;&#xD568;&#xD560; &#xC218; &#xC5C6;&#xC2B5;&#xB2C8;&#xB2E4;.(\&apos;, \&quot;, \\, /, :, |, &lt;, &gt;, </em>.
          ?)
          <br />&#xD734;&#xB300;&#xD3F0; &#xD615;&#xC2DD;&#xC774; &#xB9DE;&#xC9C0; &#xC54A;&#xC2B5;&#xB2C8;&#xB2E4;.
          ( - &#xC720;&#xBB34; &#xC0C1;&#xAD00;&#xC5C6;&#xC74C; )
          <br />&#xC774;&#xBA54;&#xC77C; &#xD615;&#xC2DD;&#xC774; &#xB9DE;&#xC9C0; &#xC54A;&#xC2B5;&#xB2C8;&#xB2E4;.
          <br
          />&#xD734;&#xB300;&#xD3F0; &#xBCF8;&#xC778;&#xC778;&#xC99D; &#xC694;&#xCCAD;
          &#xC0DD;&#xB144;&#xC6D4;&#xC77C;&#xC758; &#xB0A0;&#xC9DC;&#xAC00; &#xC801;&#xD569;&#xD558;&#xC9C0;
          &#xC54A;&#xC2B5;&#xB2C8;&#xB2E4;. 8&#xC790;&#xB9AC;&#xB85C; &#xC785;&#xB825;&#xD574;&#xC8FC;&#xC138;&#xC694;.(ex.20200120)(&#xC694;&#xCCAD;
          &#xC0DD;&#xB144;&#xC6D4;&#xC77C; :**** )</p>
        <p>&#xBE44;&#xBC00;&#xBC88;&#xD638;&#xC5D0; &#xD55C;&#xAE00;&#xC740; &#xC785;&#xB825;&#xD560;
          &#xC218; &#xC5C6;&#xC2B5;&#xB2C8;&#xB2E4;.</p>
        <p>&#xBE44;&#xBC00;&#xBC88;&#xD638;&#xC5D0; &#xD2B9;&#xC218;&#xBB38;&#xC790;[\&apos;
          \&quot; \]&#xB97C; &#xC785;&#xB825;&#xD560; &#xC218; &#xC5C6;&#xC2B5;&#xB2C8;&#xB2E4;.</p>
        <p>&#xBE44;&#xBC00;&#xBC88;&#xD638;&#xC778;&#xC99D; &#xBE44;&#xBC00;&#xBC88;&#xD638;(password)&#xB294;
          4~15&#xC790;&#xB85C; &#xC785;&#xB825;&#xD574;&#xC8FC;&#xC138;&#xC694;.</p>
        <p>&#xBE44;&#xBC00;&#xBC88;&#xD638;&#xC778;&#xC99D; &#xD78C;&#xD2B8;&#xB294;
          50&#xC790; &#xC774;&#xD558;&#xB85C; &#xC785;&#xB825;&#xD574;&#xC8FC;&#xC138;&#xC694;.</p>
        <p>&#xBA54;&#xC138;&#xC9C0; &#xAE00;&#xC790;&#xC218;&#xB97C; &#xCD08;&#xACFC;&#xD588;&#xC2B5;&#xB2C8;&#xB2E4;.(250&#xC790;
          &#xC81C;&#xD55C;)</p>
        <p>player_list&#xC758; name &#xAC12;&#xC740; &#xD544;&#xC218;&#xB85C; &#xC785;&#xB825;&#xD558;&#xC154;&#xC57C;
          &#xD569;&#xB2C8;&#xB2E4;.</p>
        <p>&#xC2DC;&#xC791;&#xD558;&#xB294; &#xC0AC;&#xB78C;(memb_email:***)&#xC740;
          &#xD68C;&#xC0AC;&#xC5D0; &#xAC00;&#xC785;&#xB41C; &#xC0AC;&#xB78C;&#xC774;&#xC5EC;&#xC57C;
          &#xD569;&#xB2C8;&#xB2E4;.</p>
        <p>&#xC874;&#xC7AC;&#xD558;&#xC9C0; &#xC54A;&#xB294; &#xC11C;&#xC2DD;&#xC785;&#xB2C8;&#xB2E4;.</p>
        <p>(&#xC11C;&#xC2DD;&#xC544;&#xC774;&#xB514;:**) &#xC11C;&#xC2DD;&#xC5D0;
          &#xC791;&#xC131;&#xC790;&#xAC00; &#xC124;&#xC815;&#xB418;&#xC9C0; &#xC54A;&#xC558;&#xC2B5;&#xB2C8;&#xB2E4;.</p>
        <p>&#xC11C;&#xC2DD;&#xBA54;&#xB274;&#xC5D0;&#xC11C; &#xD574;&#xB2F9; &#xC11C;&#xC2DD;&#xC758;
          &#xBB38;&#xC11C; &#xC791;&#xC131;&#xC790;&#xB97C; &#xC9C0;&#xC815;&#xD574;&#xC8FC;&#xC138;&#xC694;.(&#xC11C;&#xC2DD;&#xC544;&#xC774;&#xB514;:**)</p>
        <p>&#xC124;&#xC815;&#xD55C; &#xBB38;&#xC11C;&#xC791;&#xC131;&#xC790; &#xC218;(
          * <em>)&#xC640; &#xC11C;&#xC2DD;&#xC758; &#xBB38;&#xC11C;&#xC791;&#xC131;&#xC790; &#xC218;( * </em>)&#xAC00;
          &#xC77C;&#xCE58;&#xD558;&#xC9C0; &#xC54A;&#xC2B5;&#xB2C8;&#xB2E4;.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">10</td>
      <td style="text-align:left">&#xC2E4;&#xD328;</td>
      <td style="text-align:left">&#xC2E4;&#xD328;</td>
    </tr>
    <tr>
      <td style="text-align:left">11</td>
      <td style="text-align:left">&#xC2E4;&#xD328;</td>
      <td style="text-align:left">&#xC218;&#xC2E0; &#xBA54;&#xC138;&#xC9C0;&#xC758; Body &#xC815;&#xBCF4;&#xAC00;
        &#xC798;&#xBABB;&#xB41C; &#xD615;&#xD0DC;&#xC5EC;&#xC11C; &#xD30C;&#xC2F1;&#xD558;&#xC9C0;
        &#xBABB;&#xD588;&#xC2B5;&#xB2C8;&#xB2E4;.</td>
    </tr>
    <tr>
      <td style="text-align:left">12</td>
      <td style="text-align:left">&#xC2E4;</td>
      <td style="text-align:left">eSignon &#xC11C;&#xBE44;&#xC2A4; &#xC774;&#xC6A9;&#xAE30;&#xAC04;&#xC774;
        &#xB9CC;&#xB8CC;&#xB418;&#xC5C8;&#xC2B5;&#xB2C8;&#xB2E4;. &#xACE0;&#xAC1D;&#xC9C0;&#xC6D0;&#xC13C;&#xD130;&#xB85C;
        &#xC5F0;&#xB77D;&#xBD80;&#xD0C1;&#xB4DC;&#xB9BD;&#xB2C8;&#xB2E4;.(02-6299-5926)</td>
    </tr>
    <tr>
      <td style="text-align:left">13</td>
      <td style="text-align:left">&#xC2E4;</td>
      <td style="text-align:left">eSignon &#xC11C;&#xBE44;&#xC2A4; &#xC0AC;&#xC6A9;&#xAC74;&#xC218;&#xAC00;
        &#xCD08;&#xACFC;&#xB418;&#xC5C8;&#xC2B5;&#xB2C8;&#xB2E4;. &#xACE0;&#xAC1D;&#xC9C0;&#xC6D0;&#xC13C;&#xD130;&#xB85C;
        &#xC5F0;&#xB77D;&#xBD80;&#xD0C1;&#xB4DC;&#xB9BD;&#xB2C8;&#xB2E4;.(02-6299-5926)</td>
    </tr>
    <tr>
      <td style="text-align:left">19</td>
      <td style="text-align:left">&#xC2E4;</td>
      <td style="text-align:left">&#xB0A0;&#xC9DC;&#xD615;&#xC2DD;&#xC774; &#xC798;&#xBABB;&#xB418;&#xC5C8;&#xC2B5;&#xB2C8;&#xB2E4;.
        ( &#xB9CC;&#xB8CC;&#xC77C; &#xC124;&#xC815; )</td>
    </tr>
    <tr>
      <td style="text-align:left">20</td>
      <td style="text-align:left">&#xC2E4;</td>
      <td style="text-align:left">&#xC9C0;&#xB09C; &#xB0A0;&#xC9DC;&#xB97C; &#xB9CC;&#xB8CC;&#xC77C;&#xB85C;
        &#xC124;&#xC815;&#xD560; &#xC218; &#xC5C6;&#xC2B5;&#xB2C8;&#xB2E4;.</td>
    </tr>
    <tr>
      <td style="text-align:left">99</td>
      <td style="text-align:left">&#xC2E4;&#xD328;</td>
      <td style="text-align:left">Unexpected exception ( &#xC798;&#xBABB;&#xB41C; &#xD3EC;&#xB9F7; )</td>
    </tr>
  </tbody>
</table>

## Response Body Example

```javascript
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
   "lang": "ko-KR" }
}
```

Response 로 수신한 토큰을 https://docs.esignon.net/mail/sign?token=:token 경로에 token 값을 입력  
한뒤 접근하면 진행중인 계약서에 접근할 수 있습니다.   
\( 생성자 기준으로 발급되는 token 입니다. 생성자가 만약 계약 단계에 있을경우 해당 URL로 서명이 가능  
그 외의 경우에는 해당 URL로 진행중인 문서 확인이 가능합니다.  \) 

## Response export\_api Example

```javascript
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

## Response Body Example \( Preview \)

```javascript
{
	"header": {
		"response_code": "5005A",
		"result_code": "00",
		"result_msg": "success (preview url)",
		"version": "9.9.99"
	},
	"body": {
		"preview_url": "미리보기 URL"
	}
}
```

preview 옵션 설정시 Response로 비대면 계약 시작이 아닌 미리보기 URL이 제공됩니다. 

