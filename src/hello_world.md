# Hello World!

It is traditional to write a 'Hello World' program whenever you begin learning a new language. Here it is in Huff!

```
#define macro MAIN() = takes (0) returns (0) {
    0x48656c6c6f2c20776f726c6421 0x00 mstore // Store "Hello, World!" in memory.
    0x1a 0x00 return // Return 26 bytes starting from memory pointer 0.
}
```