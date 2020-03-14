# Contents

## Download raw content

This method returns the raw content of a file.

```
GET /repos/:username/:reponame/raw/:ref/:path
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|ref|string|**Required** The name of the commit/branch/tag|
|path|string|**Required** The content path|

### Response

```
Status: 200 OK
Content-Type: text/plain
```

	## Getting Started
	
	To install Macaron:
	
		go get github.com/Unknwon/macaron
	
	The very basic usage of Macaron:
	
	```go
	package main
	
	import "github.com/Unknwon/macaron"
	
	func main() {
		m := macaron.Classic()
		m.Get("/", func() string {
			return "Hello world!"
		})
		m.Run()
	}
	```

## Download archive

This method returns archive by given format.

```
GET /repos/:username/:reponame/archive/:ref:format
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|ref|string|**Required** The name of the commit/branch/tag|
|format|string|**Required** The format of archive, either **.zip** or **.tar.gz**|

### Response

```
Status: 200 OK
Content-Type: application/octet-stream
```

## Get contents

```
GET /repos/:username/:reponame/contents/:path
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|`ref`|`string`|The name of the commit/branch/tag. The default is the default branch of the repository, usually is `master`.|

### Response if path is empty

It's possible for `:path` to be empty. If no path is specified the contents at the root of the repository are returned.

```
Status: 200 OK
```
```json
[
  {
    "type": "file",
    "encoding": "base64",
    "size": 50,
    "name": "Sum.groovy",
    "path": "src/Sum.groovy",
    "content": "c3RhdGljIGludCBzdW0oaW50IHZhbDEsIHZhbDIpIHsKICAgIHZhbDEgKyB2YWwyCn0=",
    "sha": "9f221918607d78c1db3f6c6d5afa68a66b1146a8",
    "url": "https://try.gogs.io/api/v1/repos/unknwon/git-module-testrepo/contents/src/Sum.groovy",
    "git_url": "https://try.gogs.io/api/v1/repos/unknwon/git-module-testrepo/git/blobs/9f221918607d78c1db3f6c6d5afa68a66b1146a8",
    "html_url": "https://try.gogs.io/unknwon/git-module-testrepo/src/master/Sum.groovy",
    "download_url": "https://try.gogs.io/unknwon/git-module-testrepo/raw/master/Sum.groovy",
    "_links": {
      "git": "https://try.gogs.io/api/v1/repos/unknwon/git-module-testrepo/git/blobs/9f221918607d78c1db3f6c6d5afa68a66b1146a8",
      "self": "https://try.gogs.io/api/v1/repos/unknwon/git-module-testrepo/contents/src/Sum.groovy",
      "html": "https://try.gogs.io/unknwon/git-module-testrepo/src/master/Sum.groovy"
    }
  }
]
```

### Response if content is a file
```
Status: 200 OK
```
```json
{
  "type": "file",
  "encoding": "base64",
  "size": 795,
  "name": "README.txt",
  "path": "README.txt",
  "content": "VGhpcyBpcyBhIHNhbX...",
  "sha": "adfd6da3c0a3fb038393144becbf37f14f780087",
  "url": "https://try.gogs.io/api/v1/repos/unknwon/git-module-testrepo/contents/README.txt",
  "git_url": "https://try.gogs.io/api/v1/repos/unknwon/git-module-testrepo/git/blobs/adfd6da3c0a3fb038393144becbf37f14f780087",
  "html_url": "https://try.gogs.io/unknwon/git-module-testrepo/src/master/README.txt",
  "download_url": "https://try.gogs.io/unknwon/git-module-testrepo/raw/master/README.txt",
  "_links": {
    "git": "https://try.gogs.io/api/v1/repos/unknwon/git-module-testrepo/git/blobs/adfd6da3c0a3fb038393144becbf37f14f780087",
    "self": "https://try.gogs.io/api/v1/repos/unknwon/git-module-testrepo/contents/README.txt",
    "html": "https://try.gogs.io/unknwon/git-module-testrepo/src/master/README.txt"
  }
}
```


### Response if content is a directory

```
Status: 200 OK
```
```json
[
  {
    "type": "file",
    "encoding": "base64",
    "size": 50,
    "name": "Sum.groovy",
    "path": "src/Sum.groovy",
    "content": "c3RhdGljIGludCBzdW0oaW50IHZhbDEsIHZhbDIpIHsKICAgIHZhbDEgKyB2YWwyCn0=",
    "sha": "9f221918607d78c1db3f6c6d5afa68a66b1146a8",
    "url": "https://try.gogs.io/api/v1/repos/unknwon/git-module-testrepo/contents/src/Sum.groovy",
    "git_url": "https://try.gogs.io/api/v1/repos/unknwon/git-module-testrepo/git/blobs/9f221918607d78c1db3f6c6d5afa68a66b1146a8",
    "html_url": "https://try.gogs.io/unknwon/git-module-testrepo/src/master/Sum.groovy",
    "download_url": "https://try.gogs.io/unknwon/git-module-testrepo/raw/master/Sum.groovy",
    "_links": {
      "git": "https://try.gogs.io/api/v1/repos/unknwon/git-module-testrepo/git/blobs/9f221918607d78c1db3f6c6d5afa68a66b1146a8",
      "self": "https://try.gogs.io/api/v1/repos/unknwon/git-module-testrepo/contents/src/Sum.groovy",
      "html": "https://try.gogs.io/unknwon/git-module-testrepo/src/master/Sum.groovy"
    }
  },
  {
    "type": "dir",
    "size": 0,
    "name": "main",
    "path": "src/main",
    "sha": "b312d30ddff2f204d6b6aa78dd4beda593d9d787",
    "url": "https://try.gogs.io/api/v1/repos/unknwon/git-module-testrepo/contents/src/main",
    "git_url": "https://try.gogs.io/api/v1/repos/unknwon/git-module-testrepo/git/trees/b312d30ddff2f204d6b6aa78dd4beda593d9d787",
    "html_url": "https://try.gogs.io/unknwon/git-module-testrepo/src/master/main",
    "download_url": "https://try.gogs.io/unknwon/git-module-testrepo/raw/master/main",
    "_links": {
      "git": "https://try.gogs.io/api/v1/repos/unknwon/git-module-testrepo/git/trees/b312d30ddff2f204d6b6aa78dd4beda593d9d787",
      "self": "https://try.gogs.io/api/v1/repos/unknwon/git-module-testrepo/contents/src/main",
      "html": "https://try.gogs.io/unknwon/git-module-testrepo/src/master/main"
    }
  }
]
```

### Response if content is a symlink
```
Status: 200 OK
```
```json
{
  "type": "symlink",
  "target": "run.sh",
  "size": 6,
  "name": "symlink.run.sh",
  "path": "symlink.run.sh",
  "sha": "e0e63473c2593040d7d1c67637864821b28cef4b",
  "url": "https://try.gogs.io/api/v1/repos/unknwon/git-module-testrepo/contents/symlink.run.sh",
  "git_url": "",
  "html_url": "https://try.gogs.io/unknwon/git-module-testrepo/src/master/symlink.run.sh",
  "download_url": "https://try.gogs.io/unknwon/git-module-testrepo/raw/master/symlink.run.sh",
  "_links": {
    "git": "",
    "self": "https://try.gogs.io/api/v1/repos/unknwon/git-module-testrepo/contents/symlink.run.sh",
    "html": "https://try.gogs.io/unknwon/git-module-testrepo/src/master/symlink.run.sh"
  }
}
```

### Response if content is a submodule
```
Status: 200 OK
```
```json
{
  "type": "submodule",
  "submodule_git_url": "https://github.com/gogs/docs-api.git",
  "size": 0,
  "name": "docs-api",
  "path": "gogs/docs-api",
  "sha": "6b08f76a5313fa3d26859515b30aa17a5faa2807",
  "url": "https://try.gogs.io/api/v1/repos/unknwon/git-module-testrepo/contents/gogs/docs-api",
  "git_url": "",
  "html_url": "https://try.gogs.io/unknwon/git-module-testrepo/src/master/docs-api",
  "download_url": "https://try.gogs.io/unknwon/git-module-testrepo/raw/master/docs-api",
  "_links": {
    "git": "",
    "self": "https://try.gogs.io/api/v1/repos/unknwon/git-module-testrepo/contents/gogs/docs-api",
    "html": "https://try.gogs.io/unknwon/git-module-testrepo/src/master/docs-api"
  }
}
```
