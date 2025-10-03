# Source Code Documentation

This document provides an overview of the main script files in the Context7 MCP server project.

---

## 1. **index.ts**

The entry point of the project that orchestrates all functionality and exports the main modules.

This file:
- Sets up the MCP (Model Context Protocol) server
- Configures command-line arguments and transport options (stdio/http)
- Registers available tools (`resolve-library-id` and `get-library-docs`)
- Handles HTTP and stdio transport layers for communication
- Manages server initialization and startup logic

---

## 2. **lib/api.ts**

Handles all API-related functions and logic for communicating with the Context7 service.

This file includes:
- `searchLibraries()`: Searches for libraries matching a given query
- `fetchLibraryDocumentation()`: Retrieves documentation for a specific library
- Proxy configuration for network requests
- Error handling for API responses (rate limiting, authentication, etc.)

---

## 3. **lib/encryption.ts**

Manages encryption and decryption utilities for securing sensitive data.

Key functionality:
- `encryptClientIp()`: Encrypts client IP addresses using AES-256-CBC encryption
- `generateHeaders()`: Creates HTTP headers with encrypted client IP and API key
- Validates encryption keys to ensure proper format

> **📚 Note for Junior Developers:** Encryption is essential for securing sensitive data like IP addresses and API keys. It transforms readable data (plaintext) into scrambled data (ciphertext) that can only be decoded with the correct key. This project uses AES-256-CBC, a strong encryption algorithm that ensures data privacy during transmission.

---

## 4. **lib/types.ts**

Defines TypeScript types and interfaces for the project, ensuring type safety throughout the codebase.

Main type definitions:
- `SearchResult`: Structure for library search results
- `SearchResponse`: Response format for search queries
- `DocumentState`: Enum for documentation processing states

> **📚 Note for Junior Developers:** TypeScript types help catch errors during development by specifying what kind of data a variable or function should work with. For example, if a function expects a `string` but receives a `number`, TypeScript will warn you before the code runs. This prevents bugs and makes code more maintainable and self-documenting.

---

## 5. **lib/utils.ts**

Contains general-purpose utility functions that are reused across the project.

Key functions:
- `formatSearchResult()`: Formats a single search result into a human-readable string
- `formatSearchResults()`: Formats multiple search results with proper formatting

> **📚 Note for Junior Developers:** Utility functions are reusable pieces of code that perform common tasks. They help keep code modular and DRY (Don't Repeat Yourself). Instead of writing the same formatting logic in multiple places, we centralize it in one function that can be called anywhere. This makes the code easier to test, maintain, and update.

---

## Project Structure

```
src/
├── index.ts              # Entry point and server setup
└── lib/
    ├── api.ts           # API communication layer
    ├── encryption.ts    # Security utilities
    ├── types.ts         # TypeScript type definitions
    └── utils.ts         # Reusable utility functions
```
