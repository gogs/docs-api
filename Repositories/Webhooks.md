# Webhooks

## List hooks

```
GET /repos/:username/:reponame/hooks
```

### Response

```
Status: 200 OK
```
```json
[
  {
    "id": 14,
    "type": "gogs",
    "events": [
      "create",
      "push"
    ],
    "active": true,
    "config": {
      "content_type": "json",
      "url": "http://127.0.0.1:3000/unknwon/repo1/settings/hooks/14"
    },
    "updated_at": "2015-08-29T18:25:52+08:00",
    "created_at": "2015-08-27T20:17:36+08:00"
  },
  {
    "id": 15,
    "type": "slack",
    "events": [
      "create",
      "push"
    ],
    "active": true,
    "config": {
      "channel": "#gogs",
      "color": "good",
      "content_type": "json",
      "icon_url": "https://try.gogs.io/img/favicon.png",
      "url": "https://hooks.slack.com/services/T03FHQZLC/B09QNJ2CU/n3nFHS3ISw",
      "username": "Gogs"
    },
    "updated_at": "2015-08-29T18:25:55+08:00",
    "created_at": "2015-08-28T23:28:09+08:00"
  }
]
```

## Create a hook

```
POST /repos/:username/:reponame/hooks
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|type|string|**Required** The type of webhook, either **gogs** or **slack**|
|config|object|**Required** Key/value pairs to provide settings for this hook|
|events|array|Determines what events the hook is triggered for. Default: **["push"]**|
|active|bool|Determines whether the hook is actually triggered on pushes. Default is **false**|

### Example

To create a webhook, the following fields are used by the `config`:

- `url`: A **required** string defining the URL to which the payloads will be delivered.
- `content_type`: A **required** string defining the media type used to serialize the payloads. Supported values include **json** and **form**.
- `secret`: An optional string that’s passed with the HTTP requests body, e.g. **{"secret": "xxx"}**.

Here’s how you can create a hook that posts payloads in JSON format:

```json
{
    "type": "gogs",
    "config": {
        "url": "http://gogs.io",
        "content_type": "json"
    },
    "events": [
        "create",
        "delete",
        "fork",
        "push",
        "issues",
        "issue_comment",
        "pull_request",
        "release",
    ],
    "active": true
}
```

### Response

```
Status: 201 Created
```
```json
{
  "id": 20,
  "type": "gogs",
  "config": {
    "content_type": "json",
    "url": "http://gogs.io"
  },
  "events": [
    "create",
    "push"
  ],
  "active": true,
  "updated_at": "2015-08-29T11:31:22.453572732+08:00",
  "created_at": "2015-08-29T11:31:22.453569275+08:00"
}
```

## Edit a hook

```
PATCH /repos/:username/:reponame/hooks/:id
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|config|object|**Required** Key/value pairs to provide settings for this hook|
|events|array|Determines what events the hook is triggered for. Default: **["push"]**|
|active|bool|Active or deactive the hook is actually triggered on pushes. Ignore this field to leave it unchanged|

### Example

```json
{
    "config": {
        "url": "http://gogs.io/hook"
    },
    "events": [
        "push"
    ]
}
```

### Response

```
Status: 200 OK
```
```json
{
  "id": 20,
  "type": "gogs",
  "config": {
    "content_type": "json",
    "url": "http://gogs.io/hook"
  },
  "events": [
    "push"
  ],
  "active": true,
  "updated_at": "2015-08-29T11:45:30.577057789+08:00",
  "created_at": "2015-08-29T11:31:22+08:00"
}
```

## Delete a hook

```
DELETE /repos/:username/:reponame/hooks/:id
```

### Response

```
Status: 204 No Content
```