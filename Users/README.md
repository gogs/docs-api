# Users

## Search users

```
GET /users/search
```

> Request without providing basic authentication or access token will result empty `email` field for anti-spam purpose.

### Parameters

|Name|Type|Description|
|----|----|-----------|
|q|string|**Required** Keyword of username|
|limit|int|Limit number of search results. Default is **10**|

### Example

```
$ curl https://try.gogs.io/api/v1/users/search?q=u&limit=5
```

### Response

```
Status: 200 OK
```
```json
{
  "data": [
    {
      "id": 1,
      "username": "unknwon",
      "full_name": "",
      "email": "fake@local",
      "avatar_url": "/avatars/1"
    },
    {
      "id": 4,
      "username": "user1",
      "full_name": "",
      "email": "user1@user.com",
      "avatar_url": "/avatars/4"
    }
  ],
  "ok": true
}
```

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

## Create an access token

Creating an access token requires that you are authenticated via basic authentication.

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

## Delete an access token

Deleting an access token requires that you are authenticated via basic authentication.

```
DELETE /users/:username/tokens
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|sha1|string|**Required** SHA1 of access token|

### Example

```json
{
    "sha1": "61d40add61894c11b14049b5ab189dc8f0500aef"
}
```

### Response

```
Status: 200 OK
```
```json
{
  "name": "name_of_deleted_key",
  "sha1": ""
}
```
