## tslint
### 安装
全局安装：

```
npm install tslint typescript -g
# or
yarn global add tslint typescript

tslint -v (显示安装tslint的版本)

```
本地安装（你的项目的工作目录）

```
npm install tslint typescript --save-dev
# or
yarn add tslint typescript --dev

```
### CLI使用
用法：

```
tslint [options] [file ...]
```
Options:

```
-c, --config          configuration file
-e, --exclude         exclude globs from path expansion
--fix                 Fixes linting errors for select rules. This may overwrite linted files
--force               return status code 0 even if there are lint errors
-h, --help            display detailed help
-i, --init            generate a tslint.json config file in the current working directory
-o, --out             output file
--outputAbsolutePaths whether or not outputted file paths are absolute
-p, --project         tsconfig.json file
-r, --rules-dir       rules directory
-s, --formatters-dir  formatters directory
-t, --format          output format (prose, json, stylish, verbose, pmd, msbuild, checkstyle, vso, fileslist, codeFrame)  [default: "prose"]
--test                test that tslint produces the correct output for the specified directory
--type-check          (deprecated) enable type checking when linting a project
-v, --version         current version

```
> 具体的options的描述参看：https://palantir.github.io/tslint/usage/cli/

### 初始化tslint.json文件
初始化tslint的配置文件tslint.json，使用如下命令：

```
tslint --init
```
### 配置规则

具体的配置规则请看[tslint官网](https://palantir.github.io/tslint/usage/configuration/)

关于的extends配置参看：[tslint官网](https://palantir.github.io/tslint/usage/configuration/) 和 [tslint](https://github.com/palantir/tslint)

关于TSLint core rules：[tslint官网](https://palantir.github.io/tslint/rules/）

这里只提供一个配置的demo：

```
{
  "extends": [
    "tslint:recommended",
    "tslint-react",
    "tslint-eslint-rules"
  ],
  "rules": {
    "semicolon": [
      true,
      "never"
    ], //每个语句后强制不使用分号
    "indent": [
      true,
      "spaces",
      2
    ], // 两个空格
    "linebreak-style": [
      true,
      "LF"
    ],
    "quotemark": [
      true,
      "single",
      "jsx-single"
    ],
    "new-parens": true, //使用new操作符时要使用括号
    "no-arg": true, //不允许使用argument.callee
    "no-conditional-assignment": true, //不允许赋值/分配操作在条件语句中
    "no-consecutive-blank-lines": false, //不允许一行或多行空行
    "no-trailing-whitespace": false, //不允许在行末尾有拖尾空格
    "interface-name": false,
    "object-literal-sort-keys": false,
    "no-string-literal": false,
    "one-variable-per-declaration": [
      true,
      "ignore-for-loop"
    ], //在同一个生命语句中禁止多个变量定义
    "ordered-imports": false,
    "member-access": false, //需要为类成员提供明确的可见性声明
    "class-name": true,
    "eofline": true, //确保文件以换行符结尾 不用
    "comment-format": [
      true,
      "check-space"
    ], //注释规则
    "newline-before-return": true,
    "max-line-length": false,
    "trailing-comma": true, //数组或对象最后一个不允许逗号
    "jsx-curly-spacing": "never",
    "jsx-no-lambda": false,
    "object-literal-shorthand": false, // 尽可能用es6
    "jsx-wrap-multiline": true,
    "no-shadowed-variable": false,
    "jsx-no-multiline-js": false,
    "prefer-for-of": false,
    "radix": false,
    "no-unused-expression": false,
    "variable-name": false,
    "jsdoc-format": false,
    "no-var-requires": false,
    "import-blacklist": false,
    "prefer-const": false,
    "no-require-imports": false,
    "space-before-function-paren": false,
    "only-arrow-functions": false,
    "no-bitwise": false // 是否不允许使用位运算符
  },
  "jsRules": {
    "max-line-length": {
      "options": [
        256
      ]
    }
  }
}

```




