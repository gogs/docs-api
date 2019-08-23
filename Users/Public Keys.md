# Public Keys

## List public keys for a user

```
GET /users/:username/keys
```

### Response

```
Status: 200 OK
```
```json
[
  {
    "id": 1,
    "key": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDUbmwBOG5vI8qNCztby5LDc9ozwTuwsqf+1fpuHjT9iQ2Lu9nlKHQJcPSgdrYAcc+88K6o74ayhTAjfajKxkIHnbzZFjidoVZSQDhX5qvl93jvY/Uz390qky0sweW+fspm8pRJL+ofE3QEN5AXAuycq1tgsRT32XC+Ta82Xyv8b3xW+pWbsZzYCzUsZXDe/xWxg1rndXh2BIrmcYf9BMiv9ZJIojJXfuLCeRXl550tDzaMFC0rQ/T5pZjs/lQemtg92MnxnEDi5nhuvDwM4Q8eqCTOXc4BCE7iyIHv+B7rx+0x99ytMh5BSIIGyWTfgTot/AjGVm5aRKJSRFgPBm9N comment with whitespace",
    "url": "http://localhost:3000/api/v1/user/keys/1",
    "title": "local",
    "created_at": "2015-11-18T15:05:43-05:00"
  }
]
```

## Get a single public key

```
GET /user/keys/:id
```

### Response

```
Status: 200 OK
```
```json
{
  "id": 1,
  "key": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDUbmwBOG5vI8qNCztby5LDc9ozwTuwsqf+1fpuHjT9iQ2Lu9nlKHQJcPSgdrYAcc+88K6o74ayhTAjfajKxkIHnbzZFjidoVZSQDhX5qvl93jvY/Uz390qky0sweW+fspm8pRJL+ofE3QEN5AXAuycq1tgsRT32XC+Ta82Xyv8b3xW+pWbsZzYCzUsZXDe/xWxg1rndXh2BIrmcYf9BMiv9ZJIojJXfuLCeRXl550tDzaMFC0rQ/T5pZjs/lQemtg92MnxnEDi5nhuvDwM4Q8eqCTOXc4BCE7iyIHv+B7rx+0x99ytMh5BSIIGyWTfgTot/AjGVm5aRKJSRFgPBm9N comment with whitespace",
  "url": "http://localhost:3000/api/v1/user/keys/1",
  "title": "local",
  "created_at": "2015-11-18T15:05:43-05:00"
}
```

## List your public keys

```
GET /user/keys
```

### Response

```
Status: 200 OK
```
```json
[
  {
    "id": 1,
    "key": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDUbmwBOG5vI8qNCztby5LDc9ozwTuwsqf+1fpuHjT9iQ2Lu9nlKHQJcPSgdrYAcc+88K6o74ayhTAjfajKxkIHnbzZFjidoVZSQDhX5qvl93jvY/Uz390qky0sweW+fspm8pRJL+ofE3QEN5AXAuycq1tgsRT32XC+Ta82Xyv8b3xW+pWbsZzYCzUsZXDe/xWxg1rndXh2BIrmcYf9BMiv9ZJIojJXfuLCeRXl550tDzaMFC0rQ/T5pZjs/lQemtg92MnxnEDi5nhuvDwM4Q8eqCTOXc4BCE7iyIHv+B7rx+0x99ytMh5BSIIGyWTfgTot/AjGVm5aRKJSRFgPBm9N comment with whitespace",
    "url": "http://localhost:3000/api/v1/user/keys/1",
    "title": "local",
    "created_at": "2015-11-18T15:05:43-05:00"
  }
]
```

## Create a public key

```
POST /user/keys
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|title|string|**Required** The name of the key|
|key|string|**Required** The content of the key|

### Example

Here’s how you can create a public key:

```json
{
  "title": "unknwon@gogs",
  "key": "ssh-rsa AAA...",
}
```

### Response

```
Status: 201 Created
```
```json
{
  "id": 2,
  "key": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDUbmwBOG5vI8qNCztby5LDc9ozwTuwsqf+1fpuHjT9iQ2Lu9nlKHQJcPSgdrYAcc+88K6o74ayhTAjfajKxkIHnbzZFjidoVZSQDhX5qvl93jvY/Uz390qky0sweW+fspm8pRJL+ofE3QEN5AXAuycq1tgsRT32XC+Ta82Xyv8b3xW+pWbsZzYCzUsZXDe/xWxg1rndXh2BIrmcYf9BMiv9ZJIojJXfuLCeRXl550tDzaMFC0rQ/T5pZjs/lQemtg92MnxnEDi5nhuvDwM4Q8eqCTOXc4BCE7iyIHv+B7rx+0x99ytMh5BSIIGyWTfgTot/AjGVm5aRKJSRFgPBm9N comment with whitespace",
  "url": "http://localhost:3000/api/v1/user/keys/2",
  "title": "local2",
  "created_at": "2015-11-18T21:18:55.292816433-05:00"
}
```

## Delete a public key

```
DELETE /user/keys/:id
```

### Response

```
Status: 204 No Content
```
