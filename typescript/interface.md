## 接口
### 数组类型
与我们使用interface来描述函数类型一样，我们也可以用interface来描述数组类型。数组类型有一个"index"类型用来描述了数组索引的类型，以及一个返回值类型用来表示相对应索引的元素类型。

```
interface StringArray {
  [index: number]: string;
}
var myArray: StringArray;
myArray = ["Bob", "Fred"];
```
支持的两种索引类型：string和number。数组可以同时使用这两种索引类型。但也存在限制，数字索引的返回值类型必须是字符串索引返回值类型的子类型。

```
interface Something {   
    [index: string]: number;
    [index: number]: number;  //数字索引的返回值类型是number,它是字符串索引的返回值类型的子类型；若[index: string]:string,则数字索引的返回值类型也必须是string
}
```
举例如下：

```
interface StringArr {
    [index: string]: string;
}
var myArray_1: StringArr;
myArray_1 = {
    '111': 'dsd',
    'rewrw': 'lw'
};

console.log('data: ', myArray_1["111"])
```
虽然索引标识是个用来描述数组及"dictionary"模式的很好的方式，同时也迫使所有属性需要匹配他们的返回类型。在这个例子中，属性类型与索引类型不匹配，类型检查程序给出错误：

```
interface Dictionary {
  [index: string]: string;
  length: number;    // 错误, 'length'的类型不是索引类型的子类型
} 
```
