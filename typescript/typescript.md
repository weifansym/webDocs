##  TypeScript start
## 安装
全局安装：

```
npm install -g typescript
```

查看安装版本：

```
tsc -v
```
## 编译

直接编译：

```
tsc helloWorld.ts
```

基于配置文件编译:

    
    tsc -int  生成配置文件tsconfig.json。
    
    tsc 根据配置文件编译项目中的ts
    你会在tsconfig.json中配置的编译输出生成文件中，看到编译的结果。
    
> 根据[tsconfg.json](https://www.tslang.cn/docs/handbook/tsconfig-json.html)
查看tsconfg.json的具体配置信息


