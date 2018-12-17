# Organizations

## List your organizations

List organizations for the authenticated user.

```
GET /user/orgs
```

### Response

```
Status: 200 OK
```
```json
[
  {
    "id": 6,
    "username": "gogs",
    "full_name": "Gogs",
    "avatar_url": "/avatars/6",
    "description": "Gogs is a painless self-hosted Git Service.",
    "website": "https://gogs.io",
    "location": "USA"
  }
]
```

## List user organizations

List public organization memberships for the specified user.

```
GET /users/:username/orgs
```

### Response

```
Status: 200 OK
```
```json
[
  {
    "id": 6,
    "username": "gogs",
    "full_name": "Gogs",
    "avatar_url": "/avatars/6",
    "description": "Gogs is a painless self-hosted Git Service.",
    "website": "https://gogs.io",
    "location": "USA"
  }
]
```

## Get an organization

```
GET /orgs/:orgname
```

### Response

```
Status: 200 OK
```
```json
{
  "id": 6,
  "username": "gogs",
  "full_name": "Gogs",
  "avatar_url": "/avatars/6",
  "description": "Gogs is a painless self-hosted Git Service.",
  "website": "https://gogs.io",
  "location": "USA"
}
```

## Edit an organization

```
PATCH /orgs/:org
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|full_name|string|Full name of organization|
|description|string|Description to the organization|
|website|string|Official website|
|location|string|Organization location|

### Example

```json
{
  "full_name": "Gogs2",
  "description": "Gogs is a painless self-hosted Git Service.",
  "website": "https://gogs.io",
  "location": "USA"
}
```

### Response

```
Status: 200 OK
```
```json
{
  "id": 6,
  "username": "gogs",
  "full_name": "Gogs2",
  "avatar_url": "/avatars/6",
  "description": "Gogs is a painless self-hosted Git Service.",
  "website": "https://gogs.io",
  "location": "USA"
}
```
