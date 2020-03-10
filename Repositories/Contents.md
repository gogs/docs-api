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
GET /repos/:username/:reponame/contents/:ref/:path
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
    "size": 0,
    "name": "README.md",
    "path": "d1",
    "sha": "e69de29bb2d1d6434b8b29ae775ad8c2e48c5391",
    "url": "https://try.gogs.io/api/v1/repos/root/test-symlink/contents/d1",
    "git_url": "https://try.gogs.io/api/v1/repos/root/test-symlink/trees/e69de29bb2d1d6434b8b29ae775ad8c2e48c5391",
    "html_url": "https://try.gogs.io/api/v1/repos/root/test-symlink/tree/e69de29bb2d1d6434b8b29ae775ad8c2e48c5391",
    "download_url": "https://try.gogs.io/api/v1/root/test-symlink/raw/d1",
    "_links": {
      "git": "https://try.gogs.io/api/v1/repos/root/test-symlink/trees/e69de29bb2d1d6434b8b29ae775ad8c2e48c5391",
      "self": "https://try.gogs.io/api/v1/repos/root/test-symlink/contents/d1",
      "html": "https://try.gogs.io/api/v1/repos/root/test-symlink/tree/e69de29bb2d1d6434b8b29ae775ad8c2e48c5391"
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
  "target": "text1.text",
  "size": 10,
  "name": "text2.text",
  "path": "text2.text",
  "sha": "0d4ce3e58e1afc8be81cb757d628d94af27581ea",
  "url": "https://try.gogs.io/api/v1/repos/root/test-symlink/contents/text2.text",
  "git_url": "https://try.gogs.io/api/v1/repos/root/test-symlink/trees/0d4ce3e58e1afc8be81cb757d628d94af27581ea",
  "html_url": "https://try.gogs.io/api/v1/repos/root/test-symlink/tree/0d4ce3e58e1afc8be81cb757d628d94af27581ea",
  "download_url": "https://try.gogs.io/api/v1/root/test-symlink/raw/text2.text",
  "_links": {
    "git": "https://try.gogs.io/api/v1/repos/root/test-symlink/trees/0d4ce3e58e1afc8be81cb757d628d94af27581ea",
    "self": "https://try.gogs.io/api/v1/repos/root/test-symlink/contents/text2.text",
    "html": "https://try.gogs.io/api/v1/repos/root/test-symlink/tree/0d4ce3e58e1afc8be81cb757d628d94af27581ea"
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
  "size": 0,
  "name": "testrepo",
  "path": "testrepo",
  "sha": "2ddc5c87f1e6d78ea63a2d5fa19527a804ad252e",
  "url": "https://try.gogs.io/api/v1/repos/root/test-symlink/contents/testrepo",
  "git_url": "https://try.gogs.io/api/v1/repos/root/test-symlink/trees/2ddc5c87f1e6d78ea63a2d5fa19527a804ad252e",
  "html_url": "https://try.gogs.io/api/v1/repos/root/test-symlink/tree/2ddc5c87f1e6d78ea63a2d5fa19527a804ad252e",
  "download_url": "https://try.gogs.io/api/v1/root/test-symlink/raw/testrepo",
  "_links": {
    "git": "https://try.gogs.io/api/v1/repos/root/test-symlink/trees/2ddc5c87f1e6d78ea63a2d5fa19527a804ad252e",
    "self": "https://try.gogs.io/api/v1/repos/root/test-symlink/contents/testrepo",
    "html": "https://try.gogs.io/api/v1/repos/root/test-symlink/tree/2ddc5c87f1e6d78ea63a2d5fa19527a804ad252e"
  }
}
```
