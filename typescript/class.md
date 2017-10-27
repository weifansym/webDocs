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
### 默认是public(公有)
你可能已经注意到了，在上面的例子中，我们并未对类的任何可见成员使用"public"关键字进行修饰。类似C#语言，需要给成员使用"public"修饰符用来明确它是可见。在TypeScript中，每个成员默认是"public"的。

你还可以给成员标记上"private"，这样你就可以控制在你的类之外哪些成员是可见。我们可以像这样重写上一节的"Animal"类：
```
class Animal {
    private name:string;
    constructor(theName: string) { this.name = theName; }
    move(meters: number) {
        alert(this.name + " moved " + meters + "m.");
    }
}
```
### 理解Private(私有)

TypeScript是个构造类型的系统。当我们对两个类型进行比较的时候，无论它们是从哪里来，如果所有成员的类型都是兼容的，那么我们可以认为他们的类型也是兼容的。

当我们比较的类型中含有"private"(私有)成员，则我们就需要不同的对待了。两个类型(假如是A和B)被认为是兼容的，如果A类型含有一个私有成员，那么B类型就必须也有一个私有成员并且与A类型的私有成员源自同一处声明。

让我们用一个例子来更好的看看私有成员在实践中如何运用：
```
class Animal {
    private name:string;
    constructor(theName: string) { this.name = theName; }
}
class Rhino extends Animal {
    constructor() { super("Rhino"); }
}
class Employee {
    private name:string;
    constructor(theName: string) { this.name = theName; }    
}
var animal = new Animal("Goat");
var rhino = new Rhino();
var employee = new Employee("Bob");
animal = rhino;
animal = employee; // 错误: Animal 和 Employee 不兼容
```
> 这个问题应该是其他变成语言中多态的概念，也就是类型兼容性的问题，可以单独分章节拿出来分析的

在这个例子中，我们有一个"Animal"和一个"Rhino"，"Rhino"是"Animal"的一个子类。我们还有一个新的类"Employee"，它看上去跟"Animal"类是完全相同的。我们给这些类分别创建实例，并且对他们进行相互赋值，看下将会发生什么。因为"animal"和"rhino"的私有成员都是从"Animal"类定义的"private name: string"共享而来的，所以他们是兼容的。然而，"employee"的情况却不是这样的。当我们试图将"employee"赋值给"animal"，我们得到了一个错误，他们的类型是不兼容的。尽管"Employee"也有一个名称是"name"的私有成员，但它和在"Animal"中的私有成员"name"还是不相同的。

### 理解protected(保护)  后续补充
这个需要后续补充

### 参数属性
关键字"public"和"private"通过创建参数属性的方式给我们提供了创建和初始化类的成员的便捷方式。这个特性让你可以一个步骤就创建和初始化成员。这里有一个之前例子的进一步修改。注意我们是如何在constructor中将"name"使用"private name: string"的便捷方式完整的创建并初始化成这个类的私有成员"name"的。

```
class Animal {
    constructor(private name: string) { }
    move(meters: number) {
        alert(this.name + " moved " + meters + "m.");
    }
}
var goat = new Animal("Goat");
goat.move(25); // Goat moved 25 m.
```
通过这种方式使用"private"来创建和初始化私有成员，"public"也一样。
> 参数属性这种方式，是不是使得相关成员属性定义不明确，描述不清晰，应该分开单独写

### 访问器

TypeScript提供 getters/setters 的方式来拦截对于类成员对象成员的访问。它让我们可以更精确的控制如何对对象成员的进行访问。

让我们来将一个类的属性的某些写法改写成用"get"和"set"。首先，我们从一个没有"get"和"set"的例子开始：
```
class Employee {
    fullName: string;
}
var employee = new Employee();
employee.fullName = "Bob Smith";
if (employee.fullName) {
    alert(employee.fullName);
}
```
以上代码允许我们随意设置fullName，可能我们会觉得这样比较直接和方便，但这么随心所欲的改变名字也可能会导致问题。

在这个版本中，我们将给被允许修改员工信息的用户一个可用的密码。在对fullName进行"set"访问的之前，我们会以检查密码来代替允许直接修改。我们添加一个相应的"get"让之前的例子依然能实现。

```
var passcode = "secret passcode";
class Employee {
    private _fullName: string;
    get fullName(): string {
        return this._fullName;
    }
    set fullName(newName: string) {
        if (passcode && passcode == "secret passcode") {
            this._fullName = newName;
        }
        else {
            alert("Error: Unauthorized update of employee!");
        }
    }
}
var employee = new Employee();
employee.fullName = "Bob Smith";
if (employee.fullName) {
    alert(employee.fullName);
}
```
为了证明现在访问需要密码，我们可以修改密码，然后我们会发现，当密码不符合的时候会弹出提示"Error: Unauthorized update of employee!"(错误：没有修改employee的权限)。

> 注意：访问器需要我们将文件以ECMAScript5编程输出。
```
tsc --target ES5 your.ts
```
## 静态成员与实例成员
到此为止，我们只谈到类的实例成员，那些只有实例化后才初始化并且显示的成员。我们还可以为类创建类的静态成员，静态成员在类本身上可见而非在实例上可见。在这个例子中，我们使用"static"来修饰"origin",因为他是所有Grid类都会用到的东西。任何地方需要使用它，都需要在前面加上类名。这就像要在实例对象方法中需要在成员属性前加上"this"来访问这个实例的成员属性。在这里我们将使用"Grid."来访问静态成员。

```
class Grid {
    static origin = {x: 0, y: 0};
    calculateDistanceFromOrigin(point: {x: number; y: number;}) {
        var xDist = (point.x - Grid.origin.x);
        var yDist = (point.y - Grid.origin.y);
        return Math.sqrt(xDist * xDist + yDist * yDist) / this.scale;
    }
    constructor (public scale: number) { }
}
var grid1 = new Grid(1.0);  // 1x 规模
var grid2 = new Grid(5.0);  // 5x 规模
alert(grid1.calculateDistanceFromOrigin({x: 10, y: 10}));
alert(grid2.calculateDistanceFromOrigin({x: 10, y: 10}));
```

## 高级技巧
### 构造函数
当你在TypeScript中声明一个类的同时，你也定义了很多东西。首先就是这个类的实例类型。

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
var greeter: Greeter;
greeter = new Greeter("world");
alert(greeter.greet());
```
这里，当我们写"var greeter: Greeter"，我们就已经将"Greeter"类的实例类型定义为"Greeter"了。这对于用过其它面向对象语言的程序员而言已经习以为常了。

我们也同时的创建了一个类的构造函数，当我们使用"new"来为类创建实例的时候，我们将会调用这个函数。让我们结合实践，在编译后的JavaScript中看看上面的这个例子吧：

```
var Greeter = (function () {
    function Greeter(message) {
        this.greeting = message;
    }
    Greeter.prototype.greet = function () {
        return "Hello, " + this.greeting;
    };
    return Greeter;
})();
var greeter;
greeter = new Greeter("world");
alert(greeter.greet());
```
> 在创建完类之后，类的静态成员就存在了，类的实例成员需要等到实例构建之后才存在（???）


