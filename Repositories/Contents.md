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
