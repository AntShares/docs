# Binary.Atoi Method

Converts a character string to a specific base value, decimal or hexadecimal. The default is decimal.

Namespace: [Neo.SmartContract.Framework.Services.System](../../system.md)

Assembly: Neo.SmartContract.Framework

## Syntax

```c#
public static extern BigInteger Atoi(string value, int @base = 10);
```

Parameters:
- value: The string to convert.
- base: The value base.

Return: Equivalent value.

## Example

```c#
public class Contract1 : SmartContract.Framework.SmartContract
{
    public static object Convert()
    {
        return Binary.Atoi("ff", 16); 
    }
}
```

Deploy and then invoke the contract, the response body is:

```json
[{
    "type":"Integer",
    "value":"-1"
}]
```

Response description：

- Integer type: Equivalent value.

- Other: failed.

[Back](../Binary.md)

