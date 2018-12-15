# Overview

This is a set of documents which describes Gogs REST API v1 usage, since it's still in early stage:

1. Content of documentation and APIs are subject to change.
2. We do not provide documentation in other languages.
3. Aim to be in the format that is similar to [GitHub REST API v3](https://developer.github.com/v3/).

If you have any questions or concern, please [file an issue](https://github.com/gogits/go-gogs-client/issues/new). :blush:

## Installation 

The API is preinstalled with the base Gogs deployment. See [current version](#current-version) and [API source code](https://github.com/gogs/gogs/tree/master/routes/api) for more details.

## Current Version

All Gogs APIs are under **v1** using request path prefix `/api/v1`.

## Schema

All data is sent and received as JSON.

```
HTTP/2 200
content-type: application/json; charset=UTF-8
date: Sat, 15 Dec 2018 01:55:28 GMT
server: Caddy
content-length: 175
```

All timestamps return in ISO 8601 format:

```
YYYY-MM-DDTHH:MM:SSZ
```

## Authentication

There are three ways to authenticate through Gogs API v1. Requests that require authentication will return `404 Not Found`, instead of `403 Forbidden`, in some places. This is to prevent the accidental leakage of private repositories to unauthorized users.

## Basic Authentication

```
curl -u "unknwon" https://try.gogs.io/api/v1/users/unknwon/tokens
```

Basic authentication can only be used to obtain access tokens.

### Access Token

Personal access tokens are easier to manage and use, but except for few APIs (i.e. generate or get a access token), and they can be sent in **header** or **URL query**.

```
$ curl -H "Authorization: token {ACCESS_TOKEN}" https://try.gogs.io/api/v1/user/repos
$ curl https://try.gogs.io/api/v1/user/repos?token={ACCESS_TOKEN}
```

## Parameters

Parameters of all requests use POST method can be passed through a normal HTML form or JSON data, but sending JSON is recommended.

## Clients

- [Go](https://github.com/gogs/go-gogs-client)
- [Android](https://github.com/unfoldingWord-dev/android-gogs-client)

## Notes

- The style of documentation is heavily influenced by [GitHub Developer](https://developer.github.com/).