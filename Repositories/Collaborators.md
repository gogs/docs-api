# Collaborators

## Add user as a collaborator

```
PUT /repos/:username/:reponame/collaborators/:collaborator
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|permission|string|The permission to grant the collaborator. Can be one of **read**, **write** and **admin**. Default is **write**. Read details on [forum](https://discuss.gogs.io/t/how-to-manage-collaborators/87)|

## Get collaborators

```
GET /repos/:username/:reponame/collaborators
```

### Response

```
Status: 200 OK
```
```json
[
  {
    "id": 3,
    "username": "user1",
    "login": "user1",
    "full_name": "",
    "email": "user1@user.com",
    "avatar_url": "https://secure.gravatar.com/avatar/0207f4280f6c1bd45e1a2ed7cb1cca3d",
    "permissions": {
      "admin": false,
      "push": true,
      "pull": true
    }
  }
]
```