# Contract Class

The class representing a contract.

Namespace：[Neo.SmartContract.Framework.Service](../Neo.SmartContract.Framework.Service.md)

Assembly: Neo.SmartContract.Framework

## Syntax

```c#
public class Contract
```

## Attributes

| Name | Description |
| -------------------------------- | ------ |
| Id     | Contract Id. The native contract ID is a negative integer, and the normal contract ID is a positive integer. |
| UpdateCounter | Contract update counter |
| Hash  | Contract hash, which is determined by the deployer's script hash, the contract NEF checkcode, and the contract name. |
| Script  | Contract script array |
| Manifest  | Json strings that represents the contract Manifest |

## Methods

| Name | Description |
| -------------------------------- | ------ |
| [Call(UInt160 scriptHash, string method, object[] arguments)](Contract/Call.md) | Invokes the contract |
| [GetCallFlags()](Contract/GetCallFlags.md)         | Gets the CallFlag of the contract |
| [CreateStandardAccount()](Contract/CreateStandardAccount.md)         | Creates a standard account with public key |

## Constructor

The Contract object can be constructed through [ContractManagement.GetContract(UInt60 hash)](ContractManagement/GetContract.md).

 [ContractManagement.Deploy(byte[] nefFile, string manifest)](ContractManagement/Deploy.md) publishes the contract onto the blockchain and returns a contract object.

