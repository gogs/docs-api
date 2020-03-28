# Releases

## List Releases

```
GET /repos/:owner/:repo/releases
```

### Response

```
Status: 200 OK
```
```json
[
  {
    "id": 1,
    "tag_name": "sometag",
    "target_commitish": "master",
    "name": "awesome-release",
    "body": "Description of the release",
    "draft": false,
    "prerelease": false,
    "author": {
      "id": 1,
      "username": "Author Name",
      "login": "",
      "full_name": "",
      "email":"author@email.com",
      "avatar_url": ""
    },
    "created_at": "2020-03-28T13:38:00+03:00"
  }
]
```
