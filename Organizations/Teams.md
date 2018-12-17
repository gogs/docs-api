# Teams

## List teams of an organization

```
GET /orgs/:orgname/teams
```

### Response

```
Status: 200 OK
```
```json
[
  {
    "id": 4,
    "name": "Owners",
    "description": "",
    "permission": "owner"
  },
  {
    "id": 5,
    "name": "Members",
    "description": "",
    "permission": "read"
  },
  {
    "id": 11,
    "name": "api-team",
    "description": "",
    "permission": "write"
  }
]
```
