# 기간으로 조회

* 특정 서식으로 작성한 문서를 기간으로 조회합니다.

## API 속성-

| Url | Type | **Code** |
| :--- | :--- | :--- |
| https://docs.esignon.net/api/{CompID}/search | POST | 5009Q |

## Request

### Parameters

#### PathParameters

| **Parameter Name** | DataType | **Description** |
| :--- | :--- | :--- |
| CompID | String | 회사ID |

####  Headers

| **Parameter Name**                         | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| Content-Type | String | Required | "application/json" |
| Authorization | String | Required | "esignon 발급받은 Token" |

####   Body 

  Body - Header Parameter

| **Parameter Name**                         | DataType | Required | **Description** |
| :--- | :--- | :--- | :--- |
| request\_code | String | Required | "5009Q"\(API 고유 코드\) |
| api\_name | String | Required | "start api" |
| session\_id | String | Required | "" |
| version | String | Required | "1.1.60" |

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
      <td style="text-align:left">client_id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Required</td>
      <td style="text-align:left">esignon &#xC5D0;&#xC11C; &#xBC1C;&#xAE09;&#xBC1B;&#xC740; ID ( &#xBC1C;&#xAE09;&#xC740;
        &#xBB38;&#xC758; )</td>
    </tr>
    <tr>
      <td style="text-align:left">search_date_type</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">START or END / START &#x2013; &#xBB38;&#xC11C; &#xC2DC;&#xC791; &#xAE30;&#xC900;
        / END &#x2013; &#xBB38;&#xC11C; &#xC644;&#xB8CC; &#xAE30;&#xC900; - &#xBBF8;
        &#xC785;&#xB825;&#xC2DC; &#xB514;&#xD3F4;&#xD2B8;&#xAC12; &quot;END&quot;</td>
    </tr>
    <tr>
      <td style="text-align:left">start_date</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Required</td>
      <td style="text-align:left">&#xAC80;&#xC0C9; &#xC2DC;&#xC791; &#xC9C0;&#xC810; YYYY-MM-DD</td>
    </tr>
    <tr>
      <td style="text-align:left">end_date</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Required</td>
      <td style="text-align:left">&#xAC80;&#xC0C9; &#xC885;&#xB8CC; &#xC9C0;&#xC810; YYYY-MM-DD</td>
    </tr>
    <tr>
      <td style="text-align:left">field_list</td>
      <td style="text-align:left">Data</td>
      <td style="text-align:left">Required</td>
      <td style="text-align:left">&#xC870;&#xD68C;&#xD560; &#xBB38;&#xC11C; &#xC815;&#xBCF4;</td>
    </tr>
    <tr>
      <td style="text-align:left">field_list.doc_uid</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Required</td>
      <td style="text-align:left">&#xC870;&#xD68C;&#xD560; &#xBB38;&#xC11C;&#xC758; &#xC11C;&#xC2DD; ID</td>
    </tr>
    <tr>
      <td style="text-align:left">field_list.field_name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">
        <p>&#xC870;&#xD68C;&#xD560; &#xBB38;&#xC11C; &#xC11C;&#xC2DD;&#xC758; &#xD544;&#xB4DC;
          &#xC774;&#xB984;</p>
        <p>- &#xC785;&#xB825;&#xC2DC; &#xD574;&#xB2F9; &#xD544;&#xB4DC; &#xC774;&#xB984;&#xACFC;
          &#xAC19;&#xC740; &#xD544;&#xB4DC;&#xC758; &#xAC12;&#xC744; &#xAC00;&#xC838;&#xC635;&#xB2C8;&#xB2E4;.</p>
      </td>
    </tr>
  </tbody>
</table>

## 요청 Body 예시\)

```javascript
{
 "header" : {
   "request_code" : "5009Q",
   "api_name" : "start api",
   "session_id" : "",
   "version" : "1.1.60"
 },
   "body" : {
     "comp_id": "{회사 ID}",
     "client_id": "{발급받은 클라이언트 ID}",
     "search_date_type":"{START or END}",
     "start_date": "{검색 시작 지점}",
     "end_date": "{검색 종료 지점}",
     "field_list": [{
  				"doc_uid": "{서식 ID}",
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

```javascript
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

### Parameter Info

| **Name**                         | **Value**                                                 | **Description** |
| :--- | :--- | :--- |
| wf\_list.wf\_status | Playing | 진행중 |
|  | Canceled | 취소 |
|  | Complete | 완료 |
|  | Disposal | 폐기 |
|  | Truncate | \(취소 상태 후 삭제한 경우\) |

