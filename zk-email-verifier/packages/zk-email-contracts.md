# zk-email/contracts

### ZK EMAIL DOCS HAVE MOVED TO [docs.zk.email](https://docs.zk.email/zk-email-verifier/packages/zk-email-contracts). THE FOLLOWING DOCS ARE OUTDATED.

### DKIMRegistry.sol

`DKIMRegistry.sol` is a Solidity contract within the `@zk-email/contracts` package, functioning as a registry for storing hashes of DKIM public keys associated with particular domains.

<details>

<summary>Details</summary>

1. **Registering DKIM Public Key Hashes**: Developers can use the contract to register new hashes of DKIM public keys for a domain, so that any email sent from the domain can be verified against the blockchain-stored hash.
2. **Validating DKIM Public Key Hashes**: The contract allows for the validation of a registered DKIM public key hash. This helps verify if the public key in an email matches the one registered in the blockchain for the domain, confirming the email's authenticity.
3. **Revoking Compromised Keys**: In the event of a security breach or compromise of a private key, developers can revoke the associated DKIM public key hash to prevent misuse.

For a detailed overview of its functionalities, please refer to the source file: DKIMRegistry.sol

</details>

### StringUtils.sol

`StringUtils.sol` is a Solidity library that offers a range of string manipulation functions, including conversion between bytes and strings, and numerical string operations, for use across the `@zk-email/contracts` package.

<details>

<summary>Details</summary>

**Converting Values to Strings**

* **To Hex String**: Convert a `uint256` to its ASCII `string` hexadecimal representation.

```solidity
string memory hexString = StringUtils.toHexString(12345, 4);
// hexString will be "0x3039" 
```

* **To Hex String Without Prefix**: Similar to `toHexString` but without the "0x" prefix.

```solidity
string memory hexStringNoPrefix = StringUtils.toHexStringNoPrefix(12345, 4);
// hexStringNoPrefix will be "3039"
```

* **To String from Various Types**: Convert `uint256`, `bytes32`, or `address` to a string.

```solidity
string memory uintToString = StringUtils.toString(uint256(12345));
string memory bytesToString = StringUtils.toString(bytes32("data"));
string memory addressToString = StringUtils.toString(address(0x123));
```

**String Comparisons**

* **String Equality**: Check if two strings are equal.

```solidity
bool isEqual = StringUtils.stringEq("hello", "hello");
// isEqual will be true
```

**Advanced String Manipulations**

* **Remove Trailing Zeros**: Trims trailing zeros from a string representation of bytes.

```solidity
string memory trimmedString = StringUtils.removeTrailingZeros("hello\x00\x00");
// trimmedString will be "hello"
```

* **Convert Packed Bytes to String**: Unpacks `uint256` values into a string, useful for handling compact data representations. 1 packed byte = 31 normal bytes.
* **Upper and Lower Case Conversion**: Convert a string to all uppercase or lowercase.

```solidity
string memory upperString = StringUtils.upper("hello"); // "HELLO"
string memory lowerString = StringUtils.lower("HELLO"); // "hello"
```

</details>
