# SMS

## Send

```shell
curl -X POST -H "Authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg==" -d '
{
"to":["4522334488","4577777777","4723434375"], "message": "This is the message text body", "from": "Compaya", "timestamp": 1474970400
}
' "https://api.cpsms.lv/v2/send"
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.cpsms.lv/v2/send",  
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"to\":[\"4522334488\",\"4577777777\",\"4523434375\"], \"message\": \"This is the message text body\", \"from\": \"Compaya\", \"timestamp\": 1474970400}",
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
{
    "success": [
        [
            {
                "to": "4522334488",
                "price": "1",
                "countryCode": "1"
            },
            {
                "to": "4577777777",
                "price": "1",
                "countryCode": "1"
            },
            {
                "to": "4523434375",
                "price": "1",
                "countryCode": "1"
            }
        ]
    ]
}
```

This endpoint lets you send a SMS to one or multiple recipients.

### HTTP Request

`POST https://api.cpsms.dk/v2/send`

### Parameters

Parameter | Type | Description
--------- | ------- | -----------
to <br>**required** | string or array | The recipient(s) of the message. The number starting with country code. 
message <br>**required** | string | The body text of the SMS message.
from | string | Sender name or number.
timestamp | int <br>(unix timestamp) | If specified the message is send at given time.
encoding | string | Default is <code>UTF-8</code>. alternative <code>ISO-8859-1</code>.
dlr_url | string | If specified you will receive delivery reports to the given URL.
flash | int | Default is 0. Specifies if the SMS is a flash SMS.



## Send to group

```shell
curl -X POST -H "Authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg=="  -d '
{
"to_group":12345, "message": "This is the message text body", "from": "Compaya", "timestamp": 1474970400
}
' "https://api.cpsms.lv/v2/sendgroup"
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.cpsms.lv/v2/sendgroup",  
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"to_group\":12345, \"message\": \"This is the message text body\", \"from\": \"Compaya\", \"timestamp\": 1474970400}",
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
{
    "success": [
        [
            {
                "to": "4522334488",
                "price": "1",
                "countryCode": "1"
            },
            {
                "to": "4577777777",
                "price": "1",
                "countryCode": "1"
            },
            {
                "to": "4523434375",
                "price": "1",
                "countryCode": "1"
            }
        ]
    ]
}
```

This endpoint lets you send a SMS to recipients you have created as contacts in a group.

### HTTP Request

`POST https://api.cpsms.dk/v2/sendgroup`

### Parameters

Parameter | Type | Description
--------- | ------- | -----------
to_group <br>**required** | int | Specify the Group ID where you have your contacts. 
message <br>**required** | string | The body text of the SMS message.
from | string | Sender name or number.
timestamp | int <br>(unix timestamp) | If specified the message is send at given time.
encoding | string | Default is <code>UTF-8</code>. alternative <code>ISO-8859-1</code>.
dlr_url | string | If specified you will receive delivery reports to the given URL.
flash | int | Default is 0. Specifies if the SMS is a flash SMS.

<aside class="success">
You can create, list (and more) groups with the API methods or at CPSMS.DK.
</aside>


## Simple send (as GET)

This endpoint lets you send a SMS as GET. Makes it possible to execute a SMS in the URL.

### HTTP Request

`GET username:APIkey@https://api.cpsms.dk/v2/simplesend`

### Parameters

Parameter | Type | Description
--------- | ------- | -----------
to <br>**required** | string or array | The recipient(s) of the message. The number starting with country code. 
message <br>**required** | string | The body text of the SMS message.
from | string | Sender name or number.

```URL
GET username:APIkey@https://api.cpsms.dk/v2/simplesend/$to/$message/$from
``` 

