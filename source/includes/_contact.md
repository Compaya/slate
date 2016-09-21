# Contact

## Create Contact

```shell
curl -X POST -H "Authorization: Basic bGFyc3ZpbmRlcjpHdWxlR3VtbWlzdMO4dmxlcg==" -d '
{
"groupId": 11969,
"phoneNumber": "4596322222",
"contactName": "Customer1"
' "https://api.cpsms.dk/v2/addcontact"
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.cpsms.dk/v2/addcontact",  
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_POSTFIELDS => '{"groupId": 11969,"phoneNumber": "4596322222","contactName": "Customer1"}',
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
    "Success": "Contact created/added in group"
}
```

This endpoint lest you create a new contact or add an existing to a group. If the contact exists in another group it will also be added to the new specified group.  

### HTTP Request
<aside class="wrap_request">
<code class="post">POST</code> https://api.cpsms.dk/v2/addcontact <br>
<code class="post">POST</code> https://api.cpsms.dk/v2/addcontact/<code>&lt;groupId&gt;</code>/<code>&lt;phoneNumber&gt;</code>/<code>&lt;contactName&gt;</code>
</aside>
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
[
    {
        "phoneNumber": "4595222222",
        "contactName": "Contact1"
    },
    {
        "phoneNumber": "4596222222",
        "contactName": "Contact2"
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
<aside class="wrap_request">
<code class="get">GET</code> https://api.cpsms.dk/v2/listcontacts/<code>&lt;groupId&gt;</code>
</aside>

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
"contactName":"New contact"
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
 CURLOPT_POSTFIELDS => '{"phoneNumber": "4595222222" ,"groupId": 11969,"contactName":"New contact"}',
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
    "Success": "Contact updated"
}
```

This endpoint creates a group for contacts.

### HTTP Request
<aside class="wrap_request">
<code class="put">PUT</code> https://api.cpsms.dk/v2/updatecontact <br>
<code class="put">PUT</code> https://api.cpsms.dk/v2/updatecontact/<code>&lt;groupId&gt;</code>/<code>&lt;phoneNumber&gt;</code>/<code>&lt;new contactName&gt;</code>
</aside>
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
  CURLOPT_POSTFIELDS => '{"phoneNumber": "4595222222" ,"groupId": 11969,',
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
    "Success": "Contact deleted/removed"
}
```

This endpoint you can remove a contact from a group. If the contact is removed from all groups, it will be totally deleted.

### HTTP Request
<aside class="wrap_request">
<code class="delete">DELETE</code> https://api.cpsms.dk/v2/deletecontact <br>
<code class="delete">DELETE</code> https://api.cpsms.dk/v2/deletecontact/<code>&lt;groupId&gt;</code>/<code>&lt;phoneNumber&gt;</code>
</aside>
### Parameters

Parameter | Type | Description
--------- | ------- | -----------
groupId <br>**required** | int | The ID of the group. You can find the ID with the listGroups API function or at [CPSMS.dk](http://cpsms.dk).
phoneNumber <br>**required** | string | The contacts phone number. With country code.
