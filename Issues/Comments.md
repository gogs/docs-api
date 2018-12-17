# Comments

## List comments on an issue

Issue Comments are ordered by ascending ID.

```
GET /repos/:username/:reponame/issues/:index/comments
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|since|string|Only comments updated at or after this time are returned. This is a timestamp in RFC3339 format: **2006-01-02T15:04:05Z07:00**, e.g. **2017-06-27T15:04:05-04:00**|

### Response

```
Status: 200 OK
```
```json
[
  {
    "id": 74,
    "user": {
      "id": 1,
      "username": "unknwon",
      "full_name": "无闻",
      "email": "fake@local",
      "avatar_url": "http://localhost:3000/avatars/1"
    },
    "body": "what?",
    "created_at": "2016-08-26T11:58:18-07:00",
    "updated_at": "2016-08-26T11:58:18-07:00"
  },
  {
    "id": 75,
    "user": {
      "id": 1,
      "username": "unknwon",
      "full_name": "无闻",
      "email": "fake@local",
      "avatar_url": "http://localhost:3000/avatars/1"
    },
    "body": "awesome!!",
    "created_at": "2016-08-26T11:58:24-07:00",
    "updated_at": "2016-08-26T11:58:24-07:00"
  },
  {
    "id": 76,
    "user": {
      "id": 1,
      "username": "unknwon",
      "full_name": "无闻",
      "email": "fake@local",
      "avatar_url": "http://localhost:3000/avatars/1"
    },
    "body": "this is awesome?",
    "created_at": "2016-08-26T12:21:28-07:00",
    "updated_at": "2016-08-26T12:21:28-07:00"
  }
]
```

## List comments of an issue for a given repository

Issue comments are ordered by ascending ID.

```
GET /repos/:username/:reponame/issues/comments
```

### Parameters

| Name | Type | Description |
| --- | --- | --- |
| since | string | Only comments updated at or after this time are returned. This is a timestamp in RFC3339 format: **2006-01-02T15:04:05Z07:00**|

### Response

```
Status: 200 OK
```
``` json
[
  {
    "id": 74,
    "user": {
      "id": 1,
      "username": "unknwon",
      "full_name": "无闻",
      "email": "fake@local",
      "avatar_url": "http://localhost:3000/avatars/1"
    },
    "body": "what?",
    "created_at": "2016-08-26T11:58:18-07:00",
    "updated_at": "2016-08-26T11:58:18-07:00"
  }
]
```

## Create a comment

```
POST /repos/:username/:reponame/issues/:index/comments
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|body|string|**Required** The contents of the comment.|

### Example

```json
{
    "body": "Me too"
}
```

### Response

```
Status: 201 Created
```
```json
{
"id": 68,
"user": {
    "id": 1,
    "username": "unknwon",
    "full_name": "无闻",
    "email": "fake@local",
    "avatar_url": "http://localhost:3000/avatars/1"
},
"body": "Me too",
"created_at": "2016-08-16T09:44:00-07:00",
"updated_at": "2016-08-26T13:51:28-07:00"
}
```

## Edit a comment

```
PATCH /repos/:username/:reponame/issues/:index/comments/:id
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|body|string|**Required** The contents of the comment.|

## Delete a Issue-comment

```
DELETE /repos/:username/:reponame/issues/:index/comments/:id
```

### Response

```
Status: 204 No Content
```
