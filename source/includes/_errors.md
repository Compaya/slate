# Errors

<aside class="notice">The error message varies according to the specific problem. And can be informative.</aside>
<aside class="success">Code 200 means success. </aside>

The CPSMS.dk API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- There is something wrong with your request.
401 | Unauthorized -- Something wrong with the user credentials. 
402 | Payment Required - You do not have enough SMS credit/ points.
403 | Forbidden -- IP validating gone wrong.
404 | Not Found -- The specified method could not be found.
500 | Internal Server Error -- We had a problem with our server. Try again later.

