# Start email sending - ExportAPI Description

ExportAPI is a function that allows the contractor to export the body in JSON format based on the information set through the export\_api\_info parameter value at the start of the non-face-to-face contract.

If you enter "embed" instead of custom in request\_code, the contract progress URL will be exported and KakaoTalk and email notifications will not be sent to the contractor. This function is used when shipping separately from the customer based on the URL received.

If using embedded code, we provide the contract start URL with a response upon initial non-face-to-face contact call, and whenever the signer approves or rejects the contract, we provide the progress URL to export and the contractor's number or email that you entered \(e-mail if called, number if called by number\) Download documents so that documents can be downloaded at the end of the contract, and provide a history certificate download URL.

## Parameter 

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Parameter Name                        </b>
      </th>
      <th style="text-align:left">DataType<b>                                                </b>
      </th>
      <th style="text-align:left">Required</th>
      <th style="text-align:left"><b>Description</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">export_api_info</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">
        <p>The value that you set when you export the created data.</p>
        <p>( like webhook )</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.api_type</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Required</td>
      <td style="text-align:left">&quot;StartAndEnd&quot; ( Start and End step) or &quot;ALL&quot; ( ALL
        step )</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.url</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Required</td>
      <td style="text-align:left">URL to receive data from</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.request_code</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">Return The Value You Want to Receive or &quot;embed&quot;( See ExportAPI
        Description)</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.clientid</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">ID issued by esignon (<a href="https://esignon.net/en/customer/">question </a>for
        issue)</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.authorization</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">The value you want to set to header authorization when receiving data</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.request_params</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">Use when you want to get a specific value inside a document.</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.request_params.param_id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Required</td>
      <td style="text-align:left">Name of parameter to receive (custom)</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.request_params.param_value</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Required</td>
      <td style="text-align:left">Default value to be obtained if the value to be obtained from Params.fields
        is not in the document</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.request_params.fields</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left">Required</td>
      <td style="text-align:left">The value entered instead of param_value if the value corresponding to
        the field name exists in the document by querying the field name inside
        the format.</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.request_params.fields.doc_id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Required</td>
      <td style="text-align:left">templateID</td>
    </tr>
    <tr>
      <td style="text-align:left">export_api_info.request_params.fields.field_name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Required</td>
      <td style="text-align:left">template field name</td>
    </tr>
  </tbody>
</table>

## export\_api Response\) 

```javascript
{
	"header": {
		"api_name": "export",
		"session_id": "S1001",
		"request_code": "{ Value set at request }"
	},
	"body": {
		"wfluid": "0", 
		"clientid": "{ Unique ID for using eSignonAPI }",
		"processid": "1", //Progress stage delimited value of document
		"requestid": "{ header's request_code }",
		"actionid": "1", //Progress stage delimited value of document
		"workdatetime": "2020-01-31 04:23:28.0", //Completion time
		"worktype": "CF", //CF=Approval, RT=turn back( If the original contractor returns the document, it will be canceled.)
		"wfuid": "{}", // Document ID
		"useremail": "{ Signer email }", 
		"opinion": "", //When approving or returning, print when customers use a return message or a transmission message.
		"param_id": "param_value" // filed_name exist - param_id:field_value return
	}
}
```

## Export\_api Response Example\) When code-embedded \(Playing\)

```javascript
{
	"header": {
		"api_name": "export",
		"session_id": "S1001",
		"request_code": "{embed}"
	},
	"body": {
		"wfluid": "0",
		"clientid": "{ Unique ID for using eSignonAPI }",
		"processid": "1", //Progress stage delimited value of document
		"requestid": "{ embed }",
		"actionid": "1", //Progress stage delimited value of document
		"workdatetime": "2020-01-31 04:23:28.0", //Completion time
		"worktype": "CF",//CF=Approval, RT=turn back( If the original contractor returns the document, it will be canceled.)
		"wfuid": "{}", //Document ID
		"useremail": "{ Signer email }", 
		"opinion": "", //When approving or returning, print when customers use a return message or a transmission message.
		"param_id": "param_value",
		"next_play_user":"{Email to sign next}",
		"play_url":"{URLs to be passed to customers to sign next}",
		"status":"{Playing}", // progress status
		"next_user_name":"{Next Signer Name}",
		"user_name":"{Current Signer Name}"
	}
}
```

## Export\_api Response Example\) When code-embedded \(Complete\)

```javascript
{
	"header": {
		"api_name": "export",
		"session_id": "S1001",
		"request_code": "{embed}"
	},
	"body": {
		"wfluid": "0",
		"clientid": "{ Unique ID for using eSignonAPI }",
		"processid": "1", //Progress stage delimited value of document
		"requestid": "{ embed }",
		"actionid": "1", //Progress stage delimited value of document
		"workdatetime": "2020-01-31 04:23:28.0", //Completion time
		"worktype": "CF",//CF=Approval, RT=turn back( If the original contractor returns the document, it will be canceled.)
		"wfuid": "{}", //Document ID
		"useremail": "{ Signer email }", 
		"opinion": "", //When approving or returning, print when customers use a return message or a transmission message.
		"param_id": "param_value",
		"cert_url":"{History Certificate Download URL}",
		"download_url":"{Document Download URL}",
		"status":"{Playing}", // progress status
		"user_name":"{Current Signer Name}"
	}
}
```

