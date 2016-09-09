# Contact

## Create Contact

```shell
curl -X POST -H "Authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg==" -d '
{
"groupId": 11969,
"phoneNumber": "4596322222",
"contactName": "Sonny"
' "https://api.cpsms.dk/v2/addcontact"
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.cpsms.dk/v2/addcontact",  
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_POSTFIELDS => "{\n\"groupId\": 11969,\n\"phoneNumber\": \"4596322222\",\n\"contactName\": \"Nuller\"\n}",
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
    "Success": "Contact created/added in group"
}
```

This endpoint lest you create a new contact or add an existing to a group. If the contact exists in another group it will also be added to the new specified group.  

### HTTP Request
<wrap>
`POST https://api.cpsms.dk/v2/addcontact` <br> **Or** <br>
`POST https://api.cpsms.dk/v2/addcontact/<groupId>/<phoneNumber>/<contactName>`
</wrap>
### Parameters

Parameter | Type | Description
--------- | ------- | -----------
groupId <br>**required** | int | Id of the group the contact is to be placed in.
phoneNumber <br>**required** | string | The phone number for the contact starting with country code.
contactName | string | Name/ identifier of the contact. 



## List contact(s)

```shell
curl -X GET -H "Authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg==" 
' "https://api.cpsms.dk/v2/listcontacts/<groupId>"
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


> The above command returns JSON structured like this:

```json
[
    {
        "phoneNumber": "4595222222",
        "contactName": "Nuller"
    },
    {
        "phoneNumber": "4596222222",
        "contactName": "Buller Larsen"
    },
    {
        "phoneNumber": "4588389000",
        "contactName": "CPSMS help"
    }
]
```





This endpoint can list all contacts in a given group. <br>
You need to specify a <code>groupId</code>.

### HTTP Request

`GET https://api.cpsms.dk/v2/listcontacts/<groupId>`

### Parameters

Parameter | Type | Description
--------- | ------- | -----------
groupId <br>**required**| int | Specifies a group.
 



## Update contact

```shell
curl -X PUT -H "Authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg==" -d '
{
"phoneNumber": "4595222222" ,
"groupId": 11969,
"contactName":"New Nuller"
}
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
 CURLOPT_POSTFIELDS => "{\n\n\"phoneNumber\": \"4595222222\" ,\n\"groupId\": 11969,\n\"contactName\":\"New Nuller\"\n}\n",
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
    "Success": "Contact updated"
}
```

This endpoint creates a group for contacts.

### HTTP Request
<wrap>
`PUT https://api.cpsms.dk/v2/updatecontact` <br> **Or** <br>
`PUT https://api.cpsms.dk/v2/updatecontact/<group ID>/<phoneNumber>/<new contactName>`
</wrap>
### Parameters

Parameter | Type | Description
--------- | ------- | -----------
groupId <br>**required** | int | The ID of the group. You can find the ID with the listGroups API function or at [CPSMS.dk](http://cpsms.dk).
phoneNumber <br>**required** | string | The phone number for the contact starting with country code.
contactName | string | Name of the contact.


## Delete contact

```shell
curl -X DELETE -H "Authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg==" -d '
{
"phoneNumber": "4595222222" ,
"groupId": 11969
}
' "https://api.cpsms.dk/v2/deletecontact"
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.cpsms.dk/v2/deletecontact",  
  CURLOPT_CUSTOMREQUEST => "DELETE",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_POSTFIELDS => "{\n\n\"phoneNumber\": \"4595222222\" ,\n\"groupId\": 11969,\n\n}\n",
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
    "Success": "Contact deleted/removed"
}
```

This endpoint you can remove a contact from a group. If the contact is removed from all groups, it will be totally deleted.

### HTTP Request
<wrap>
`DELETE https://api.cpsms.dk/v2/deletecontact` <br> **Or** <br>
`DELETE https://api.cpsms.dk/v2/deletecontact/<group ID>/<phoneNumber>`
</wrap>
### Parameters

Parameter | Type | Description
--------- | ------- | -----------
groupId <br>**required** | int | The ID of the group. You can find the ID with the listGroups API function or at [CPSMS.dk](http://cpsms.dk).
phoneNumber <br>**required** | string | The contacts phone number. With country code.
