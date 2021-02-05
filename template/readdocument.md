# 목록조회

* 서식 목록을 조회합니다.

## API 속성-

| Url | Type | **Code** |
| :--- | :--- | :--- |
| https://docs.esignon.net/JEDOC/Common.do?lang={value} | POST | 1123Q |

## Request

### Parameters

#### PathParameters

| **Parameter Name** | DataType | **Description** |
| :--- | :--- | :--- |
| lang | String | ko,en,jp |

####  Headers

| **Parameter Name**                         | DataType | **Description** |
| :--- | :--- | :--- |
| Content-Type | String | "application/json" |
| Authorization | String | "esignon ${발급받은토큰}" |

####   Body 

  Body - Header Parameter

| **Parameter Name**                         | DataType | **Description** |
| :--- | :--- | :--- |
| request\_code | String | "1123Q"\(API 고유 코드\) |
| request\_msg | String | "" |
| session\_id | String | "" |
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
      <td style="text-align:left">&#xD68C;&#xC0AC; ID</td>
    </tr>
    <tr>
      <td style="text-align:left">memb_email</td>
      <td style="text-align:left">Stirng</td>
      <td style="text-align:left">&#xC0AC;&#xC6A9;&#xC790; &#xC774;&#xBA54;&#xC77C;</td>
    </tr>
    <tr>
      <td style="text-align:left">biz_id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&quot;0&quot;</td>
    </tr>
    <tr>
      <td style="text-align:left">search_dir_id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#xC11C;&#xC2DD;&#xC744; &#xCC3E;&#xC744; &#xD3F4;&#xB354; ID / &quot;all&quot;(&#xACF5;&#xC720;&#xD3F4;&#xB354;),&quot;my&quot;(&#xB0B4;
        &#xD3F4;&#xB354;)</td>
    </tr>
    <tr>
      <td style="text-align:left">display_order_mode</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        <p>&#xC815;&#xB82C;&#xAE30;&#xC900;&#xAC12;</p>
        <p>2 &#xC11C;&#xC2DD; &#xC0DD;&#xC131;&#xC77C; &#xC624;&#xB984;&#xCC28;&#xC21C;</p>
        <p>3 &#xC11C;&#xC2DD;&#xBA85; &#xB0B4;&#xB9BC;&#xCC28;&#xC21C;</p>
        <p>4 &#xC11C;&#xC2DD;&#xBA85; &#xC624;&#xB984;&#xCC28;&#xC21C;</p>
        <p>5 &#xC11C;&#xC2DD;ID &#xB0B4;&#xB9BC;&#xCC28;&#xC21C;</p>
        <p>6 &#xC11C;&#xC2DD;ID &#xC624;&#xB984;&#xCC28;&#xC21C;</p>
        <p>7 &#xC11C;&#xC2DD;&#xD0C0;&#xC785; &#xB0B4;&#xB9BC;&#xCC28;&#xC21C;</p>
        <p>8 &#xC11C;&#xC2DD;&#xD0C0;&#xC785; &#xC624;&#xB984;&#xCC28;&#xC21C;</p>
        <p>9 &#xBB38;&#xC11C;&#xC791;&#xC131;&#xC790;&#xC218; &#xB0B4;&#xB9BC;&#xCC28;&#xC21C;</p>
        <p>10 &#xBB38;&#xC11C;&#xC791;&#xC131;&#xC790;&#xC218; &#xC624;&#xB984;&#xCC28;&#xC21C;</p>
      </td>
    </tr>
  </tbody>
</table>

## 요청 Body 예시\)

```javascript
{
        "header": {
                "request_code": "1123Q",
                "request_msg": "",
                "session_id": "",
                "version": "9.9.99"
        },
        "body": {
                 "comp_id": "{회사 ID}",
                 "biz_id": "0",
                 "memb_email" : "{사용자 이메일}",
                 "search_dir_id": "all",
                 "display_order_mode": "2" 
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

```javascript
{
	"body":{
		"comp_id": "{회사 ID}",
		"biz_id": "0",
		"memb_email": "{사용자 이메일}",
		"search_dir_id": "all",
		"file_list":[{//서식 정보  Example} file_lsit 참조}] 서식 전체 조회이기 때문에 모든 서식 데이터
	}],
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

```javascript
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

