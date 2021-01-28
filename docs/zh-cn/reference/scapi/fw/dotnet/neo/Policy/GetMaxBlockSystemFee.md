# GetMaxBlockSystemFee 方法 ()

获取区块最大的系统费。

命名空间：[Neo.SmartContract.Framework.Services.Neo](../../neo.md)

程序集：Neo.SmartContract.Framework

## 语法

```c#
public static extern long GetMaxBlockSystemFee();
```

## 示例

```c#
public class Contract1 : SmartContract.Framework.SmartContract
{
    public static object Main()
    {
        long result = Policy.GetMaxBlockSystemFee();
        return result;
    }
}
```
响应正文：

```json
{
	"type":"Integer",
	"value":"900000000000"
}
```

响应说明：

- Integer类型：成功获取区块最大手续费。

- 其他：失败。

[返回上级](../Policy.md)