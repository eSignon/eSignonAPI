# 비대면 계약 - ExportAPI 설명

ExportAPI 란 비대면 계약시작시 export\_api\_info Parameter 값을 통하여 설정한 정보를 기반으로               계약자가 계약서를 승인, 반려시에 설정 값을 기반으로 만들어진 JSON 형식의 body 를 설정한 URL에 export 하여 해당 회사측에서 받을 수 있게 해주는 기능입니다.

request\_code 에 사용자 정의 대신 "embed" 를 입력 할 경우 계약서 진행 URL을 export 해주며 카카오톡 및 이메일 알림이 계약자에게 발송되지 않습니다. export 받은 URL을 기반으로 고객측에서 발송을 따로               진행 할 수 있습니다.  

embed Code를 사용 할 경우 최초 비대면 계약 호출시 response로 계약 시작 URL을 제공하며 계약을         진행 시 서명자가 계약서를 승인, 반려 할 때마다 export 로 진행 URL 과 입력하셨던 계약자의  번호  또는   이메일을 제공합니다. \( 이메일로 호출한 경우 이메일, 번호로 호출한 경우 번호 \) 계약 완료시엔                   문서 다운로드가 가능하도록 문서 다운로드, 이력 인증서 다운로드 URL을 제공합니다.   
※ 계약 완료시 받을수 있는 URL 형식은 link\_type 옵션으 viewer, download 중 하나로 선택가능합니다.

## Parameter 

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Parameter Name                        </b>
      </th>
      <th style="text-align:left">DataType</th>
      <th style="text-align:left"><b>Description</b>
      </th>
    </tr>
  </thead>
  <tbody>
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
      <td style="text-align:left">export_api_info.link_type</td>
      <td style="text-align:left">String</td>
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
      <td style="text-align:left">
        <p>&#xACE0;&#xAC1D;&#xC774; &#xC815;&#xC758;&#xD558;&#xB294; &#xC784;&#xC758;&#xC758;
          &#xAC12;</p>
        <p>&quot;embed&quot; - &#xC124;&#xBA85; &#xCC38;&#xC870;</p>
      </td>
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
      <td style="text-align:left">&#xBC1B;&#xC544;&#xC62C; &#xD30C;&#xB77C;&#xBBF8;&#xD130; &#xC774;&#xB984;(&#xC0AC;&#xC6A9;&#xC790;
        &#xC9C0;&#xC815;)</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.request_params.param_value</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&quot;&quot;</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.request_params.fields</td>
      <td style="text-align:left">Data</td>
      <td style="text-align:left">&#xC11C;&#xC2DD; &#xB0B4;&#xBD80;&#xC5D0; &#xC788;&#xB294; &#xD544;&#xB4DC;&#xBA85;&#xC744;
        &#xC870;&#xD68C;&#xD558;&#xC5EC; &#xD544;&#xB4DC;&#xC774;&#xB984;&#xC5D0;
        &#xD574;&#xB2F9;&#xD558;&#xB294; &#xAC12;&#xC774; &#xBB38;&#xC11C;&#xC5D0;
        &#xC874;&#xC7AC;&#xD560; &#xACBD;&#xC6B0; param_value &#xB300;&#xC2E0;&#xC5D0;
        &#xB4E4;&#xC5B4;&#xAC00;&#xB294; &#xAC12;</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.request_params.fields.doc_id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xC11C;&#xC2DD; ID</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.request_params.fields.field_name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xAC12;&#xC744; &#xAC00;&#xC838;&#xC62C; &#xC11C;&#xC2DD; &#xB0B4; &#xD544;&#xB4DC;
        &#xBA85;</td>
    </tr>
  </tbody>
</table>

## export\_api Response\) 

