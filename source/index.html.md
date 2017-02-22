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

> To authorize, use this code:

```shell
curl --request POST \
  --url http://example.curatr3.com/oauth/access_token \
  --form grant_type=client_credentials \
  --form client_id=CLIENT_ID \
  --form client_secret=CLIENT_SECRET
```

> The above command returns JSON structured like this:

```json
[
  {
    "access_token": "49vg4POxZ5vkcPgixKDkreYhEQVscAqPNXqV64eE",
    "token_type": "Bearer",
    "expires_in": 3600
  }
]
```

> Make sure to replace `CLIENT_ID` and `CLIENT_SECRET` with the correct credentials for your organisation.


This endpoint gets a new OAuth access token.

### HTTP Request

`POST http://example.curatr3.com/oauth/access_token`

### Body Parameters

Parameter | Default | Description
--------- | ------- | -----------
grant_type | client_credentials | This will almways be 'client_credentials'
client_id | - | Your unique client ID
client_secret | - | Your unique client secret


## Use an access token

This endpoint gets a new OAuth access token.
Curatr uses OAuth to authenticate API connections.

Curatr expects for the OAuth token to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer {{bearerToken}}`

<aside class="notice">
You must replace <code>bearerToken</code> with a valid OAuth token.
</aside>

# Users

## Get All Users

> To authorize, use this code:

```shell
curl --request GET \
  --url 'http://example.curatr3.com/api/v2/users' \
  --header 'authorization: Bearer {{oauth_access_token}}'
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

This endpoint retrieves all Users in your organisation.

### HTTP Request

`GET http://example.curatr3.com/api/v2/users`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
filter | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

## Get a Specific User

```shell
curl --request GET \
  --url 'http://example.curatr3.com/api/v2/users/2' \
  --header 'authorization: Bearer {{oauth_access_token}}'
```

> The above command returns JSON structured like this:

```json
{
    "id": 2,
    "fname": "Albus",
    "lname": "Dumbledore",
    "email": "a.dumbledore@hogwarts.edu",
    "username": "a.dumbledore"
}
```

This endpoint retrieves a specific user.

### HTTP Request

`GET http://example.curatr3.com/api/v2/users/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the user to retrieve

