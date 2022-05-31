# Interfaces

The external interface includes functions and events.
The interface does not functionally change the contract, it only defines the external ABI for other
contracts and client libraries to use.

## Functions

To define a function, we will need a few components.

- Name
- Parameter Type(s)
- Type

    - pure (can not read or write state)
    - view (can read state)
    - nonpayable (can read and write state)
    - payable (can read and write state and receive Ether)

- Return Type(s)

When a funciton takes no arguments, empty parenthesis must be used.

When a funciton returns no values, empty parenthesis must be used.

### Example

The following is the function interface of a contract that conforms to the ERC20 interface.

```
#define function totalSupply() view returns (uint256)
#define function balanceOf(address) view returns (uint256)
#define function allowance(address,address) view returns (uint256)

#define function approve(address,uint256) nonpayable returns (bool)
#define function transfer(address,uint256) nonpayable returns (bool)
#define function transferFrom(address,address,uint256) nonpayable returns (bool)
```

## Events

To define an event, we will need only the following components.

- Name
- Parameter Types

If an event takes no arguments, we must use empty parenthesis.

### Example

The following is the event interface of a contract that conforms to the ERC20 interface.

```
#define event Transfer(address,address,uint256)
#define event Approve(address,address,uint256)
```

## Summary

Try writing an interface that:

- Defines an ERC20 token.
- Defines an ERC721 token.