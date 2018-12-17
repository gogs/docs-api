# Milestones

## List milestones for a repository

```
GET /repos/:owner/:repo/milestones
```

### Response

```
Status: 200 OK
```
```json
[
  {
    "id":2,
    "state":"closed",
    "title":"1.0",
    "description":"Initial release",
    "open_issues":0,
    "closed_issues":12,
    "closed_at":"2016-07-04T14:37:05-07:00",
    "due_on":"2016-07-04T00:00:00-07:00"
  },
  {
    "id":4,
    "state":"open",
    "title":"1.0",
    "description":"Fix pack 1",
    "open_issues":5,
    "closed_issues":3,
    "closed_at":null,
    "due_on":"2016-09-06T00:00:00-07:00"
  }
]
```

## Get a single milestone

```
GET /repos/:owner/:repo/milestones/:id
```

### Response

```
Status: 200 OK
```
```json
{
  "id":4,
  "state":"open",
  "title":"1.0",
  "description":"Fix pack 1",
  "open_issues":5,
  "closed_issues":3,
  "closed_at":null,
  "due_on":"2016-09-06T00:00:00-07:00"
}
```

## Create a milestone

Only users with write access to a repository can perform this action.

```
POST /repos/:owner/:repo/milestones
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|title|string|The title of the milestone|
|description|string|The description of the milestone |
|due_on|time|The due date e.g., "2016-09-06T00:00:00-07:00" |

### Example

```json
{
  "title":"1.0.1",
  "description":"Fix pack 1",
  "due_on":"2016-09-06T00:00:00-07:00"
}
```

### Response

```
Status: 201 Created
```
```json
{
  "id":4,
  "state":"open",
  "title":"1.0.1",
  "description":"Fix pack 1",
  "open_issues":0,
  "closed_issues":0,
  "closed_at":null,
  "due_on":"2016-09-06T00:00:00-07:00"
}
```

## Edit a milestone

Repository owners and users with write access can perform this action.

```
PATCH /repos/:owner/:repo/milestones/:id
```

### Parameters

Leave value empty to remain unchanged.

|Name|Type|Description|
|----|----|-----------|
|title|string|The title of the milestone|
|description|string|The description of the milestone |
|due_on|time|The due date e.g., "2016-09-06T00:00:00-07:00" |
|state|string|Either "open" or "closed"|

## Delete a milestone

Only users with write access to a repository can perform this action.

```
DELETE /repos/:owner/:repo/milestones/:id
```

### Response

```
Status: 204 No Content
```