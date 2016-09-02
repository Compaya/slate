---
title: API Documentation for CPSMS.dk

language_tabs:
  - shell
  - php: PHP


toc_footers:
  - <a href='#'>Sign Up for a FREE demo login</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Welcome 

To the CPSMS.DK API. 
Here you will find descriptions of the almost endless possibilities with our API.

So indulge yourself in the plethora of opportunities for letting your programs interact with CPSMS.

"CPSMS - I'm loving it" 

# Getting started
(Something) | Value 
--------- | ------- 
Host | api.cpsms.dk/v2
Port | 443
Protocol | HTTPS
Authentication | Basic Authentication

<aside class="success">
Remember — Generate a API key in the <code>INDSTILLINGER -> API section</code> at [cpsms.dk](https://cpsms.dk/login)
</aside>

## User account

First step is to create a user account at [cpsms.dk](https://www.cpsms.dk/demologin.php).
You get the first 10 SMS points for free.

## Generate a API key

You have to generate a API key at [cpsms.dk](https://cpsms.dk/login).
This is the password to use the API.
Navigate to <code>INDSTILLINGER -> API section</code> and then generate a API key.

<aside class="notice">
For extra security you can turn on IP validating and add the IP(s) you want to allow.
</aside>
# Authentication

> To authorize, use this code:


```shell
# With cURL, you can just pass the correct header with each request
curl "https://api.cpsms.lv/v2/endpoint"
  -H "Authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg=="
```

```php
# Adding a cURL header
<?php
CURLOPT_HTTPHEADER => array(
    "Authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg==",
    "cache-control: no-cache" 
);
```





> Make sure to replace Authorization with your own API user and key.

CPSMS uses Basic Authorization to access the API. It's a base64 of your CPSMS username and a API key you need to generate on CPSMS.dk.


`Authorization: Basic "base64 encoding"`

<aside class="notice">
You must replace <code>base64 encoding</code> with your personal API login credentials as base64 encoding.
</aside>

# SMS

## send

```shell
curl -X POST -H "Authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg==" -H "Cache-Control: no-cache" -d '
{
"to":["4522334488","4577777777","4723434375"], "message": "This is the message text body", "from": "Compaya", "timestamp": 1474970400
}
' "http://api.cpsms.lv/v2/send"
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "http://api.cpsms.lv/v2/send",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"to\":[\"4522334488\",\"4577777777\",\"4523434375\"], \"message\": \"This is the message text body\", \"from\": \"Compaya\", \"timestamp\": 1474970400}",
  CURLOPT_HTTPHEADER => array(
    "authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg==",
    "cache-control: no-cache"
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



## sendgroup

```shell
curl -X POST -H "Authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg==" -H "Cache-Control: no-cache" -d '
{
"to_group":12345, "message": "This is the message text body", "from": "Compaya", "timestamp": 1474970400
}
' "http://api.cpsms.lv/v2/sendgroup"
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "http://api.cpsms.lv/v2/send",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"to_group\":12345, \"message\": \"This is the message text body\", \"from\": \"Compaya\", \"timestamp\": 1474970400}",
  CURLOPT_HTTPHEADER => array(
    "authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg==",
    "cache-control: no-cache"
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


## simplesend

This endpoint lets you send a SMS as GET. Makes it possible to execute a SMS in the URL.

### HTTP Request

`GET username:APIkey@https://api.cpsms.dk/v2/simplesend`

### Parameters

Parameter | Type | Description
--------- | ------- | -----------
to <br>**required** | string or array | The recipient(s) of the message. The number starting with country code. 
message <br>**required** | string | The body text of the SMS message.
from | string | Sender name or number.


## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

