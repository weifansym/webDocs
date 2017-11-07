## declare
In this short quick tip, I’ll describe what is this keyword and where to use it.

在这个简短的快速教程中，我将会描述这个关键字是什么，以及怎么使用这个关键字

### If It Doesn’t Exists, Declare It
Not all JavaScript libraries/frameworks have TypeScript declaration files. On the other hand, we might want to use libraries/frameworks 
in our TypeScript files without getting compilation errors. What can we do? 
One solution is to use the declare keyword. The declare keyword is used for ambient declarations where you want to define a variable
that may not have originated from a TypeScript file.

不是所有的js包或者是框架都有Typescript的声明文件。另一方面，我们有需要在Typescript中引入这些包或者框架来去除编译报错。那我们改怎么办呢？
一个解决方式就是使用declare关键字，这个declare关键字被用来做环境声明，在你想要定义一个变量，而这个变量又不是出自Typescript文件时。

For example, lets imagine that we have a library called myLibrary that doesn’t have a TypeScript declaration file and have a namespace 
called myLibrary in the global namespace. 
If you want to use that library in your TypeScript code, you can use the following code:

例如， 让我们想想一下，我们有一个叫做myLibrary的包，这个包没有TypeScript声明文件，但是在全局命名空间中有一个叫做myLibrary的命名空间。
如果你想要的在TypeScript中使用这个包，你应该使用下面的代码：

```
declare var myLibrary;
```
The type that the TypeScript runtime will give to myLibrary variable is the any type. The problem here is that you won’t have Intellisense
for that variable in design time but you will be able to use the library in your code. Another option to have the same behavior without
using the declare keyword is just using a variable with the any type:


```
var myLibrary: any;
```
Both of the code examples will result in the same JavaScript output but the declare example is more readable and expresses an ambient 
declaration.

Summary

The TypeScript declare keyword is used to declare variables that may not have originated from a TypeScript file.
