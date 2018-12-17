# Issues

## List issues for a repository

This endpoint may also return pull requests in the response. If an issue is a pull request, the object will include a `pull_request` key.

```
GET /repos/:owner/:repo/issues
```

### Response

```
Status: 200 OK
Link: <http://localhost:3000/api/v1/repos/unknwon/issue-1146/issues?page=2>; rel="next",<http://localhost:3000/api/v1/repos/unknwon/issue-1146/issues?page=2>; rel="last"
```
```json
[
  {
    "id": 74,
    "number": 3,
    "state": "open",
    "title": "this feature is broken!!",
    "body": "好样的！",
    "user": {
      "id": 4,
      "username": "user2",
      "full_name": "",
      "email": "user2@user.com",
      "avatar_url": "https://secure.gravatar.com/avatar/634cbb8402cb7d3dc74018b51fa388de"
    },
    "labels": [
      {
        "name": "kind/bug",
        "color": "#e11d22"
      }
    ],
    "assignee": null,
    "milestone": {
      "id": 1,
      "state": "open",
      "title": "0.11",
      "description": "",
      "open_issues": 2,
      "closed_issues": 1,
      "closed_at": null,
      "due_on": null
    },
    "comments": 3,
    "pull_request": null,
    "created_at": "2016-03-05T14:56:48-05:00",
    "updated_at": "2016-03-05T15:15:01-05:00"
  },
  {
    "id": 73,
    "number": 2,
    "state": "open",
    "title": "great!",
    "body": "",
    "user": {
      "id": 3,
      "username": "user1",
      "full_name": "",
      "email": "joe2010xtmf@163.com",
      "avatar_url": "https://secure.gravatar.com/avatar/0207f4280f6c1bd45e1a2ed7cb1cca3d"
    },
    "labels": [
      {
        "name": "boot2docker",
        "color": "#207de5"
      }
    ],
    "assignee": {
      "id": 1,
      "username": "unknwon",
      "full_name": "无闻",
      "email": "fake@local",
      "avatar_url": "/avatars/1"
    },
    "milestone": {
      "id": 1,
      "state": "open",
      "title": "0.11",
      "description": "",
      "open_issues": 2,
      "closed_issues": 1,
      "closed_at": null,
      "due_on": null
    },
    "comments": 0,
    "pull_request": null,
    "created_at": "2016-03-05T14:54:46-05:00",
    "updated_at": "2016-03-05T14:54:46-05:00"
  }
]
```

## Get a single issue

This endpoint may also return pull requests in the response. If an issue is a pull request, the object will include a `pull_request` key.

```
GET /repos/:owner/:repo/issues/:index
```

### Response

```
Status: 200 OK
```
```json
{
  "id": 72,
  "number": 1,
  "state": "open",
  "title": "test issue",
  "body": "",
  "user": {
    "id": 3,
    "username": "user1",
    "full_name": "",
    "email": "fake@local",
    "avatar_url": "https://secure.gravatar.com/avatar/0207f4280f6c1bd45e1a2ed7cb1cca3d"
  },
  "labels": [],
  "assignee": null,
  "milestone": null,
  "comments": 1,
  "pull_request": null,
  "created_at": "2016-03-05T13:18:51-05:00",
  "updated_at": "2016-03-05T13:18:51-05:00"
}
```

## Create an issue

Any user with read access to a repository can create an issue.

```
POST /repos/:owner/:repo/issues
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|title|string|The title of the issue|
|body|string|The contents of the issue|
|assignee|string|Username for the user that this issue should be assigned to. *NOTE: Only users with write access can set the assignee for new issues. The assignee is silently dropped otherwise.*|
|milestone|int|The **ID** of the milestone to associate this issue with. *NOTE: Only users with write access can set the milestone for new issues. The milestone is silently dropped otherwise.*|
|labels|array of int|Labels **ID** to associate with this issue. *NOTE: Only users with write access can set labels for new issues. Labels are silently dropped otherwise.*|
|closed|bool|Indicate initial issue state as closed (**true**) or open (**false**). The default is **false**.|

### Example

```json
{
  "title": "Found a bug",
  "body": "I'm having a problem with this.",
  "assignee": "unknwon",
  "milestone": 1,
  "labels": [
    "Label1",
    "Label2"
  ]
}
```

## Edit an issue

Issue owners and users with write access can edit an issue.

```
PATCH /repos/:owner/:repo/issues/:index
```

### Parameters

Leave value empty to remain unchanged.

|Name|Type|Description|
|----|----|-----------|
|title|string|The title of the issue|
|body|string|The contents of the issue|
|assignee|string|Username for the user that this issue should be assigned to. *NOTE: Only users with write access can set the assignee for new issues. The assignee is silently dropped otherwise.*|
|milestone|int|The **ID** of the milestone to associate this issue with. *NOTE: Only users with write access can set the milestone for new issues. The milestone is silently dropped otherwise.*|
|state|string|Either "open" or "closed"|
