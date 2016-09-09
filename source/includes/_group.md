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
    "groupId": "11986",
    "groupName": "This is a new group"
}
```

This endpoint creates a group for contacts.

### HTTP Request
<aside class="wrap_request">
<code>POST</code> https://api.cpsms.dk/v2/addgroup <br>
<code>POST</code> https://api.cpsms.dk/v2/addgroup/<code>&lt;groupName&gt;</code>
</aside>

### Parameters

Parameter | Type | Description
--------- | ------- | -----------
groupName <br>**required** | string | Name of the group.


## List group(s)

```shell
curl -X GET -H "Authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg==" 
' "https://api.cpsms.dk/v2/listgroups/<groupId>"
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.cpsms.dk/v2/listgroups/<groupId>",
  CURLOPT_CUSTOMREQUEST => "GET",  
  CURLOPT_RETURNTRANSFER => true,
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

```json
[
     {
         "groupId": 11963,
         "groupName": "Group #1"
     },
     {
         "groupId": 11964,
         "groupName": "Group #2"
     },
     {
         "groupId": 11966,
         "groupName": "Group #3"
     }
]
```

> The above command returns JSON structured like this:



This endpoint you can view all or just one specific group. <br>
If you do not specify a <code>groupId</code> your response will be a list of all your groups.

### HTTP Request

<aside class="wrap_request">
<code>GET</code> https://api.cpsms.dk/v2/listgroups/<code>&lt;groupId&gt;</code>
</aside>

### Parameters

Parameter | Type | Description
--------- | ------- | -----------
groupId | int | Specifies a group.
 
<aside class="notice">
If you specify a <code>groupId</code> the JSON resault is "a little different".  Omskrives!?!?!
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
    "Success": "groupId <groupId> Updated"
}
```

This endpoint creates a group for contacts.

### HTTP Request
<aside class="wrap_request">
<code>PUT</code> https://api.cpsms.dk/v2/updategroup <br>
<code>PUT</code> https://api.cpsms.dk/v2/updategroup/<code>&lt;group ID&gt;</code>/<code>&lt;New groupname&gt;</code>
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
    "Success": "Group <groupId> deleted"
}
```

This endpoint you can delete a group. A group can only be deleted if it do not contain Contacts.

### HTTP Request
<wrap>
`DELETE https://api.cpsms.dk/v2/deletegroup` <br> **Or** <br>
`DELETE https://api.cpsms.dk/v2/deletegroup/<group ID>`
</wrap>
### Parameters

Parameter | Type | Description
--------- | ------- | -----------
groupId <br>**required** | int | The ID of the group. You can find the ID with the listGroups API function or at [CPSMS.dk](http://cpsms.dk).
