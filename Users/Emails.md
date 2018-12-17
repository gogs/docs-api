# Emails

## List email addresses for a user

```
GET /user/emails
```

### Response

```
Status: 200 OK
```
```json
[
  {
    "email": "fake@local",
    "verified": true,
    "primary": true
  }
]
```

## Add email address(es)

```
POST /user/emails
```

### Example

```json
[
  "user1@user.com",
  "user2@user.com"
]
```

### Response

```
Status: 201 Created
```
```json
[
  {
    "email": "user1@user.com",
    "verified": false,
    "primary": false
  },
  {
    "email": "user1@user.com",
    "verified": false,
    "primary": false
  }
]
```

## Delete email address(es)

```
DELETE /user/emails
```

### Example

```json
[
  "user1@user.com",
  "user2@user.com"
]
```

### Response

```
Status: 204 No Content
```
