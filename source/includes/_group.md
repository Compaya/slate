# Group

## Create group

```shell
curl -X PUT -H "Authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg==" -H "Cache-Control: no-cache" -d '
{
"groupname": "This is a new group"
}
' "https://api.cpsms.lv/v2/addgroup"
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.cpsms.lv/v2/addgroup",  
  CURLOPT_CUSTOMREQUEST => "PUT",
  CURLOPT_POSTFIELDS => "{\n\"groupname\": \"This is a new group\"\n}",
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
    "Id": "11985",
    "Name": "test"
}
```

This endpoint you can create a group for contacts.

### HTTP Request

`PUT https://api.cpsms.dk/v2/addgroup`

### Parameters

Parameter | Type | Description
--------- | ------- | -----------
groupname <br>**required** | string | Name of the group 


## List group(s)

```shell
curl -X GET -H "Authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg==" 
' "https://api.cpsms.lv/v2/listgroups/<groupId>"
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.cpsms.lv/v2/listgroups/<groupId>",
  CURLOPT_CUSTOMREQUEST => "GET",  
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
    "Id": "11985",
    "Name": "Returned group name"
}
```

This endpoint you can view all or just one specific group. <br>
If you do not specify a group ID your response will be a list of all your groups.

### HTTP Request

`GET https://api.cpsms.dk/v2/listgroups/<groupId>`

### Parameters

Parameter | Type | Description
--------- | ------- | -----------
groupId | int | Specifies a group 


