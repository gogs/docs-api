# Overview

This is a set of documents which describes Gogs REST API v1 usage, since it's still in early stage:

1. Content of documentation and APIs are subject to change.
2. We do not provide documentation in other languages.
3. Aim to be in the format that is similar to [GitHub REST API v3](https://developer.github.com/v3/).

If you have any questions or concern, please [file an issue](https://github.com/gogs/go-gogs-client/issues/new). :blush:

## TOC

- [Administration](Administration)
  - [Users](Administration/Users.md)
  - [Repositories](Administration/Repositories.md)
  - [Organizations](Administration/Organizations.md)
- [Issues](Issues)
  - [Comments](Issues/Comments.md)
  - [Labels](Issues/Labels.md)
  - [Milestones](Issues/Milestones.md)
- [Miscellaneous](Miscellaneous)
- [Organizations](Organizations)
  - [Members](Organizations/Members.md)
  - [Teams](Organizations/Teams.md)
- [Repositories](Repositories)
  - [Branches](Repositories/Branches.md)
  - [Collaborators](Repositories/Collaborators.md)
  - [Commits](Repositories/Commits.md)
  - [Contents](Repositories/Contents.md)
  - [Deploy Keys](Repositories/Deploy%20Keys.md)
  - [Webhooks](Repositories/Webhooks.md)
- [Users](Users)
  - [Emails](Users/Emails.md)
  - [Followers](Users/Followers.md)
  - [Public Keys](Users/Public%20Keys.md)
- [Git Data](Git%20Data)
  - [Trees](Git%20Data/Trees.md)

## Installation 

The API is preinstalled with the base Gogs deployment. See [current version](#current-version) and [API source code](https://github.com/gogs/gogs/tree/master/internal/route/api) for more details.

## Current Version

All Gogs APIs are under **v1** using request path prefix `/api/v1`.

## Schema

All data is sent and received as JSON unless specified otherwise.

```
HTTP/2 200
content-type: application/json; charset=UTF-8
date: Sat, 15 Dec 2018 01:55:28 GMT
server: Caddy
content-length: 175
```

All timestamps return in RFC3339 format:

```
YYYY-MM-DDTHH:MM:SSZ
2006-01-02T15:04:05Z07:00
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

## Pagination

You can specify further pages with the `?page` parameter.

```
curl https://try.gogs.io/api/v1/repos/unknwon/hello/issues?page=1
```

Note that page numbering is 1-based and that omitting the `?page` parameter will return the first page.

### Link header

The [Link header](http://tools.ietf.org/html/rfc5988) includes pagination information:

```
Link: <https://try.gogs.io/api/v1/repos/unknwon/hello/issues?page=3>; rel="next",
  <https://try.gogs.io/api/v1/repos/unknwon/hello/issues?page=50>; rel="last"
```

The example includes a line break for readability.

This Link response header contains one or more Hypermedia link relations, some of which may require expansion as URI templates.

The possible rel values are:

|Name|Description|
|----|-----------|
|`next`|The link relation for the immediate next page of results.|
|`last`|The link relation for the last page of results.|
|`first`|The link relation for the first page of results.|
|`prev`|The link relation for the immediate previous page of results.|

## Clients

- [Go](https://github.com/gogs/go-gogs-client)
- [Android](https://github.com/unfoldingWord-dev/android-gogs-client)

## Notes

- The style of documentation is heavily influenced by [GitHub Developer](https://developer.github.com/).
