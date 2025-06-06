---
Title: Refresh JWT requests
alwaysopen: false
categories:
- docs
- operate
- rs
description: Refresh JW token requests
headerRange: '[1-2]'
linkTitle: refresh_jwt
weight: $weight
---

| Method | Path | Description |
|--------|------|-------------|
| [POST](#post-refresh_jwt) | `/v1/users/refresh_jwt` | Get a new authentication token |

## Get a new authentication token {#post-refresh_jwt}

    POST /v1/users/refresh_jwt

Generate a new JSON Web Token (JWT) for authentication.

Takes a valid token and returns the new token generated by the request.

### Request {#post-request} 

#### Example HTTP request

	POST /v1/users/refresh_jwt 

#### Request headers

| Key | Value | Description |
|-----|-------|-------------|
| Host | cnm.cluster.fqdn | Domain name |
| Authorization | JWT eyJ5bGciOiKIUzI1NiIsInR5cCI6IkpXVCJ9.<br></br>eyJpYXViOjE0NjU0NzU0ODYsInVpZFI1IjEiLCJ<br></br>leHAiOjE0NjU0Nz30OTZ9.2xYXumd1rDoE0e<br></br>dFzcLElMOHsshaqQk2HUNgdsUKxMU | Valid JSON Web Token (JWT) |

#### Request body

| Field | Type | Description |
|-------|------|-------------|
| ttl | integer | Time to live - The amount of time in seconds the token will be valid (optional) |

### Response {#post-response} 

Returns a JSON object that contains the generated access token.

#### Example JSON body

```json
 {
     "access_token": "eyJ5bGciOiKIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpYXViOjE0NjU0NzU0ODYsInVpZFI1IjEiLCJleHAiOjE0NjU0Nz30OTZ9.2xYXumd1rDoE0edFzcLElMOHsshaqQk2HUNgdsUKxMU"
 }
```



### Status codes {#post-status-codes} 

| Code | Description |
|------|-------------|
| [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) | A new token is given. |
| [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) | The token is invalid or password has expired. |
