# User Administration

## Create a new user

```
POST /admin/users
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|source_id|int|Authentication source ID. Remain default means a local user|
|login_name|string|Authentication source login name, **required** for non-local user|
|username|string|**Required** Unique user name|
|email|string|**Required** Unique email address of user|
|password|string|Default password for user, **required** for local user|
|send_notify|bool|Send a notification email for this creation, require mailer service enabled|

### Example

```json
{
    "source_id": 1,
    "login_name": "apiuser",
    "username": "apiuser",
    "email": "apiuser@user.com"
}
```

### Response

```
Status: 201 Created
```
```json
{
  "id": 9,
  "username": "apiuser",
  "full_name": "",
  "email": "apiuser@user.com",
  "avatar_url": "//1.gravatar.com/avatar/0550f43afcac6f78c3af2dd3a6f1c176"
}
```

## Edit an existing user

```
PATCH /admin/users/:username
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|source_id|int|Authentication source ID. Remain default means a local user|
|login_name|string|Authentication source login name, **required** for non-local user|
|full_name|string|Full name of user|
|email|string|**Required** Unique email address of user|
|password|string|New password for user. Ignore this field to leave it unchanged|
|website|string|Personal website of user|
|location|string|Location of user|
|active|bool|Active or deactive the user. Ignore this field to leave it unchanged|
|admin|bool|Promote or depromote the user to be site admin. Ignore this field to leave it unchanged|
|allow_git_hook|bool|Allow or disallow the user for using Git hooks. Ignore this field to leave it unchanged|
|allow_import_local|bool|Allow or disallow the user for importing local repositories. Ignore this field to leave it unchanged|

### Example

```json
{
    "source_id":1,
    "login_name":"apiuser",
    "full_name": "API User",
    "email":"apiuser@user.com"
}
```

### Response

```
Status: 200 OK
```
```json
{
  "id": 9,
  "username": "apiuser",
  "full_name": "API User",
  "email": "apiuser@user.com",
  "avatar_url": "//1.gravatar.com/avatar/b7193b9f212a6fe7a20db58d556fcc41"
}
```

## Delete a user

```
DELETE /admin/users/:username
```

### Response

```
Status: 204 No Content
```

## Create a public key for user

```
POST /admin/users/:username/keys
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|title|string|**Required** The name of the key|
|key|string|**Required** The content of the key|
