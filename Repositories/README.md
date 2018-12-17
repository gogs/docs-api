# Repositories

## Search repositories

```
GET /repos/search
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|q|string|**Required** Keyword of username|
|uid|int|User ID to specify search whose repositories. Default is **0** and search all repositories|
|limit|int|Limit number of search results. Default is **10**|
|page|int|Page number. Default is **1**|

### Example

```
$ curl https://try.gogs.io/api/v1/repos/search?q=u&uid=1&limit=5
```

### Response

```
Status: 200 OK
```
```json
{
  "data": [
    {
      "id": 1717,
      "owner": {
        "id": 0,
        "username": "",
        "full_name": "",
        "email": "",
        "avatar_url": ""
      },
      "full_name": "unknwon/Issue-966",
      "private": false,
      "fork": false,
      "html_url": "",
      "clone_url": "",
      "ssh_url": "",
      "permissions": {
        "admin": false,
        "push": false,
        "pull": false
      }
    },
    {
      "id": 154,
      "owner": {
        "id": 0,
        "username": "",
        "full_name": "",
        "email": "",
        "avatar_url": ""
      },
      "full_name": "unknwon/issue935",
      "private": false,
      "fork": false,
      "html_url": "",
      "clone_url": "",
      "ssh_url": "",
      "permissions": {
        "admin": false,
        "push": false,
        "pull": false
      }
    }
  ],
  "ok": true
}
```

## List your repositories

List repositories that are accessible to the authenticated user.

This includes repositories owned by the authenticated user, repositories where the authenticated user is a collaborator, and repositories that the authenticated user has access to through an organization membership.

```
GET /user/repos
```

### Response

```
Status: 200 OK
```
```json
[
  {
    "id": 2,
    "owner": {
      "id": 1,
      "username": "unknwon",
      "full_name": "",
      "email": "fake@local",
      "avatar_url": "/avatars/1"
    },
    "full_name": "unknwon/macaron",
    "private": false,
    "fork": false,
    "html_url": "http://localhost:3000/unknwon/macaron",
    "clone_url": "http://localhost:3000/unknwon/macaron.git",
    "ssh_url": "jiahuachen@localhost:unknwon/macaron.git",
    "permissions": {
      "admin": true,
      "push": true,
      "pull": true
    }
  },
  {
    "id": 8,
    "owner": {
      "id": 2,
      "username": "org1",
      "full_name": "org1",
      "email": "org1@org.com",
      "avatar_url": "/avatars/2"
    },
    "full_name": "org1/gogs",
    "private": false,
    "fork": false,
    "html_url": "http://localhost:3000/org1/gogs",
    "clone_url": "http://localhost:3000/org1/gogs.git",
    "ssh_url": "jiahuachen@localhost:org1/gogs.git",
    "permissions": {
      "admin": true,
      "push": true,
      "pull": true
    }
  }
]
```

## List user repositories

List public repositories for the specified user.

```
GET /users/:username/repos
```

## List organization repositories

List repositories that are accessible to the authenticated user.

```
GET /orgs/:orgname/repos
```

## Create

Create a new repository for the authenticated user.

```
POST /user/repos
```

Create a new repository in this organization. The authenticated user must be a **owner** of the specified organization.

```
POST /org/:org/repos
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

##### Litte notes on README template

If you have created file on your corresponding `custom/conf/readme/My README`, then use "My README".

Currently, you can use following placeholder for corresponding values of repository:

- `{Name}`: Repository name
- `{Description}`: Repository description
- `{CloneURL.SSH}`: Repository SSH clone address
- `{CloneURL.HTTPS}`: Repository HTTP/HTTPS clone address

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

## Migrate

Migrate a repository from other Git hosting sources for the authenticated user.

```
POST /repos/migrate
```

To migrate a repository for a organization, the authenticated user must be a **owner** of the specified organization.

### Parameters

|Name|Type|Description|
|----|----|-----------|
|`clone_addr`|string|**Required** Remote Git address (HTTP/HTTPS URL or local path)|
|`auth_username`|string|Authorization username|
|`auth_password`|string|Authorization password|
|`uid`|int|**Required** User ID who takes ownership of this repository|
|`repo_name`|string|**Required** Repository name|
|`mirror`|bool|Repository will be a mirror. Default is **false**|
|`private`|bool|Repository will be private. Default is **false**|
|`description`|string|Repository description|

### Example

```json
{
  "clone_addr": "https://github.com/Unknwon/macaron",
  "uid": 1,
  "repo_name": "hello-macaron"
}
```

### Response

```
Status: 201 Created
```
```json
{
  "id": 19,
  "owner": {
    "id": 1,
    "username": "unknwon",
    "full_name": "",
    "email": "fake@local",
    "avatar_url": "//1.gravatar.com/avatar/d8b2871cdac01b57bbda23716cc03b96"
  },
  "full_name": "unknwon/hello-macaron",
  "private": false,
  "fork": false,
  "html_url": "https://try.gogs.io:3000/unknwon/hello-macaron",
  "clone_url": "https://try.gogs.io:3000/unknwon/hello-macaron.git",
  "ssh_url": "git@try.gogs.io:unknwon/hello-macaron.git",
  "permissions": {
    "admin": true,
    "push": true,
    "pull": true
  }
}
```

## Get

Get information of a single repository.

```
GET /repos/:owner/:repo
```

### Response

```
Status: 200 OK
```
```json
{
  "id": 19,
  "owner": {
    "id": 1,
    "username": "unknwon",
    "full_name": "",
    "email": "fake@local",
    "avatar_url": "//1.gravatar.com/avatar/d8b2871cdac01b57bbda23716cc03b96"
  },
  "full_name": "unknwon/hello-macaron",
  "private": false,
  "fork": false,
  "html_url": "https://try.gogs.io/unknwon/hello-macaron",
  "clone_url": "https://try.gogs.io/unknwon/hello-macaron.git",
  "ssh_url": "git@try.gogs.io:unknwon/hello-macaron.git",
  "permissions": {
    "admin": true,
    "push": true,
    "pull": true
  }
}
```

## Delete

Deleting a repository requires owner access of repository.

```
DELETE /repos/:owner/:repo
```

### Response

```
Status: 204 No Content
```

## Edit Issue Tracker

```
PATCH /repos/:owner/:repo/issue-tracker
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|`enable_issues`|bool|Enable issue tracker for the repository. Ignore this field to leave it unchanged|
|`enable_external_tracker`|bool|Enable external issue tracker for the repository. Ignore this field to leave it unchanged|
|`external_tracker_url`|string|The URL of the external issue tracker. Ignore this field to leave it unchanged|
|`tracker_url_format`|string|The URL format of the external issue tracker. Ignore this field to leave it unchanged|
|`tracker_issue_style`|string|The naming style of the issue, can be **numeric** or **alphanumeric**. Ignore this field to leave it unchanged|

### Example

```json
{
  "enable_issues": true,
  "enable_external_tracker": true,
  "external_tracker_url": "https://github.com/gogs/gogs/issues",
  "tracker_url_format": "https://github.com/gogs/{repo}/issues/{index}"
}
```

### Response

```
Status: 204 No Content
```

## Mirror Sync

Add mirror repository to sync queue on behalf of the authenticated user. If the repository is not a mirror, 404 will be returned.

```
POST /repos/:owner/:repo/mirror-sync
```

### Response

```
Status: 202 Accepted
```