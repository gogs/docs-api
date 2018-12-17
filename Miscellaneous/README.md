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
|mode|string|The rendering mode, can be empty or **gfm**. In **gfm** mode, Markdown will be rendered with repository context|
|context|string|The repository context. Only taken into account when rendering mode is **gfm**|

### Example

```json
{
  "text": "Hello world gogs/gogs#1 **cool**, and #1!",
  "mode": "gfm",
  "context": "gogs/gogs"
}
```

### Response

```
Status: 200 OK
Content-Type: text/html
```
```html
<p>Hello world gogs/gogs#1 <strong>cool</strong>, and <a href="https://try.gogs.io/gogs/gogs/issues/1" rel="nofollow">#1</a>!</p>
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
