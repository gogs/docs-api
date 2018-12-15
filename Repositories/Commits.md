# Commits

## Get a single commit

```
GET /repos/:username/:reponame/commits/:sha
```

### Response

```
Status: 200 OK
```
```json
{
  "url": "https://try.gogs.io/api/v1/repos/unknwon/demo/commits/dc20792485ffd49b0bca49f90a8d44a16241b84a",
  "sha": "dc20792485ffd49b0bca49f90a8d44a16241b84a",
  "html_url": "https://try.gogs.io/unknwon/demo/commits/dc20792485ffd49b0bca49f90a8d44a16241b84a",
  "commit": {
    "url": "https://try.gogs.io/api/v1/repos/unknwon/demo/commits/dc20792485ffd49b0bca49f90a8d44a16241b84a",
    "author": {
      "name": "unknwon",
      "email": "u@gogs.io",
      "date": "2018-12-10T23:51:52-05:00"
    },
    "committer": {
      "name": "unknwon",
      "email": "u@gogs.io",
      "date": "2018-12-10T23:51:52-05:00"
    },
    "message": "Update 'README.md'",
    "tree": {
      "url": "https://try.gogs.io/api/v1/repos/unknwon/demo/tree/dc20792485ffd49b0bca49f90a8d44a16241b84a",
      "sha": "dc20792485ffd49b0bca49f90a8d44a16241b84a"
    }
  },
  "author": {
    "id": 1,
    "username": "unknwon",
    "login": "unknwon",
    "full_name": "",
    "email": "u@gogs.io",
    "avatar_url": "https://secure.gravatar.com/avatar/d8b2871cdac01b57bbda23716cc03b96"
  },
  "committer": {
    "id": 1,
    "username": "unknwon",
    "login": "unknwon",
    "full_name": "",
    "email": "u@gogs.io",
    "avatar_url": "https://secure.gravatar.com/avatar/d8b2871cdac01b57bbda23716cc03b96"
  },
  "parents": [
    {
      "url": "https://try.gogs.io/api/v1/unknwon/demo/commits/9227a50146b3fd815fe864af99b984c77d06326a",
      "sha": "9227a50146b3fd815fe864af99b984c77d06326a"
    }
  ]
}
```