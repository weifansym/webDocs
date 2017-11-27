## vscode开发ts遇到的问题
### 引入node包报错：Cannot find module

这是因为没有安装ts版本的node包，所以运行tsc命令编译的时候会报错：
```
error TS2307: Cannot find module 'http'.
```
解决方式：只需要引入ts版本的node包就可以了，运行如下命令安装：
```
npm install @types/node --save
```
