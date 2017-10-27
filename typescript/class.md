# 类
传统的JavaScript注重用函数和基于原型的继承来创建可复用的组件，但这可能让用习惯面对对象方式的程序员感到棘手，因为他们的继承和创建对象都是由类而来的。从JavaScript的下一个版本，ECMAScript 6开始，JavaScript程序员就能够用基于这种基于类的面对对象方式来创建编写自己的程序了。在TypeScript中，不需要再等JavaScript的下一个版本就已经支持开发者使用这一技术了。

## 类

让我们来看一个简单的基于类的例子：
```
class Greeter {
    greeting: string;
    constructor(message: string) {
        this.greeting = message;
    }
    greet() {
        return "Hello, " + this.greeting;
    }
}
var greeter = new Greeter("world");

```
如果你之前有使用过C#或者Java，会觉得语法非常相似。我们声明一个新的类"Greeter"。这个类里面有三个成员，一个名为"greeting"的属性，一个constructor和一个"greet"方法。

你会注意到，在类里面当某一个成员使用了"this"，意味着他访问的是这个类的成员。

在最后一行中，我们使用"new"来为Greeter类构造一个实例。这将会调用之前定义的构造函数，并且创建一个新的Greeter类型的对象，并且执行构造函数来初始化这个对象。

## 继承
在TypeScript中，我们可以使用常见的面向对象模式。当然，在基于类的编程中最基本的模式之一就是能够创建一个新的类，这个新的类继承已有的类，并对已有的类做扩展。
来看一个例子：

```
class Animal {
    name:string;
    constructor(theName: string) { this.name = theName; }
    move(meters: number = 0) {
        console.log(this.name + " moved " + meters + "m.");
    }
}
class Snake extends Animal {
    constructor(name: string) { super(name); }
    moveSome(meters = 5) {
        console.log("Slithering...");
        //super.move(meters);
    }
}
class Horse extends Animal {
    constructor(name: string) { super(name); }
    move(meters = 45) {   //
        console.log("Galloping...");
        //super.move(meters);
    }
}
var sam = new Snake("Sammy the Python");
var tom = new Horse("Tommy the Palomino");
sam.move();
sam.moveSome();
tom.move(34);

//  类里面声明的访问限制条件：public，private，protected
//  类里面声明的其他限制条件：static（声明类的属性）
//  子类覆盖父类成员的方法，属性,不能覆盖类的成员方法和属性
//  子类覆盖父类中的super，调用父类的构造函数
```
这个例子包含了TypeScript中继承的特性，当然，在其他语言中也一样。在这里，我们使用"extends"关键字来创建一个子类。你可以看到，这里"Horse"和"Snake"两个子类都基于"Animal"这个父类，并且对其特性进行了扩展。在这里，我们使用"extends"关键字来创建一个子类。你可以看到，这里"Horse"和"Snake"两个子类都基于"Animal"这个基类并且获取其特性。

例子也体现了在子类中可以重写基类中的方法以达到重写后的方法是在这个子类中专用。这里的"Horse"和"Snake"都创建了"move"这个方法，这样就重写了从基类继承过来的move方法，并且在不同类中给"move"不同的方法。

## 公有和私有的修饰符
> 默认是public(公有)
