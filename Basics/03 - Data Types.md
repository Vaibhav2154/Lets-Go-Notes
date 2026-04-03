# Data Types in Go

Tags: #go #basics #data-types

## Overview

Go is a statically typed language. Every variable has a type known at compile time.

## Basic Types

| Category | Types |
|----------|-------|
| Integer | `int`, `int8`, `int16`, `int32`, `int64` |
| Unsigned | `uint`, `uint8`, `uint16`, `uint32`, `uint64` |
| Float | `float32`, `float64` |
| Complex | `complex64`, `complex128` |
| Boolean | `bool` |
| String | `string` |
| Byte | `byte` (alias for `uint8`) |
| Rune | `rune` (alias for `int32`, represents Unicode code point) |

## Default (Zero) Values

| Type | Default |
|------|---------|
| Numeric | `0` |
| Boolean | `false` |
| String | `""` |
| Pointer, Slice, Map, Function, Struct | `nil` |

## Related Notes

- [[04 - Variables]]
- [[06 - Constants]]
