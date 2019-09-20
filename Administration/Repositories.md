# Repositories Administration

## Create a new repository

Create a new repository for a user or organization.

```
POST /admin/users/:username/repos
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|name|string|**Required** The name of the repository|
|description|string|A short description of the repository|
|private|bool|Either **true** to create a private repository, or **false** to create a public one. Default is **false**|
|auto_init|bool|Pass **true** to create an initial commit with README, .gitignore and LICENSE. Default is **false**|
|gitignores|string|Desired [language .gitignore templates](https://github.com/gogs/gogs/tree/master/conf/gitignore) to apply. Use the name of the templates. For example, "Go" or "Go,SublimeText".|
|license|string|Desired [LICENSE template](https://github.com/gogs/gogs/tree/master/conf/license) to apply. Use the name of the template. For example, "Apache v2 License" or "MIT License".|
|readme|string|Desired README template to apply. Use the name of the template. Default is **Default**|

### Example

```json
{
  "name": "Hello-World",
  "description": "This is your first repository",
  "private": false
}
```

### Response

```
Status: 201 Created
```
```json
{
  "id": 27,
  "owner": {
    "id": 1,
    "username": "unknwon",
    "full_name": "",
    "email": "fake@local",
    "avatar_url": "/avatars/1"
  },
  "full_name": "unknwon/Hello-World",
  "private": false,
  "fork": false,
  "html_url": "https://try.gogs.io/unknwon/Hello-World",
  "clone_url": "https://try.gogs.io/unknwon/hello-world.git",
  "ssh_url": "git@try.gogs.io:unknwon/hello-world.git",
  "permissions": {
    "admin": true,
    "push": true,
    "pull": true
  }
}
```
