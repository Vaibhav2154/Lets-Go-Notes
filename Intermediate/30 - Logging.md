# Logging in Go

Tags: #go #intermediate #logging #log #logrus

## Overview

Go has a built-in `log` package for basic logging and the popular third-party `logrus` library for structured, leveled logging.

## Standard `log` Package

```go
import "log"

// Basic log (includes timestamp by default)
log.Println("This is a log message.")

// Prefix
log.SetPrefix("INFO: ")
log.Println("Info message.")

// Flags for output format
log.SetFlags(log.Ldate | log.Ltime | log.Llongfile)
log.Println("Message with date, time, and file.")

// Custom loggers
infoLogger  := log.New(os.Stdout, "INFO: ", log.Ldate|log.Ltime|log.Lshortfile)
warnLogger  := log.New(os.Stdout, "WARN: ", log.Ldate|log.Ltime)
errorLogger := log.New(os.Stdout, "ERROR: ", log.Ldate|log.Ltime|log.Lshortfile)

infoLogger.Println("Info message")
warnLogger.Println("Warning message")
errorLogger.Println("Error message")
```

## Log to File

```go
file, _ := os.OpenFile("app.log", os.O_CREATE|os.O_WRONLY|os.O_APPEND, 0666)
defer file.Close()

fileLogger := log.New(file, "DEBUG: ", log.Ldate|log.Ltime|log.Lshortfile)
fileLogger.Println("This goes to the log file.")
```

## Logrus (Structured Logging)

```go
import "github.com/sirupsen/logrus"

log := logrus.New()
log.SetLevel(logrus.InfoLevel)
log.SetFormatter(&logrus.JSONFormatter{})

log.Info("Info message")
log.Warn("Warning message")
log.Error("Error message")

// Structured fields
log.WithFields(logrus.Fields{
    "username": "John",
    "method":   "GET",
}).Info("User logged in.")
```

## `log` Flags Reference

| Flag | Output |
|------|--------|
| `log.Ldate` | Date: `2009/11/10` |
| `log.Ltime` | Time: `23:00:00` |
| `log.Lshortfile` | `file.go:12` |
| `log.Llongfile` | `/full/path/file.go:12` |

## Related Notes

- [[29 - Environment Variables]]
- [[23 - Exit (Basics)]]
