# Log

## Getlog 

```shell
curl -X GET -H "Authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg==" -H  "https://api.cpsms.dk/v2/getlog"
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.cpsms.dk/v2/getlog",  
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_POSTFIELDS => '',
  CURLOPT_HTTPHEADER => array(
    "authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg=="
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```


> The above command returns JSON structured like this:

```json
[
    {
        "to": "4522334455",
        "from": "CPSMS",
        "pointPrice": 1,
        "userReference": null,
        "dlrStatus": 1,
        "dlrStatusText": "Received",
        "timeSent": 1466041455
    },
    {
        "to": "4533224455",
        "from": "CPSMS API",
        "pointPrice": 1,
        "userReference": "someUserIdentifier",
        "dlrStatus": 0,
        "dlrStatusText": "",
        "timeSent": 1467331800
    },
    {
        "to": "4522334488",
        "from": "Some sender",
        "pointPrice": 1,
        "userReference": null,
        "dlrStatus": 0,
        "dlrStatusText": "",
        "timeSent": 1470009600
    }
]
```

This endpoint requests your SMS log. <br>
You can look back a maximum of 3 months from current time, and the log will be shown that far back if you do not add start and end date. <br>
It’s possible to request a specific <code>&lt;to&gt;</code> with or without start/end dates.

<aside class="notice">
This request is restricted to 1 request every 2 minutes.
</aside>

### HTTP Request
<aside class="wrap_request">
<code class="get">GET</code> https://api.cpsms.dk/v2/getlog <br>
<code class="get">GET</code> https://api.cpsms.dk/v2/getlog/<code>&lt;to&gt;</code> <br>
<code class="get">GET</code> https://api.cpsms.dk/v2/getlog/<code>&lt;fromDate&gt;</code>/<code>&lt;toDate&gt;</code> <br>
<code class="get">GET</code> https://api.cpsms.dk/v2/getlog/<code>&lt;fromDate&gt;</code>/<code>&lt;toDate&gt;</code>/<code>&lt;to&gt;</code> <br>
</aside>

### Parameters

Parameter | Type | Description
--------- | ------- | -----------
to | string | The recipient of the message you want to lookup. The number starting with country code. 
fromDate | int <br>(unix timestamp) | Timestamp from where the log result should start.
toDate | int <br>(unix timestamp) | Timestamp from where the log result should end.