```javascript
{
	"header": {
		"api_name": "export",
		"session_id": "S1001",
		"request_code": "{ exportAPI_info 에서 지정한 request_code 값 }"
	},
	"body": {
		"wfluid": "0", //이싸인온에서 사용하는 서식구분id
		"clientid": "{ eSignonAPI 사용을 위한 Unique ID }",
		"processid": "1", //이싸인온에서 사용하는 process 구분값
		"requestid": "{ header 의 request_code 값 }",
		"actionid": "1", //이싸인온에서 사용하는 action 구분값
		"workdatetime": "2020-01-31 04:23:28.0", //작성완료시간
		"worktype": "CF", //CF=승인, RT=반려 작성자가 2단계 이상의 문서에서는 승인, 반려를 선택할 수 있음.
		"wfuid": "{}", //이싸인온에서 사용하는 문서구분id
		"useremail": "{ 서명자 이메일or휴대폰번호 }", 
		"opinion": "", //승인, 반려시 고객들이 반려 메세지,전송 메세지를 사용한 경우 출력
		"param_id": "param_value", // 서식에 field_name으로 등록한 필드 박스의 값이 없을경우 param_id:param_value return  
															 //	값이 있을경우엔 param_id:field_value를 return
		"status":"{Playing}", // 진행 상태 - Playing 진행중 / Complete 완료 / Canceled 취소됨
	}
}
```

## export\_api 응답 예시\) code-embed 상태 일 때 \( 진행중 \)

```javascript
{
	"header": {
		"api_name": "export",
		"session_id": "S1001",
		"request_code": "{embed로 고정}"
	},
	"body": {
		"wfluid": "0", //이싸인온에서 사용하는 서식구분id
		"clientid": "{ eSignonAPI 사용을 위한 Unique ID }",
		"processid": "1", //이싸인온에서 사용하는 process 구분값
		"requestid": "{ embed로 고정 }",
		"actionid": "1", //이싸인온에서 사용하는 action 구분값
		"workdatetime": "2020-01-31 04:23:28.0", //작성완료시간
		"worktype": "CF", //CF=승인, RT=반려 작성자가 2단계 이상의 문서에서는 승인, 반려를 선택할 수 있음.
		"wfuid": "{}", //이싸인온에서 사용하는 문서구분id
		"useremail": "{ 서명자 이메일or휴대폰번호 }", 
		"opinion": "", //승인, 반려시 고객들이 반려 메세지,전송 메세지를 사용한 경우 출력
		"param_id": "param_value", // fields 값을 설정한 경우 fields_value를 return
		"next_play_user":"{다음 차례로 서명할 이메일 or 휴대폰 번호}",
		"play_url":"{다음 차례로 서명할 고객에게 전달할 URL}",
		"status":"{Playing}", // 진행 상태 - Playing 진행중 / Complete 완료 / Canceled 취소됨
		"next_user_name":"{다음 서명자 이름}",
		"user_name":"{현재 서명자 이름}"
	}
}
```

## export\_api 응답 예시\) code-embed 상태 일 때 \( 완료 \)

```javascript
{
	"header": {
		"api_name": "export",
		"session_id": "S1001",
		"request_code": "{embed로 고정}"
	},
	"body": {
		"wfluid": "0", //이싸인온에서 사용하는 서식구분id
		"clientid": "{ eSignonAPI 사용을 위한 Unique ID }",
		"processid": "1", //이싸인온에서 사용하는 process 구분값
		"requestid": "{ embed로 고정 }",
		"actionid": "1", //이싸인온에서 사용하는 action 구분값
		"workdatetime": "2020-01-31 04:23:28.0", //작성완료시간
		"worktype": "CF", //CF=승인, RT=반려 작성자가 2단계 이상의 문서에서는 승인, 반려를 선택할 수 있음.
		"wfuid": "{}", //이싸인온에서 사용하는 문서구분id
		"useremail": "{ 서명자 이메일or휴대폰번호 }", 
		"opinion": "", //승인, 반려시 고객들이 반려 메세지,전송 메세지를 사용한 경우 출력
		"param_id": "param_value", // fields 값을 설정한 경우 fields_value를 return
		"cert_url":"{이력 인증서 다운로드 URL}", // link_type 옵션으로 URL 종류 선택가능
		"download_url":"{문서 다운로드 URL}", // link_type 옵션으로 URL 종류 선택가능
		"status":"{Complete}", // 진행 상태 - Playing 진행중 / Complete 완료 / Canceled 취소됨
		"user_name":"{현재 서명자 이름}"
	}
}
```

