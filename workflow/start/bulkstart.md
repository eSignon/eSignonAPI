# Bulk Contract Start

* Start Bulk Contract

* For bulk sending, the order of signatures depends on the steps you set in the template. \(It depends on the template step type\) The sender will be set as starter of document and the signer's information will be determined by the value in unset\_player\_list. Document will be sent for all signers in the unset\_player\_list.

## API URL

| Url | Type | **Code** |
| :--- | :--- | :--- |
| https://docs.esignon.net/JEDOC/Common.do | POST | 1410Q |

## Request

### Parameters

####  Headers

| **Parameter Name**                         | DataType | **Description** |
| :--- | :--- | :--- |
| Content-Type | String | application/json |
| Authorization | String | esignon {token} |

####   Body 

  Body - Header Parameter

| **Parameter Name**                         | DataType | **Description** |
| :--- | :--- | :--- |
| request\_code | String | "1410Q" |
| request\_msg | String | "Start Work Flow Bulk Sending" |
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
      <td style="text-align:left">Company ID</td>
    </tr>
    <tr>
      <td style="text-align:left">biz_id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&quot;0&quot;</td>
    </tr>
    <tr>
      <td style="text-align:left">memb_email</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Document starter&apos;s email</td>
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
        <p>lid_id created when creating the template</p>
        <p>(You can check the select Templete list.)</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">unset_player_list</td>
      <td style="text-align:left">Data</td>
      <td style="text-align:left">Enter the signers information</td>
    </tr>
    <tr>
      <td style="text-align:left">unset_player_list.memb_id_type</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&quot;EMail&quot;</td>
    </tr>
    <tr>
      <td style="text-align:left">unset_player_list.email</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Email address</td>
    </tr>
    <tr>
      <td style="text-align:left">unset_player_list.name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Signer name</td>
    </tr>
    <tr>
      <td style="text-align:left">unset_player_list.language</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&quot;ko-KR&quot;,&quot;en-US&quot;,&quot;ja-JP&quot;</td>
    </tr>
    <tr>
      <td style="text-align:left">unset_player_list.workflow_name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Document name to start</td>
    </tr>
    <tr>
      <td style="text-align:left">unset_player_list.enable_mobile_cert</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&quot;false&quot; ( is only available in Korea.)</td>
    </tr>
    <tr>
      <td style="text-align:left">unset_player_list.mobile_number</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&quot;&quot; ( is only available in Korea.)</td>
    </tr>
    <tr>
      <td style="text-align:left">unset_player_list.enable_password_cert</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Password authentication feature &quot;True or false&quot;</td>
    </tr>
    <tr>
      <td style="text-align:left">unset_player_list.password_hint</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Password hint</td>
    </tr>
    <tr>
      <td style="text-align:left">unset_player_list.password</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Password</td>
    </tr>
    <tr>
      <td style="text-align:left">field_list</td>
      <td style="text-align:left">Data</td>
      <td style="text-align:left">Field value added in case there is a value to be entered in advance</td>
    </tr>
    <tr>
      <td style="text-align:left">field_list.doc_id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Templete ID</td>
    </tr>
    <tr>
      <td style="text-align:left">field_list.field_name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Templete field name</td>
    </tr>
    <tr>
      <td style="text-align:left">field_list.field_value</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The value you want to enter in the field</td>
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

## Request Body Example

```javascript
{
  "header": {
    "request_code": "1410Q",
    "api_name": "Start Work Flow Bulk Sending",
    "session_id": "",
    "version" : "9.9.99"
  },
  "body": {
    "comp_id": "{Company ID}",
    "biz_id": "0",
    "memb_email": "{ Email of document starter}",
    "workflow_lib_id": "{ templete lib_id }",
    "workflow_name": "",
    "unset_player_list": [{
        "memb_id_type" : "{ EMail }",
        "email": "{ email adress }",
        "name" : "{ Signer name }",
        "language": "ko-KR",//ko-KR, ja-JP, en-US
        "workflow_name" : "{ document name }",
        "enable_mobile_cert" : "flase",//( is only available in Korea.)
        "mobile_number" : "",//( is only available in Korea.)
        "enable_password_cert":"{true or false}",
	      "password_hint":"{Password to use when proceeding with the contract hint}",  		
	      "password":"{Password to use when proceeding with the contract}",
        "field_list": [{ // Field used to transfer by entering a value in the field at contract startup
      				"doc_id": "{ Templete ID }",
      				"field_name": "{ Templete field name }",
      				"field_value": "{ The value you want to enter in the appropriate field }"
			  }]
      }],// Send contracts to all customers you set up
    "comment": "",
    "enable_legal_agreement":"false"
  }
}
```

## Response

| Code | **Description** | **Reference** |
| :--- | :--- | :--- |
| 200 | success | success |
| 400 | Connection failed |  |

#### Result\_msg

| Code | **Description** | **Reference** |
| :--- | :--- | :--- |
| 00 | success | success |
| -1 | fail | Parsing failed because the body information of the received message is incorrect. |
| 10 | fail | The specific Work Flow Library does not exist. |
| 11 | fail | Failed. |
| 12 | fail | The maximum storage capacity has been exceeded. |
| 13 | fail | The maximum number of documents is exceeded. |
| 14 | fail | The usage period has expired. |
| 15 | fail | The writer setting is incorrect. |

## Response Body Example

```javascript
}
	"body":{
		"workflow_list":[
			{
			"workflow_id": "{Document ID}",
			"unset_player_email": "{Signer email}",
			"unset_player_name": "{Signer name}",
			"result": "OK",
			"description": "",
			"workflow_name": "{Documnet name}",
			"token": "{accesstoken}",
			"lang": "ko-KR",
			"reg_date": "{Company Payment Renewal Date}"},
			"comp_id": "{Company ID}",
			"biz_id": "0",
			"memb_email": "{Email of document starter}",
			"workflow_lib_id": "{Templete lib_id}"
			},
	"header":{
		"session_id": "thread_023",
		"response_code": "1410A",
		"result_code": "00",
		"result_msg": "Start Work Flow bulk Sending.",
		"version": "9.9.99"
	}
}
```

