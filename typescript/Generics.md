## 泛型
### 泛型类
泛型类的实例：
 ```
 class GenericNumber_1<T> {
    static dudu: string;
    zeroValue: T;
}

class Duhuo {
    name: string;
   constructor () {

   }
}

class Huo extends Duhuo{
    age: number
}

class Du extends Duhuo {
  address: string
}

/*let obj = new GenericNumber_1<Duhuo>();
let huo = new Huo();
huo.age = 12;
huo.name = 'huhu';

obj.zeroValue = huo;

console.log(obj.zeroValue.name)
// console.log(obj.zeroValue.age);  //  异常：没有这个属性*/

/*let obj = new GenericNumber_1<Huo>();
let duHuo = new Duhuo();
duHuo.name = '多态';

obj.zeroValue = duHuo;    //  异常： Type 'Duhuo' is not assignable to type 'Huo'*/

 ```
 
 在泛型中使用类类型
 
当在TypeScript中使用泛型创建工厂函数的时候，需要引用其构造函数的类类型。

```
class Greeter_1{
    greeter:string = "Hello World";
}
//  泛型方法
function create_1<T>(c: T): T {
    return c
}

//  泛型工厂函数
//  当在TypeScript中使用泛型创建工厂函数的时候，需要引用其构造函数的类类型。
//  参数c是一个对象参数，其中new ()相当于构造函数，T就是构造函数的所属的类的类型变量
function create<T> (c: {new () : T} ): T {
    return new c();
}

var newGreeter = create<Greeter_1>(Greeter_1);

```
