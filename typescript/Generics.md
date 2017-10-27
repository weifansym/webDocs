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
