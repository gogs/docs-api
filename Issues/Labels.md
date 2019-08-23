# Labels

## List all labels for a repository

```
GET /repos/:username/:reponame/labels
```

### Response

```
Status: 200 OK
```
```json
[
  {
    "id": 3,
    "name": "feature",
    "color": "#70c24a"
  },
  {
    "id": 4,
    "name": "bug",
    "color": "#e11d21"
  },
  {
    "id": 5,
    "name": "enhancement",
    "color": "#207de5"
  }
]
```

## Get a single label

```
GET /repos/:username/:reponame/labels/:id
```

### Response

```
Status: 200 OK
```
```json
{
  "id": 3,
  "name": "feature",
  "color": "#70c24a"
}
```

## Create a label

```
POST /repos/:username/:reponame/labels
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|name|string|**Required** The name of the label|
|color|string|**Required** A 7 character hex code with the leading #, identifying the color|

### Example

```json
{
  "name": "something",
  "color": "#123123"
}
```

### Response

```
Status: 201 Created
```
```json
{
  "id": 7,
  "name": "something",
  "color": "#123123"
}
```

## Update a label

```
PATCH /repos/:username/:reponame/labels/:id
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|name|string|The name of the label|
|color|string|A 7 character hex code with the leading #, identifying the color|

## Delete a label

```
DELETE /repos/:username/:reponame/labels/:id
```

### Response

```
Status: 204 No Content
```

## List labels on an issue

```
GET /repos/:username/:reponame/issues/:index/labels
```

### Response

```
Status: 200 OK
```
```json
[
  {
    "id": 3,
    "name": "feature",
    "color": "#70c24a"
  },
  {
    "id": 4,
    "name": "bug",
    "color": "#e11d21"
  },
  {
    "id": 5,
    "name": "enhancement",
    "color": "#207de5"
  }
]
```

## Add labels to an issue

```
POST /repos/:username/:reponame/issues/:index/labels
```

### Example

```json
{
	"labels": [3,4]
}
```

### Response

```
Status: 200 OK
```
```json
[
  {
    "id": 3,
    "name": "feature",
    "color": "#70c24a"
  },
  {
    "id": 4,
    "name": "bug",
    "color": "#e11d21"
  },
  {
    "id": 5,
    "name": "enhancement",
    "color": "#207de5"
  }
]
```

## Remove a label from an issue

```
DELETE /repos/:username/:reponame/issues/:index/labels/:id
```

### Response

```
Status: 204 No Content
```

## Replace all labels for an issue

```
PUT /repos/:username/:reponame/issues/:index/labels
```

### Example

```json
{
	"labels": [5,6]
}
```

### Response

```
Status: 200 OK
```
```json
[
  {
    "id": 5,
    "name": "enhancement",
    "color": "#207de5"
  },
  {
    "id": 6,
    "name": "feature",
    "color": "#70c24a"
  }
]
```

## Remove all labels from an issue

```
DELETE /repos/:username/:reponame/issues/:index/labels
```

### Response

```
Status: 204 No Content
```
