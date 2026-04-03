# URL Parsing in Go

Tags: #go #intermediate #url #net/url #http

## Overview

The `net/url` package provides functions to parse, build, and encode URLs.

## URL Anatomy

```
[scheme://][userinfo@]host[:port][/path][?query][#fragment]
```

## Code Example

```go
import "net/url"

rawURL := "https://example.com:8080/path?query=param#fragment"
parsedURL, _ := url.Parse(rawURL)

fmt.Println(parsedURL.Scheme)    // "https"
fmt.Println(parsedURL.Host)      // "example.com:8080"
fmt.Println(parsedURL.Port())    // "8080"
fmt.Println(parsedURL.Path)      // "/path"
fmt.Println(parsedURL.RawQuery)  // "query=param"
fmt.Println(parsedURL.Fragment)  // "fragment"

// Query parameters
rawURL1 := "https://example.com/path?name=John&age=30"
u, _ := url.Parse(rawURL1)
q := u.Query()
fmt.Println(q.Get("name"))  // "John"
fmt.Println(q.Get("age"))   // "30"
```

## Building a URL

```go
base := &url.URL{
    Scheme: "https",
    Host:   "example.com",
    Path:   "/search",
}
q := base.Query()
q.Set("name", "John")
q.Set("age", "30")
base.RawQuery = q.Encode()
fmt.Println(base.String())  // https://example.com/search?age=30&name=John
```

## Encoding Query Values

```go
values := url.Values{}
values.Add("name", "Jane")
values.Add("city", "London")
encoded := values.Encode()  // "city=London&name=Jane"
```

## Related Notes

- [[13 - URL Parsing]]
- [[11 - Random Numbers]]
