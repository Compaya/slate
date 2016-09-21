# SMS

## Send

```shell
curl -X POST -H "Authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg==" -d '
{
"to":"4522334488", "message": "This is the message text body", "from": "Compaya", "timestamp": 1474970400
}
' "https://api.cpsms.dk/v2/send"
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.cpsms.dk/v2/send",  
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_POSTFIELDS => '{"to":"4522334488", "message": "This is the message text body", "from": "Compaya", "timestamp": 1474970400}',
  CURLOPT_HTTPHEADER => array(
    "authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg=="
  ),
));

$response = curl_exec($curl);
$httpCode = curl_getinfo($curl, CURLINFO_HTTP_CODE);

curl_close($curl);

if($httpCode == 200) {
	echo 'OK: ' . $response;
} else {

	echo 'Read response message for details: ' . $response;
}
```


> The above command returns JSON structured like this:

```json
{
    "success": [
        {
            "to": "4522334488",
            "cost": 1
        }
    ]
}
```

> If you specify "to" as array with multiple recipients and something is wrong with one or more phone numbers, your response will return like this:

```json
{
    "success": [
        {
            "to": "4522334488",
            "cost": 1
        }
    ],
    "error": [
        {
            "errorCode": 400,
            "errMsg": "Phone number length and country code do not match.",
            "to": "21314181"
        }
    ]
}
```

This endpoint lets you send a SMS to one or multiple recipients.

### HTTP Request
<aside class="wrap_request">
<code class="post">POST</code> https://api.cpsms.dk/v2/send
</aside>

### Parameters

Parameter | Type | Description
--------- | ------- | -----------
to <br>**required** | string or array | The recipient(s) of the message. The number starting with country code. 
message <br>**required** | string | The body text of the SMS message.
from | string | Sender name or number.
timestamp | int <br>(unix timestamp) | If specified the message is send at given time.
encoding | string | Default is <code>UTF-8</code>. Alternative <code>ISO-8859-1</code>.
dlr_url | string | If specified you will receive delivery reports to the given URL.
flash | int | Default is <code>0</code>. Specifies if the SMS is a flash SMS.
reference | string(32) | This can be used as your identifier. A ID from your own system. 


<aside class="notice">
If you specify multiple <code>&lt;to&gt;</code> and you have an error along with success. Your HTTP header response code will be 207 Multi-status. <br>
You are adviced to go thrue your error(s) before sending to the same recipients.
</aside>


## Send to group

```shell
curl -X POST -H "Authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg=="  -d '
{
"to_group":12345, "message": "This is the message text body", "from": "Compaya", "timestamp": 1474970400
}
' "https://api.cpsms.dk/v2/sendgroup"
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.cpsms.dk/v2/sendgroup",  
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_POSTFIELDS => '{"to_group":12345, "message": "This is the message text body", "from": "Compaya", "timestamp": 1474970400}',
  CURLOPT_HTTPHEADER => array(
    "authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg=="
  ),
));

$response = curl_exec($curl);
$httpCode = curl_getinfo($curl, CURLINFO_HTTP_CODE);

curl_close($curl);

if($httpCode == 200) {
	echo 'OK: ' . $response;
} else {

	echo 'Read response message for details: ' . $response;
}
```


> The above command returns JSON structured like this:

```json
{
    "success": [
        {
            "to": "4522334488",
            "cost": 1
        },
        {
            "to": "4522334499",
            "cost": 1
        },
        {
            "to": "46522334455",
            "cost": 1.6
        }        
    ]
}
```

This endpoint lets you send a SMS to recipients you have created as contacts in a group.

### HTTP Request

<aside class="wrap_request">
<code class="post">POST</code> https://api.cpsms.dk/v2/sendgroup
</aside>

### Parameters

Parameter | Type | Description
--------- | ------- | -----------
to_group <br>**required** | int | Specify the Group ID where you have your contacts. 
message <br>**required** | string | The body text of the SMS message.
from | string | Sender name or number.
timestamp | int <br>(unix timestamp) | If specified the message is send at given time.
encoding | string | Default is <code>UTF-8</code>. Alternative <code>ISO-8859-1</code>.
dlr_url | string | If specified you will receive delivery reports to the given URL.
flash | int | Default is <code>0</code>. Specifies if the SMS is a flash SMS.
reference | string(32) | This can be used as your identifier. A ID from your own system.

<aside class="notice">
You can create, list (and more) groups with the API methods or at CPSMS.DK.
</aside>


## Simple send (as GET)

This endpoint lets you send a SMS as GET. Makes it possible to execute a SMS in the URL.

### HTTP Request

<aside class="wrap_request">
<code class="get">GET</code> username:APIkey@https://api.cpsms.dk/v2/simplesend/<code>&lt;to&gt;</code>/<code>&lt;message&gt;</code>/<code>&lt;from&gt;</code>
</aside>

### Parameters

Parameter | Type | Description
--------- | ------- | -----------
to <br>**required** | string or array | The recipient(s) of the message. The number starting with country code. 
message <br>**required** | string | The body text of the SMS message.
from | string | Sender name or number.



## SMS credit

```shell
curl -X POST -H "Authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg==" "https://api.cpsms.dk/v2/creditvalue"
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.cpsms.dk/v2/creditvalue",  
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_POSTFIELDS => "",
  CURLOPT_HTTPHEADER => array(
    "authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg=="
  ),
));

$response = curl_exec($curl);
$httpCode = curl_getinfo($curl, CURLINFO_HTTP_CODE);

curl_close($curl);

if($httpCode == 200) {
	echo 'OK: ' . $response;
} else {

	echo 'Read response message for details: ' . $response;
}
```


> The above command returns JSON structured like this:

```json
{
    "credit": "9.843,40"
}
```

This endpoint lets you see how much credit you have left on your CPSMS.dk account. 

### HTTP Request

<aside class="wrap_request">
<code class="get">GET</code> https://api.cpsms.dk/v2/creditvalue
</aside>


## Delete SMS

```shell
curl -X DELETE -H "Authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg==" "https://api.cpsms.dk/v2/deletesms"
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.cpsms.dk/v2/deletesms",  
  CURLOPT_CUSTOMREQUEST => "DELETE",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_POSTFIELDS => "",
  CURLOPT_HTTPHEADER => array(
    "authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg=="
  ),
));

$response = curl_exec($curl);
$httpCode = curl_getinfo($curl, CURLINFO_HTTP_CODE);

curl_close($curl);

if($httpCode == 200) {
	echo 'OK: ' . $response;
} else {

	echo 'Read response message for details: ' . $response;
}
```


> The above command returns JSON structured like this:

```json
{
    "Success": "SMS deleted"
}
```

With this endpoint you get the the ability to delete a SMS that is set with a <code>&lt;timestamp&gt;</code> (timed send) set to some point in the future. <br>
The <code>&lt;timestamp&gt;</code> have to be greater than 10 minutes from delete time. <br>
You need to have set a <code>&lt;reference&gt;</code> on the SMS to have the ability to delete. <br>
Every SMS with the specified <code>&lt;reference&gt;</code> that meets the criteria will bee deleted

### HTTP Request

<aside class="wrap_request">
<code class="delete">DELETE</code> https://api.cpsms.dk/v2/deletesms/<code>&lt;reference&gt;</code>
</aside>

### Parameters

Parameter | Type | Description
--------- | ------- | -----------
reference <br>**required** | string(32) | The identifier set by you, when you posted the SMS.

<aside class="warning">
When a SMS is deleted it cannot be recoverd.
</aside>







