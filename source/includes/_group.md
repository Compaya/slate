# Group

## Create group

```shell
curl -X POST -H "Authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg==" -d '
{
"groupName": "This is a new group"
}
' "https://api.cpsms.dk/v2/addgroup"
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.cpsms.dk/v2/addgroup",  
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_POSTFIELDS => '{"groupName": "This is a new group"}',
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
    "groupId": "11986",
    "groupName": "This is a new group"
}
```

This endpoint creates a group for contacts.

### HTTP Request
<aside class="wrap_request">
<code class="post">POST</code> https://api.cpsms.dk/v2/addgroup <br>
<code class="post">POST</code> https://api.cpsms.dk/v2/addgroup/<code>&lt;groupName&gt;</code>
</aside>

### Parameters

Parameter | Type | Description
--------- | ------- | -----------
groupName <br>**required** | string | Name of the group.


## List group(s)

```shell
curl -X GET -H "Authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg==" 
' "https://api.cpsms.dk/v2/listgroups"
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.cpsms.dk/v2/listgroups",
  CURLOPT_CUSTOMREQUEST => "GET",  
  CURLOPT_RETURNTRANSFER => true,
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

```json
[
     {
         "groupId": 11963,
         "groupName": "Group 1"
     },
     {
         "groupId": 11964,
         "groupName": "Group 2"
     },
     {
         "groupId": 11966,
         "groupName": "Group 3"
     }
]
```

> The above command returns JSON structured like this:



With this endpoint you can view all your groups.

### HTTP Request

<aside class="wrap_request">
<code class="get">GET</code> https://api.cpsms.dk/v2/listgroups
</aside>



## Update group

```shell
curl -X PUT -H "Authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg==" -d '
{
"groupId": <group ID>
"groupName": "<new name of group>"
}
' "https://api.cpsms.dk/v2/updategroup"
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.cpsms.dk/v2/updategroup",  
  CURLOPT_CUSTOMREQUEST => "PUT",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_POSTFIELDS => '{"groupId": <group ID>, "groupName": "<New name of group>" }',
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
    "Success": "groupId <groupId> Updated"
}
```

This endpoint updates a group.

### HTTP Request
<aside class="wrap_request">
<code class="put">PUT</code> https://api.cpsms.dk/v2/updategroup <br>
<code class="put">PUT</code> https://api.cpsms.dk/v2/updategroup/<code>&lt;groupId&gt;</code>/<code>&lt;New groupName&gt;</code>
</aside>
### Parameters

Parameter | Type | Description
--------- | ------- | -----------
groupId <br>**required** | int | The ID of the group. You can find the ID with the listGroups API function or at [CPSMS.dk](http://cpsms.dk).
groupName <br>**required** | string | Name of the group.


## Delete group

```shell
curl -X DELETE -H "Authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg==" -d '
{
"groupId": <group ID>
}
' "https://api.cpsms.dk/v2/deletegroup"
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.cpsms.dk/v2/deletegroup",  
  CURLOPT_CUSTOMREQUEST => "DELETE",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_POSTFIELDS => "{\n    \"groupId\": <group ID>\n    }",
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
    "Success": "Group <groupId> deleted"
}
```

This endpoint deletes a group. A group can only be deleted if it does not contain Contacts.

### HTTP Request
<aside class="wrap_request">
<code class="delete">DELETE</code> https://api.cpsms.dk/v2/deletegroup<br>
<code class="delete">DELETE</code> https://api.cpsms.dk/v2/deletegroup/<code>&lt;groupId&gt;</code>
</aside>
### Parameters

Parameter | Type | Description
--------- | ------- | -----------
groupId <br>**required** | int | The ID of the group. You can find the ID with the listGroups API function or at [CPSMS.dk](http://cpsms.dk).
