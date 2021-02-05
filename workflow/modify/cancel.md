# 취소, 폐기, 삭제

* 문서를 취소 또는 폐기합니다.
* 취소 - 진행중인 문서를 취소 처리합니다.
* 폐기 - 완료된 문서를 폐기 처리합니다.
* 삭제 - 취소된 문서를 삭제 처리합니다. \( 문서란에서 보이지않게 삭제합니다. \)

## API 속성-

| Url | Type | **Code** |
| :--- | :--- | :--- |
| https://docs.esignon.net/JEDOC/Common.do | POST | 1510Q |

## Request

### Parameters

####  Headers

| **Parameter Name**                         | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| Content-Type | String | Required | "application/json" |
| Authorization | String | Required | "esignon ${발급받은토큰}" |

####   Body 

  Body - Header Parameter

| **Parameter Name**                         | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| request\_code | String | Required | "1510Q"\(API 고유 코드\) |
| request\_msg | String | Required | "" |
| request\_lang | String | Optional | "ko","en","ja" |
| session\_id | String | Required | "thread\_023" |
| version | String | Required | "9.9.99" |

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
      <td style="text-align:left">comp_id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Required</td>
      <td style="text-align:left">&#xD68C;&#xC0AC; ID</td>
    </tr>
    <tr>
      <td style="text-align:left">biz_id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Required</td>
      <td style="text-align:left">&quot;0&quot;</td>
    </tr>
    <tr>
      <td style="text-align:left">memb_email</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Required</td>
      <td style="text-align:left">&#xC0AC;&#xC6A9;&#xC790; &#xC774;&#xBA54;&#xC77C;</td>
    </tr>
    <tr>
      <td style="text-align:left">workflow_id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Required</td>
      <td style="text-align:left">&#xBB38;&#xC11C; ID</td>
    </tr>
    <tr>
      <td style="text-align:left">command</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Required</td>
      <td style="text-align:left">&quot;CANCEL&quot; - &#xCDE8;&#xC18C; / &quot;DISPOSAL&quot; - &#xD3D0;&#xAE30;
        / &quot;DELETE&quot; - &#xC0AD;&#xC81C;</td>
    </tr>
    <tr>
      <td style="text-align:left">description</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">&quot;disposal&quot; &#xC2DC;&#xC5D4; &#xD544;&#xC218; &#xAC12; - &quot;&#xD3D0;&#xAE30;
        &#xC0AC;&#xC720;&quot;</td>
    </tr>
    <tr>
      <td style="text-align:left">timezone_offset</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">
        <p>&quot;disposal&quot; &#xC2DC;&#xC5D4; &#xD544;&#xC218; &#xAC12; - &quot;UTC
          &#xC2DC;&#xAC04;&#xAC12; &#xC785;&#xB825;&quot;/&quot;+00:00&quot;</p>
        <p>&#xD55C;&#xAD6D;&#xC758; &#xACBD;&#xC6B0; &quot;+09:00&quot;</p>
      </td>
    </tr>
  </tbody>
</table>

## 요청 Body 예시\)

```javascript
{
	"header": {
			"request_code": "1510Q",
			"request_msg": "",
	    "request_lang":"{ko or ja or en}",
			"session_id": "session_id",
			"version": "9.9.99"
	},
	"body": {
			"comp_id": "{회사 ID}",
      "biz_id":"0",
      "memb_email":"{사용자 이메일}",
      "workflow_id":"{문서 ID}",
      "command":"{ CANCEL or DISPOSAL or DELETE }",
      "description":"{폐기 사유 입력}",
      "timezone_offset":"+09:00"
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
| 94 | 실패 | 인증키가 올바르지 않습니다. |
| 11 | 실패 | 필수 값이 없거나 상태 값이 올바르지 않습니다. |
| -1 | 실패 | 수신 메세지의 Body 정보가 잘못된 형태여서 파싱하지 못했습니다. |

## 응답 Body 예시\)

```javascript
{
	"header":{
		"session_id": "session_id",
		"response_code": "1510A",
		"result_code": "00",
		"result_msg": "폐기/취소를 성공했습니다.",
		"version": "9.9.99"
	},
	"body":{
		"comp_id": "{회사 ID}",
		"biz_id": "0",
		"memb_email": "{사용자 이메일}",
		"workflow_id": "{문서 ID}",
		"command": "{실행된 커맨드}"
	}
}
```



