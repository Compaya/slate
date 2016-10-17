---
title: API Documentation for CPSMS.dk

language_tabs:
  - shell
  - php: PHP


toc_footers:
  - <a href='https://cpsms.dk/demologin.php'>Sign Up for a FREE demo login</a>
  

includes:
  - sms
  - group
  - contact
  - log
  - errors

search: true
---

# Welcome 

Get started sending SMS from your own system via CPSMS.dk API.
This is the documentation listing all endpoints / methods. 

# Getting started
. | .
--------- | ------- 
Host | api.cpsms.dk/v2
Port | 443
Protocol | HTTPS
Authentication | Basic Authentication
HTTP request methods | <code class="post">POST</code>  <code class="get">GET</code>  <code class="put">PUT</code>  <code class="delete">DELETE</code>

<aside class="notice">
Remember — Generate a API key in the <code>INDSTILLINGER -> API</code> section. 
</aside>

## User account

First step is to create a user account at [cpsms.dk](https://www.cpsms.dk/demologin.php).
You get the first 10 SMS points for free.

## Generate a API key

You have to generate a API key at [cpsms.dk](https://cpsms.dk/login).<br>
This is the password to use the API.<br>
Navigate to <code>INDSTILLINGER -> API</code> section and then generate a API key.

<aside class="notice">
For extra security you can turn on IP validating and add the IP adresses('s) you want to allow.
</aside>


# Generally

Data can be send as GET parameters or posted as a JSON object. Except for SMS and GroupSMS endpoints. - these requires data to be send as JSON objects<br>
It is not possible to use a mix of GET parameters and a JSON object.<br><br>
The HTTP requests show examples with parameters set as GET.<br>
The code examples is as JSON objects.
 

 



# Authentication

> To authorize, use this code:


```shell
# With cURL, you can just pass the correct header with each request
curl "https://api.cpsms.dk/v2/endpoint"
  -H "Authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg=="
```

```php

<?php
$username = "Your CPSMS username";
$apiKey = "Your generated key";

CURLOPT_HTTPHEADER => array(
    "Authorization: Basic " . base64_encode($username . ':' . $apiKey)
);
```





> Make sure to replace $username and $apiKey with your own credentials.

CPSMS requires Basic Authorization to access the API. The token is your CPSMS username and your API key, concatenated with a colon, encoded as base64


`Authorization: Basic <token>`

<aside class="notice">
Replace <code>&lt;token&gt;</code> with your own. (Username : API key)
</aside>


