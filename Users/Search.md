# Search users

```
GET /users/search
```

> Request without providing basic authentication or access token will result empty `email` field for anti-spam purpose.

### Parameters

|Name|Type|Description|
|----|----|-----------|
|q|string|**Required** Keyword of username|
|field|string|What field to search on. Only allows `name` (default) and `email`|
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
