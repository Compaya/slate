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


> The above request returns a JSON formatted delivery report like this:

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

> If you set multiple recipients, the delevery report will contain statuses for every message, like so: 

```json
{
    "success": [
        {
            "to": "4522334488",
            "cost": 1
        },
        {
			"to": "4533445599",
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
message <br>**required** | string(1530) | The body text of the SMS message. Specifies the message to be sent. All characters allowed by the SMS protocol are accepted. If the message contains any illegal characters, they are automatically removed, and the message shortened. The maximum message length is 1530 characters, which is the length of 10 SMS'es joined together.
from | string(11/20) | Set the number that the receiver will see as the sender of the SMS. It can be either numeric with a limit of 20 chars or alphanumeric with a limit of 11 chars.
timestamp | int <br>(unix timestamp) | If specified, the message will be send at this time.
encoding | string | Default is <code>UTF-8</code>. Alternative <code>ISO-8859-1</code>.
dlr_url | string | If specified, delivery reports will be POSTed to this address.<br> If for example the <code>dlr_url</code> is http://google.com then CPSMS.dk will append ?status=x&receiver=xx <br>Example: http://google.com?status=x&receiver=xx <br><br> If needed you can add your own parameters at the end of your <code>dlr_url</code>.<br><br>See status parameters table.  
flash | int | Default is <code>0</code>. Specifies if the SMS should be send as a flash SMS.
reference | string(32) | An optional reference of your choice. 

### Status parameters (dlr_url)

Status | Description 
--------- | ------- 
1 | Delivery successful
2 | Delivery failed
3 | Message buffered
4 | Delivery abandoned

<aside class="notice">
If you specify multiple recipients, your response will contain status for every tried recipient. If one, or more, messages fail to be delivered, the response result will be returned with a HTTP status code of 207 (Multi-Status) (for easy detection - it has nothing to do with WebDAV, nor do it comply with other RFC standards related to this type of response). In that case, it is advised to traverse the response result for errors, and take appropriate action.
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


> The above request returns a JSON formatted delivery report like this:

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
message <br>**required** | string(1530) | The body text of the SMS message. Specifies the message to be sent. All characters allowed by the SMS protocol are accepted. If the message contains any illegal characters, they are automatically removed, and the message shortened. The maximum message length is 1530 characters, which is the length of 10 SMS'es joined together.
from | string(11/20) | Set the number that the receiver will see as the sender of the SMS. It can be either numeric with a limit of 20 chars or alphanumeric with a limit of 11 chars.
timestamp | int <br>(unix timestamp) | If specified, the message will be send at this time.
encoding | string | Default is <code>UTF-8</code>. Alternative <code>ISO-8859-1</code>.
dlr_url | string | If specified, delivery reports will be POSTed to this address. See details in Send example [here](#send).
flash | int | Default is <code>0</code>. Specifies if the SMS should be send as a flash SMS.
reference | string(32) | An optional reference of your choice.

<aside class="notice">
You can create, list (and more) groups with the API methods or at CPSMS.DK.
</aside>


## Simple send (as GET)

This endpoint lets you send a SMS as GET. Makes it possible to fx. execute a SMS in the URL.

```shell
curl -X GET "https://cpsmsuser:18bf8100-d5e2-4660-a214-84ecdd5d1710@api.cpsms.dk/v2/simplesend/4522335544/message/CPSMS"
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://cpsmsuser:18bf8100-d5e2-4660-a214-84ecdd5d1710@api.cpsms.dk/v2/simplesend/4522335544/message/CPSMS",  
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_RETURNTRANSFER => true,  
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


> The above request returns a JSON formatted delivery report like this:

```json
{
    "success": [
        {
            "to": "4522335544",
            "cost": 1
        }
    ]
}     
```

### HTTP Request

<aside class="wrap_request">
<code class="get">GET</code> https://username:APIkey@api.cpsms.dk/v2/simplesend/<code>&lt;to&gt;</code>/<code>&lt;message&gt;</code>/<code>&lt;from&gt;</code>
</aside>

### Parameters

Parameter | Type | Description
--------- | ------- | -----------
to <br>**required** | string or array | The recipient(s) of the message. The number starting with country code. 
message <br>**required** | string(1530) | The body text of the SMS message. Specifies the message to be sent. All characters allowed by the SMS protocol are accepted. If the message contains any illegal characters, they are automatically removed, and the message shortened. The maximum message length is 1530 characters, which is the length of 10 SMS'es joined together.
from | string(11/20) | Set the number that the receiver will see as the sender of the SMS. It can be either numeric with a limit of 20 chars or alphanumeric with a limit of 11 chars.



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


> The above request returns a JSON formatted delivery report like this:

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
  CURLOPT_POSTFIELDS => '{"reference":"<reference>"',
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


> The above request returns a JSON formatted delivery report like this:

```json
{
    "Success": "SMS(s) deleted"
}
```

With this endpoint you get the the ability to delete a SMS that is set with a <code>&lt;timestamp&gt;</code> (timed send) set to some point in the future. <br>
The <code>&lt;timestamp&gt;</code> have to be greater than 10 minutes from delete time. <br>
You need to have set a <code>&lt;reference&gt;</code> on the SMS to have the ability to delete. <br>
Every SMS with the specified <code>&lt;reference&gt;</code> that meets the criteria will bee deleted

### HTTP Request

<aside class="wrap_request">
<code class="delete">DELETE</code> https://api.cpsms.dk/v2/deletesms<br>
<code class="delete">DELETE</code> https://api.cpsms.dk/v2/deletesms/<code>&lt;reference&gt;</code>
</aside>

### Parameters

Parameter | Type | Description
--------- | ------- | -----------
reference <br>**required** | string(32) | The identifier set by you, when you posted the SMS.

<aside class="warning">
When a SMS is deleted it cannot be recoverd.
</aside>







