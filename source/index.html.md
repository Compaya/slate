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
HTTP request methods | POST, GET, PUT, DELETE

<aside class="success">
Remember — Generate a API key in the <code>INDSTILLINGER -> API section</code> at [cpsms.dk](https://cpsms.dk/login)
</aside>

## User account

First step is to create a user account at [cpsms.dk](https://www.cpsms.dk/demologin.php).
You get the first 10 SMS points for free.

## Generate a API key

You have to generate a API key at [cpsms.dk](https://cpsms.dk/login).
This is the password to use the API.
Navigate to <code>INDSTILLINGER -> API</code> section and then generate a API key.

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


`Authorization: Basic <base64 encoding>`

<aside class="notice">
You must replace <code>&lt;base64 encoding&gt;</code> with your personal API login credentials as base64 encoding.
</aside>

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

