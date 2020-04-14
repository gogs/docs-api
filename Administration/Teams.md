# Teams Administration

## List all members of a team

```
GET /admin/teams/:teamid/members
```

### Response

```
Status: 200 OK
```
```json
[
  {
    "id": 1,
    "username": "gogs",
    "login": "gogs",
    "full_name": "Gogs",
    "email": "user@email.com",
    "avatar_url": "https://secure.gravatar.com/..."
  },
  {
    "id": 2,
    "username": "gogs-2",
    "login": "gogs-2",
    "full_name": "Gogs 2",
    "email": "user-2@email.com",
    "avatar_url": "https://secure.gravatar.com/..."
  }
]
```

## Add team membership

```
PUT /admin/teams/:teamid/members/:username
```

### Response

```
Status: 204 No Content
```

## Remove team membership

```
DELETE /admin/teams/:teamid/members/:username
```

### Response

```
Status: 204 No Content
```

## Add or update team repository

```
PUT /admin/teams/:teamid/repos/:reponame
```

### Response

```
Status: 204 No Content
```

## Remove team repository

```
DELETE /admin/teams/:teamid/repos/:reponame
```

### Response

```
Status: 204 No Content
```
