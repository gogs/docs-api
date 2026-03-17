# Users

## Get a single user

```
GET /users/:username
```

> Request without providing basic authentication or access token will result empty `email` field for anti-spam purpose.

### Response

```
Status: 200 OK
```
```json
{
  "id": 1,
  "username": "unknwon",
  "full_name": "",
  "email": "fake@local",
  "avatar_url": "/avatars/1"
}
```

## Get the authenticated user

```
GET /user
```

### Response

```
Status: 200 OK
```
```json
{
  "id": 1,
  "username": "unknwon",
  "full_name": "",
  "email": "fake@local",
  "avatar_url": "/avatars/1"
}
```

## List access tokens for a user

List access tokens requires that you are authenticated via basic authentication.

```
GET /users/:username/tokens
```

### Response

```
Status: 200 OK
```
```json
[
  {
    "name": "how are you?",
    "sha1": "91e52ff55460eeb247e6423c8ca6e770263cdd8d"
  },
  {
    "name": "hi",
    "sha1": "dd8b56a38a61dc6bb240f2b4fe78ec0eb3fc2a0b"
  }
]
```

## Create a access token

Create a access token requires that you are authenticated via basic authentication.

```
POST /users/:username/tokens
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|name|string|**Required** Name of access token|

### Example

```json
{
    "name": "gogs"
}
```

### Response

```
Status: 201 Created
```
```json
{
  "name": "gogs",
  "sha1": "61d40add61894c11b14049b5ab189dc8f0500aef"
}
```
