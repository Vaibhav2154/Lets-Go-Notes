# Temp Files in Go

Tags: #go #intermediate #tmpfiles #os #cleanup

## Overview

Go provides functions to create temporary files and directories that can be cleaned up automatically with `defer`.

## Temp Directory

```go
import "os"

// Create a temp directory in the OS temp dir
tempDir, err := os.MkdirTemp("", "GoCourseTempDir")
if err != nil {
    panic(err)
}
defer os.RemoveAll(tempDir)  // cleanup when done

fmt.Println("Temp dir:", tempDir)
```

## Temp File

```go
tempFile, err := os.CreateTemp("", "myTempFile")
if err != nil {
    panic(err)
}
defer os.Remove(tempFile.Name())  // cleanup when done
defer tempFile.Close()

fmt.Println("Temp file:", tempFile.Name())
tempFile.WriteString("temporary content")
```

## Key Points

- First argument to `MkdirTemp`/`CreateTemp` is the directory path; empty string `""` uses the OS default temp dir.
- Second argument is the name prefix (a random suffix is appended automatically).
- Use `defer os.RemoveAll(dir)` for directories (removes recursively).
- Use `defer os.Remove(file.Name())` for individual files.

## Related Notes

- [[17 - Reading Files]]
- [[18 - Writing Files]]
- [[21 - Directories]]
