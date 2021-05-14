# Policy Class

Provides a series of methods of the native contract Policy, which contract hash is `0xcc5e4edd9f5f8dba8bb65734541df7a1c081c67b`.

Namespace：[Neo.SmartContract.Framework.Native](../native.md)

Assembly: Neo.SmartContract.Framework

## Syntax

```c#
public class Policy
```

## Attribute

| Name | Description       |
| ---- | ----------------- |
| Hash | The contract hash |

## Methods

| Name                       | Description                                                  |
| -------------------------- | ------------------------------------------------------------ |
| GetFeePerByte()            | Gets the network fee per transaction byte                    |
| GetExecFeeFactor()         | Gets the execution fee factor. This is a multiplier that can be adjusted by the committee to adjust the system fees for transactions |
| GetStoragePrice()          | Gets the storage price                                       |
| IsBlocked(UInt160 account) | Determines whether the specified account is blocked          |