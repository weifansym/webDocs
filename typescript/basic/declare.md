## declare
In this short quick tip, I’ll describe what is this keyword and where to use it.
在这个简短的快速教程中，我将会描述这个关键字是什么，以及怎么使用这个关键字

### If It Doesn’t Exists, Declare It
Not all JavaScript libraries/frameworks have TypeScript declaration files. On the other hand, we might want to use libraries/frameworks 
in our TypeScript files without getting compilation errors. What can we do? 
One solution is to use the declare keyword. The declare keyword is used for ambient declarations where you want to define a variable
that may not have originated from a TypeScript file.

For example, lets imagine that we have a library called myLibrary that doesn’t have a TypeScript declaration file and have a namespace 
called myLibrary in the global namespace. 
If you want to use that library in your TypeScript code, you can use the following code:

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
