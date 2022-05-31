# Macros

Macros are a principal building block of the Huff programming language. Macros are a way of writing code that writes other code, practically similar to a function, but with a few key differences.

- Macros are not exposed to the end user, as they are in Solidity or Vyper. It is up to the programmer to decide that. This is usually achieved by matching the calldata of the contract in the `MAIN()` macro.
- Macros do not contribute to the overall bytecode footprint, unless they are invoked. When they are invoked, they are 'expanded' according to the arguments they are called with and the opcodes the macro is defined by. Macro expansion can be thought of as replacing the call to `EXAMPLE()` with the opcodes `EXAMPLE()` is made of.

The only exception to the above is the `MAIN()` macro, which holds a few different and special properties a programmer must consider. This macro is effectively the entrypoint to the contract: here the final bytecode is constructed. 

Now lets look at how to write a macro!

## Example

Below is a macro from the Huff standard library. It identifies whether an address has contract code associated with it.

```
#define macro IS_CONTRACT() = takes(1) returns (1) {
    // Returns 0 if no code is associated with the address.
    extcodesize
}
```

We define a macro in Huff by entering `#define macro` followed by a macro name, stack annotations and a set of parentheses. The curly brackets tell the compiler where the macro body begins and ends. The default naming convention for macros in Huff is SCREAMING_SNAKE_CASE.

'Stack annotations' are a feature not seen in other smart contract languages. They describe how the macro will manipulate the stack. In this example, the macro `takes(1)` and `returns (1)`. This means that it will take one element off the stack, and put another one on.

If there was a macro to perform addition between two numbers then we would annotate it with `takes(2) returns(1)`. As an example, if the stack was [10, 20] it would take the 10 and 20 off and then put the sum, 30, on the stack.

In our example of the contract code macro, the `extcodesize` opcode takes in one parameter: an `address`, and returns the `size` of it, thus it takes one element off the stack and returns another one.

## Summary

Try writing macros that:

- Add two numbers together.
- Send ether to a given address.
- Perform a contract call.