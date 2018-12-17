# Followers

## List followers of a user

List a user's followers:

```
GET /users/:username/followers
```

List the authenticated user's followers:

```
GET /user/followers
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
    "full_name": "",
    "email": "user1@user.com",
    "avatar_url": "/avatars/3"
  }
]
```

## List users followed by another user

List who a user is following:

```
GET /users/:username/following
```

List who the authenticated user is following:

```
GET /user/following
```

## Check if you are following a user

```
GET /user/following/:username
```

**Response if you are following this user**

```
Status: 204 No Content
```

**Response if you are not following this user**

```
Status: 404 Not Found
```

## Check if one user follows another

```
GET /users/:username/following/:target
```

**Response if user follows target user**

```
Status: 204 No Content
```

**Response if user does not follow target user**

```
Status: 404 Not Found
```

## Follow a user

```
PUT /user/following/:username
```

### Response

```
Status: 204 No Content
```

## Unfollow a user

```
DELETE /user/following/:username
```

```
Status: 204 No Content
```
