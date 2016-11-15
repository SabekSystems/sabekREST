[![Docs](http://img.shields.io/badge/API-v1-00aced.svg?style=flat-square)](https://github.com/SabekSystems/sabekREST)

## API Documentation

>This API is useful for developers who want to consume the services of Sabek Systems.

### Introduction

**Base URL:**

`https://sabek.co.ke/api/v1`

**API Characteristics:**

- **JSON:** data back-and-forth is formatted in JSON
- **Status codes:** responses are sent back with sensible status codes
- **Fully Authenticated:** Authentication token is required on every request

### HTTP Statuses

```
200 - indicates that the request was fulfilled successfully and that no error was encountered.
4XX - indicates that either you did not authenticate correctly, you do not have authorization for the particular resource, that the object you are requesting does not exist, or that your request is malformed.
500 - indicates a serverside issue, contact webmaster
```

### Response

Responses will be sent in the form:

```js
{
  "status": 200,
  "data": [
    {
      "message_id": "S6767882hk"
    }
  ]
}
```

Where status is the HTTP response code and data/message is the response body

### API Authentication

#### Getting Your Access Token

You will need to login in intially to get your access token which lasts 7 days before it needs to be re-generated. Send a request as shown below:

```
POST /login HTTP/1.1
Content-Type: application/x-www-form-urlencoded

username={unique-id}
```

Where *unique-id* is the id provided by [Sabek Systems](https://github.com/SabekSystems)

N.B: username must be sent in the request body

On success, a response containg your token and expiry date is sent:

```js
{
  "status": 200,
  "token": "~",
  "expires": 1479835409315
}
```

#### Making Requests

All REST requests must contain the following headers:

`X-ACCESS-TOKEN` which is your access token as a string

#### Permissions

Only admins have authorization to access the Core API i.e:

`/core/*`

Clients can access other endpoints

### Endpoints

- `GET /core/admins`

Returns a list of all admins in the form:

```js
{
  "status": 200,
  "data": [{ ... }, ... { ... }]
}
```


- `GET /core/admin:email`

Returns details of a specific admin in the form:

```js
{
  "status": 200,
  "data": [{ ... }]
}
```

**More Endpoints Will be Added**


> Copyright © 2016 [Sabek Systems](https://github.com/SabekSystems)



