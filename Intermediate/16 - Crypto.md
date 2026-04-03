# Cryptography in Go

Tags: #go #intermediate #crypto #sha256 #hashing #security

## Overview

Go's `crypto` package suite provides hashing (SHA-256, SHA-512) and cryptographically secure random number generation.

## Password Hashing with Salt

```go
import (
    "crypto/rand"
    "crypto/sha256"
    "encoding/base64"
    "io"
)

// Generate a random salt
func generateSalt() ([]byte, error) {
    salt := make([]byte, 16)
    _, err := io.ReadFull(rand.Reader, salt)
    return salt, err
}

// Hash password with salt
func hashPassword(password string, salt []byte) string {
    saltedPassword := append(salt, []byte(password)...)
    hash := sha256.Sum256(saltedPassword)
    return base64.StdEncoding.EncodeToString(hash[:])
}

// Sign-up
salt, _ := generateSalt()
signUpHash := hashPassword("password123", salt)
saltStr := base64.StdEncoding.EncodeToString(salt)

// Login verification
decodedSalt, _ := base64.StdEncoding.DecodeString(saltStr)
loginHash := hashPassword("password123", decodedSalt)

if signUpHash == loginHash {
    fmt.Println("Password correct!")
} else {
    fmt.Println("Login failed!")
}
```

## Key Points

- **Never store plain passwords** — always hash with a salt.
- `sha256.Sum256(data)` returns a fixed-size `[32]byte` array — use `[:]` to get a slice.
- `crypto/rand` provides **cryptographically secure** randomness (unlike `math/rand`).
- For production password hashing, prefer `bcrypt` or `argon2` (libraries available via go modules).

## Related Notes

- [[14 - Base64 Encoding]]
- [[11 - Random Numbers]]
