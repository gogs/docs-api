# Organization Administration

## Create a new organization

```
POST /admin/users/:username/orgs
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|username|string|**Required** Organization user name|
|full_name|string|Full name of organization|
|description|string|Description to the organization|
|website|string|Official website|
|location|string|Organization location|

### Example

```json
{
  "username": "gogs",
  "full_name": "Gogs",
  "description": "Gogs is a painless self-hosted Git Service.",
  "website": "https://gogs.io",
  "location": "USA"
}
```

### Response

```
Status: 201 Created
```
```json
{
  "id": 7,
  "username": "gogs",
  "full_name": "Gogs",
  "avatar_url": "/avatars/7",
  "description": "Gogs is a painless self-hosted Git Service.",
  "website": "https://gogs.io",
  "location": "USA"
}
```

## Create team of an organization

```
POST /admin/orgs/:orgname/teams
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|name|string|**Required** Team name|
|description|string|Description to the team|
|permission|string|Team permission, can be **read**, **write** or **admin**, default is **read**|

### Example

```json
{
  "name": "new-team",
  "description": "A new team created by API",
  "permission": "write"
}
```

### Response

```
Status: 201 Created
```
```json
{
  "id": 12,
  "name": "new-team",
  "description": "A new team created by API",
  "permission": "write"
}
```
