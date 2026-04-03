# Text Templates in Go

Tags: #go #intermediate #templates #html #text

## Overview

Go's `html/template` and `text/template` packages allow generating dynamic text from a template pattern.

## Template Syntax

- `{{.FieldName}}` — access a field of the passed data
- `{{.key}}` — access a map key
- `{{if .Condition}} ... {{end}}`
- `{{range .Items}} ... {{end}}`

## Code Example

```go
import (
    "html/template"
    "os"
)

// Define templates map
templates := map[string]string{
    "welcome":      "Welcome, {{.name}}! We're glad you joined.",
    "notification": "{{.nm}}, you have a new notification: {{.ntf}}",
    "error":        "Oops! An error occurred: {{.em}}",
}

// Parse and store
parsedTemplates := make(map[string]*template.Template)
for name, tmpl := range templates {
    parsedTemplates[name] = template.Must(template.New(name).Parse(tmpl))
}

// Execute a template
data := map[string]interface{}{"name": "John"}
err := parsedTemplates["welcome"].Execute(os.Stdout, data)
```

## Key Points

- `template.Must` panics if the template fails to parse — good for static templates.
- `Execute(writer, data)` renders the template and writes to the writer.
- `html/template` auto-escapes HTML to prevent XSS.
- Use `text/template` for non-HTML output.

## Related Notes

- [[05 - String Formatting]]
- [[03 - fmt Package]]
