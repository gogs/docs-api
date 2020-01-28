# Miscellaneous

## Markdown

### Render an arbitrary Markdown document

```
POST /markdown
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|text|string|**Required** The Markdown text to render|
|context|string|The repository context, e.g. `https://github.com/gogs/gogs`|

### Example

```json
{
  "text": "Hello world gogs/gogs#1 **cool**, and #1!",
  "context": "https://github.com/gogs/gogs"
}
```

### Response

```
Status: 200 OK
Content-Type: text/html
```
```html
<p>Hello world <a href="https://try.gogs.io/gogs/gogs/issues/1" rel="nofollow">gogs/gogs#1</a> <strong>cool</strong>, and <a href="https://github.com/gogs/gogs/issues/1" rel="nofollow">#1</a>!</p>
```

### Render a Markdown document in raw mode

```
POST /markdown/raw
```

### Parameters

The raw API takes a Markdown document as plaintext(`text/plain`) and renders it as plain Markdown without a repository context.

### Response

```
Status: 200 OK
Content-Type: text/html
```
```html
<p>Hello world gogs/gogs#1 <strong>cool</strong>, and #1!</p>
```
