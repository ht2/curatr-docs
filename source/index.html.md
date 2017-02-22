---
title: Curatr API Reference

language_tabs:
  - shell
  - php
  - javascript

toc_footers:

includes:
  - errors

search: true
---

# Introduction

Welcome to the Curatr API! You can use our API to access Curatr API endpoints, which can query Curatr entities in a RESTful way.

# Authentication

## Get an access token

This endpoint gets a new OAuth token.

### HTTP Request

`GET http://example.curatr3.com/oauth/access_token`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
grant_type | client_credentials | This should not be changed.
client_id | - | Your unique client ID
client_secret | - | Your unique client secret

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

> To authorize, use this code:

```shell
curl --request POST \
  --url http://example.curatr3.com/oauth/access_token \
  --form grant_type=client_credentials \
  --form client_id=CLIENT_ID \
  --form client_secret=CLIENT_SECRET
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "http://example.curatr3.com/oauth/access_token",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"grant_type\"\r\n\r\nclient_credentials\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"client_id\"\r\n\r\nCLIENT_ID\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"client_secret\"\r\n\r\nCLIENT_SECRET\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--",
  CURLOPT_HTTPHEADER => array(
    "cache-control: no-cache",
    "content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    "postman-token: b6e80070-0baa-e9cd-58cf-c71b7f711b99"
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
    "id": 1,
    "fname": "Severus",
    "lname": "Snape",
    "email": "s.snape@hogwarts.edu",
    "username": "s.snape"
  },
  {
    "id": 2,
    "fname": "Albus",
    "lname": "Dumbledore",
    "email": "a.dumbledore@hogwarts.edu",
    "username": "a.dumbledore"
  }
]
```

> Make sure to replace `CLIENT_ID` and `CLIENT_SECRET` with the correct credentials for your organisation.

Curatr uses OAuth to authenticate API connections.

Curatr expects for the OAuth token to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer {{bearerToken}}`

<aside class="notice">
You must replace <code>bearerToken</code> with a valid OAuth token.
</aside>

# Users

## Get All Users

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

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

