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

Parameters can be added to the URL or as JSON post fields. Except for SMS and GroupSMS endpoints. <br>
It is not possible to mix.<br><br>
The HTTP requests show examples with parameters set in the url.<br>
The code examples is as post fields.
 

 



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

CPSMS uses Basic Authorization to access the API. It's a base64 of your CPSMS username and a API key you need to generate on CPSMS.dk.


`Authorization: Basic <base64 encoding>`

<aside class="notice">
Replace <code>&lt;base64 encoding&gt;</code> with your personal API login credentials as base64 encoding.
</aside>


