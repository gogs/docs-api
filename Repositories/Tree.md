# Tree

## List Repository Tree

```
GET /repos/:owner/:repo/git/trees/:sha
```

### Response

```
Status: 200 OK
```
```json
{
  "sha": "c59441ded1549b149def0d4c54594d31a7f3718f",
  "url": "http://localhost:3000/api/v1/repos/root/testrepo/git/trees/c59441ded1549b149def0d4c54594d31a7f3718f",
  "tree": [
    {
      "path": "LICENSE",
      "mode": "120000",
      "type": "blob",
      "size": 1077,
      "sha": "472ac2361b65136b393d652de25341e2ea44f299",
      "url": "http://localhost:3000/api/v1/repos/root/testrepo/git/trees/472ac2361b65136b393d652de25341e2ea44f299"
    },
    {
      "path": "README.md",
      "mode": "120000",
      "type": "blob",
      "size": 12,
      "sha": "70fcb456d436f08462602f26df6fb7e167e7a916",
      "url": "http://localhost:3000/api/v1/repos/root/testrepo/git/trees/70fcb456d436f08462602f26df6fb7e167e7a916"
    }
  ]
}
```