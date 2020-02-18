# Iterator 类

智能合约中的自定义迭代器。

命名空间：[Neo.SmartContract.Framework.Services.Neo](../neo.md)

程序集：Neo.SmartContract.Framework

## 语法

```c#
public class Iterator<TKey, TValue>
```

## 属性

|                                                        | 名称  | 说明                     |
| ------------------------------------------------------ | ----- | ------------------------ |
| ![](https://i-msdn.sec.s-msft.com/dynimg/IC74937.jpeg) | Key | 获取迭代器当前Key值 |
| ![](https://i-msdn.sec.s-msft.com/dynimg/IC74937.jpeg) | Value | 获得迭代器当前Value值 |
| ![](https://i-msdn.sec.s-msft.com/dynimg/IC74937.jpeg) | Keys | 获取迭代器所有Key的迭代器 |
| ![](https://i-msdn.sec.s-msft.com/dynimg/IC74937.jpeg) | Values | 获取迭代器所有Value的迭代器 |

## 方法

|                                                        | 名称                                | 说明                                                         |
| ------------------------------------------------------ | ----------------------------------- | ------------------------------------------------------------ |
| ![](https://i-msdn.sec.s-msft.com/dynimg/IC91302.jpeg) | Create(Map\<TKey, TValue\> entry) | 静态方法，创建迭代器                                         |
| ![](https://i-msdn.sec.s-msft.com/dynimg/IC91302.jpeg) | Create(IEnumerable\<TValue\> entry)  | 静态方法，创建迭代器                                                |
| ![](https://i-msdn.sec.s-msft.com/dynimg/IC91302.jpeg) | Concat(Iterator\<TKey, TValue\> value) |合并迭代器 |
| ![](https://i-msdn.sec.s-msft.com/dynimg/IC91302.jpeg) | Next()            | 获得迭代器中是否有下个元素，如果有则枚举器将当前位置定位到下个元素 |
