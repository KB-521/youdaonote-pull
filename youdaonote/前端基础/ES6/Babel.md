Babel 是一个 JavaScript 编译器：

Babel 是一个工具链，主要用于将 ECMAScript 2015+ 版本的代码转换为向后兼容的 JavaScript 语法，以便能够运行在当前和旧版本的浏览器或其他环境中。



使用：

```javascript
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
<script type="text/babel"></script>
```



Babel如何将ES6变成ES5语法：

1. 将代码字符串解析成抽象语法树，即所谓的AST。

1. 对AST进行处理，在这个阶段可以对ES6代码进行相应的转换，即转成ES5语法。

1. 根据处理后的AST在生成字符串



